# Examples

## Receive Tx Method 1

*Receive Transactions with a message*

This guide discusses the method of accepting payments with a note to the payment (message) in the SmartHoldem ecosystem. The service uses 1 address, but for each user a unique string is generated.

For simplicity of understanding, PHP is used as a backend.

In the process involved: the service (exchanger) and the user (the client).

Benefits:

- 1 address is sufficient for accepting payments
- simple integration
- convenient control of funds
- processing of a large number of transactions

### Client

From the client side, a certain service-exchanger, generates the initial data for the client:

- the amount to be received in the exchangeable coin (specified by the client)
- calculated result to be received at the current exchange rate STH> COIN
- address for sending STH (for all users one)
- a unique message string (identifies the sender)

Here on the service side in backend a unique string is generated for each user and stored in a database, for example, a table of the form:
userid (int), msg (string)

```php
<?php
// example generate unique user string
$msg = substr(md5(uniqid(microtime(), 1)) . getmypid(), 1, 8);

// result unique string:  561559b2
```

The client, knowing the initial data, sends the corresponding amount with a note to the specified address with the help of his wallet.

<img src="images/ex1.jpg" width="100%">

### Service
Now the backend of the service, the transaction handler, enters the work. For ease of understanding, we will use the execution of the script on crontab.

We create a php-file on the server side, then we'll assign it to cron every minute.

```php
<?php
$addr = 'Sg13BhANeairfS3o3w8N9sKaFrsht2bt4V'; //transaction verification service address
$limit  = 25; //transaction limit
$offset = 0;

//sort out the issuance of transactions by timestamp using orderBy
$url = 'http://your_node_ip:6100/api/transactions?recipientId='.$addr.'&orderBy=timestamp&offset=0';

//get the data and convert it to an array
$tx = json_decode(file_get_contents($url),true);

/*
if the transaction is more than a limit,
offset transaction transfer pointer and get the last $ limit of transactions,
since transactions can be hundreds of thousands
*/
if ($tx['count'] > $limit) {
    $offset = $tx['count'] - $limit; // calculation of displacement
    $url = 'http://node_ip:6100/api/transactions?recipientId=Sg13BhANeairfS3o3w8N9sKaFrsht2bt4V&orderBy=timestamp&offset='.$offset;
    $tx = json_decode(file_get_contents($url),true);
}

// processing data
for ($i = 0; $i < count($tx['transactions']); $i++) {
print "<br>amount:".$tx['transactions'][$i]['amount'].
" timestamp:".$tx['transactions'][$i]['timestamp'].
" msg:".$tx['transactions'][$i]['vendorField'].
" senderId:".$tx['transactions'][$i]['senderId'].
" Txid:".$tx['transactions'][$i]['id'];

/*
here we perform the necessary checks and writes to the database,
for example, add a balance

To save in the transaction table unique transactions,
which are also checked upon receipt,
for example txid, userid, timestamp, sum_sth, sum_coin
*/

/*
remember, the balance is issued in satoshi,
do not forget to convert it to exact functions
*/
$sumCOIN = bcdiv($tx['transactions'][$i]['amount'],100000000,8);

$set['btc_sth'] = 1; //course in relation to STH
$sumBTC = bcdiv($sumCOIN, $set['btc_sth'], 8); //calculate the coin rate

}
```

Congratulations, the transaction is processed, the operation is completed.

<aside class="warning">
The example does not pretend to the quality of the code, it is intended for a basic understanding of receiving payments.
</aside>

## Send Tx PHP

A simple PHP example of sending transactions.

```php
<?php
$url = 'http://node_ip:6100/api/transactions';
$data = json_encode((object) array(
            "secret" => "sender address secret pass phrase",
            "amount" => 10000000, //0.1 STH in Satoshi
            "recipientId" => "Sa9JKodiNeM7tbYjxwEhvvG1kBczhQxTN3", //recipient address
            "vendorField" => "any message" // optional
        ));


$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Accept: application/json', 'Content-Type: application/json'));
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_setopt($ch, CURLOPT_TIMEOUT, 30);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
$response = curl_exec($ch);
curl_close($ch);

$result = json_decode($response, true); //convert to array
print_r($result); //show result
```
