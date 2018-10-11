# Transactions

## Send Transaction

```shell
curl -k -H "Content-Type: application/json" -X PUT
-d '{"secret":"<AddressSecretPassphrase>","amount":<Amount>,"recipientId":"<RecipientAddress>"}'
http://127.0.0.1:6100/api/transactions
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
curl -X GET "http://127.0.0.1:6100/api/transactions/get?id={TxID}"
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

## Get all transactions

```shell
curl -X GET "http://127.0.0.1:6100/api/transactions?limit={limit}&offset={offset}"
-H "accept: application/json"
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7"
-H "version: 0.0.2"
-H "port: 6100"
```

```http
GET api/transactions?limit={limit}&offset={offset} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "transactions":
      [
        {
          "id":"2bf77bdb8a97f6b8bb8e9b656a57e8971f49ff93f494c2ba420dd8fc35e1a34a",
          "blockid":"16602765030304240142",
          "type":0,
          "timestamp":2465122,
          "amount":61042030621,
          "fee":10000000,
          "senderId":"SVx2j3NdZbDLfZ9HWS57NvqYg4c9grQLnx",
          "recipientId":"SSkYDCEXYxkETPRNHzRPAr2CgEVwq3sRtH",
          "senderPublicKey":"03b2000d0e5042e82aed1fe7d7b556ba7cbc921406fe65cc3881652115f843fbb9",
          "signature":"304402205fa2532675d2f3043f4a727c3be0f510b9dab361b05a7bb0838fedcdb5a8d817022006f84a20bb17c209c01f46ba0ed4b4becb90fb0c28da9e937f9da00dee7f78e7",
          "asset":{},
          "confirmations":792507
        },
        {
          "id":"f98257d351549ccf4956aa3abb04304db8970924a4880e97c1ecd389edd0346b",
          "blockid":"1749022156066192207",
          "type":0,
          "timestamp":2465174,
          "amount":743602918474,
          "fee":10000000,
          "senderId":"SVx2j3NdZbDLfZ9HWS57NvqYg4c9grQLnx",
          "recipientId":"SYWCs4KM8DtfUoxVkNnyetja91P2b7mSvg",
          "senderPublicKey":"03b2000d0e5042e82aed1fe7d7b556ba7cbc921406fe65cc3881652115f843fbb9",
          "signature":"304402201b16338c61e935e12112b14f7493531ec1d9a4ed73806447bd182797911d10e40220742972459a4b6701bbc26a8fe1817b930f0d2df54fbc83b36c422c40a3c91636",
          "asset":{},
          "confirmations":792503
        }
      ],
    "count":"6411"
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/transactions?limit={limit}&offset={offset}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
blockId | string<br>(query) | An unsigned integer that specifies the block ID.
limit  | integer<br>(query) | An unsigned integer that specifies the maximum number of records.
offset     | integer<br>(query) | An unsigned integer that specified the number of records to skip.
type   | integer<br>(query) | An unsigned integer that specifies the transaction type.
orderBy    | string<br>(query) | A string that specifies the column by which to sort the records.
senderPublicKey | string<br>(query) | A valid Public Key.
ownerPublicKey | string<br>(query) | A valid Public Key.
ownerAddress | string<br>(query) | A valid Address.
senderId | string<br>(query) | A valid Address.
recipientId | string<br>(query) | A valid Address.
amount | integer<br>(query) | An unsigned integer that specifies the transaction amount.
fee | integer<br>(query) | An unsigned integer that specifies the transaction fee.
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get all unconfirmed transactions

```shell
curl -X GET "http://127.0.0.1:6100/api/transactions/unconfirmed"
-H "accept: application/json"
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7"
-H "version: 0.0.2"
-H "port: 6100"
```

```http
GET api/transactions/unconfirmed HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "transactions":[]
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/transactions/unconfirmed`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
senderPublicKey | string<br>(query) | A valid Public Key.
address | string<br>(query) | A valid Address.
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Timestamp Calc TX

Calculation of transaction time begins from the first block 11/21/2017 @ 1:00pm (UTC),
from unix time: 1511269200

To get a human transaction time it is necessary to add to 1511269200 timestamp specified in the transaction

Example:

> tx result:
```json
{
  "success": true,
  "transaction": {
    "id": "2f5f333d46e6de3b77e76be0a358f83fb25cb4c3c8907fce117acef7f74c6844",
    "blockid": "15218540347764387952",
    "height": 135452,
    "type": 0,
    "timestamp": 3354199,
    "amount": 200000000000,
    "fee": 10000000,
    "senderId": "STHiQuGcpz8EQstJiBZ5HkVWxrSwc7wPgH",
    "recipientId": "SVx2j3NdZbDLfZ9HWS57NvqYg4c9grQLnx",
    "senderPublicKey": "02573f491df3c6f031660b4b64b0421103fe32ec3d8615a234892aba227191aab5",
    "signature": "3044022025303c28855f97b75e92d878dd5ff8023549da81b7605986e3bbf3ca57957d760220756e0d87be2aab86e27c6cd145ae45ba7edf2a51151cc35e98765f59b711c536",
    "asset": {

    },
    "confirmations": 2985891
  }
}
```
tx timestamp = 3354199

human time = 1511269200 + 3354199 = 1514623399 = 12/30/2017 @ 8:43am (UTC)

