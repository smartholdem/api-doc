# Examples

## Receive Transactions Method 1

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

