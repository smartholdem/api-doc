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

## Get a single transaction

```shell
curl -X GET "http://127.0.0.1/api/transactions/get?id={TxID}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/transactions/get?id={TxID} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "transaction":
      {
        "id":"6de0bf336fb0b232e27cc79822d5c69e8604c9c4ac1e55099c8403243e5c6e6f",
        "blockid":"17539280775357750950",
        "height":833616,
        "type":0,
        "timestamp":9068949,
        "amount":17000000000,
        "fee":10000000,
        "senderId":"Sf6y6bFqdPiXt9qupmTdpJFJwBWmMCfs43",
        "recipientId":"SZg73u3rVrqwahfZ2tU6G1E3YwDs52tMeW",
        "senderPublicKey":"03e340952f7d726d8598b4ae68e88e583b39735c35b489559e082c705dba50376e",
        "signature":"30450221009f5617a4f68deb466ef26c6aa5165f32ea7db23c77882d455b6a6d7fa6ad6e5e02205cf900ea86ef0bc4d5102e3d4292984c949453f6e5da756321ad8c61a3786ec7",
        "asset":{},
        "confirmations":2919
      }
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/transactions/get?id={TxID}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | string<br>(query) | A valid transaction ID
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100
