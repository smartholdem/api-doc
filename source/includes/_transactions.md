# Transactions

## Send Transaction

```shell
curl -k -X PUT "http://127.0.0.1/api/transactions"
-d '{"secret":"<AddressSecretPassphrase>","amount":<Amount>,"recipientId":"<RecipientAddress>"}' 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
PUT api/transactions HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
{
  "secret": "one two the four five six seven eith night ten eleven twelwe",
  "amount": 100000000,
  "recipientId": "SiGek5KGRWzGaRxb87CeukeeBhvi1Uu57b"
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "transactionId":"cace8c8bfe47541c4d587ede2acd2a05ce0a79c25877b98d219d363643e051a7"
  }
]
```

JSON Response

### HTTP Request

`PUT http://127.0.0.1:6100/api/transactions`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
secret | string<br>(query) | one two the four five six seven eith night ten eleven twelwe
amount | integer<br>(query) | amount in satoshi (100000000 = 1 COIN)
recipientId | string<br>(query) | Recipient Address
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

