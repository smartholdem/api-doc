# Transport

Operations for Transports

## Get a list of peers

```shell
curl -X GET "http://127.0.0.1:6100/peer/list" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET /peer/list HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "version":"0.0.2",
    "build":""
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/peer/list`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get a list of blocks by ids

```shell
curl -X GET "http://127.0.0.1:6100/peer/blocks/common?ids='{id}'" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET /peer/blocks/common?ids='{id}' HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "common":
      {
        "height":837951,
        "id":"14680647590392835738",
        "previousBlock":"3557000320223856005",
        "timestamp":9105256
      },
    "lastBlockHeight":837978
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/peer/blocks/common?ids='{id}'`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
ids | string<br>(query) | ids - list of block IDs
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get the status

```shell
curl -X GET "http://127.0.0.1:6100/peer/status" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET /peer/status HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "height":838130,
    "forgingAllowed":false,
    "currentSlot":1138339,
    "header":
      {
        "id":"3559432260321673957",
        "height":838130,
        "version":0,
        "totalAmount":0,
        "totalFee":0,
        "reward":200000000,
        "payloadHash":"e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
        "payloadLength":0,
        "timestamp":9106712,
        "numberOfTransactions":0,
        "previousBlock":"5309083107160493676",
        "generatorPublicKey":"02d0c97cc201c752b53718ff36ff48ca5dead557bc1c47335476e71a0143263789",
        "blockSignature":"3045022100b65d13e3ad465af4b7eb3209e25ccc62d7df74f2f1ea50b97ec973e8981f074402203d1af020a5cf744fdb41f2472ef30ebfaf5c0367adcc994db92895a9f272e14a"
      }
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/peer/status`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get the blockchain height peer

```shell
curl -X GET "http://127.0.0.1:6100/peer/height" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET /peer/height HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "height":838152,
    "header":
      {
        "id":"1745814126765338549",
        "height":838152,
        "version":0,
        "totalAmount":0,
        "totalFee":0,
        "reward":200000000,
        "payloadHash":"e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
        "payloadLength":0,
        "timestamp":9106896,
        "numberOfTransactions":0,
        "previousBlock":"15643855646433486272",
        "generatorPublicKey":"033691a3abe70be86360d312c4b173d48e0a94fc34c10517e95dae711549533755",
        "blockSignature":"3045022100dc956f488ff066529dd064acaa89fb5454ffa08bc92ebd24744780cc69581d9d02204444c98c1368e0c2ae765a126ed27068bbe4b09026d61e22b25054e98fd98b05"
      }
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/peer/height`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Broadcast a new transaction

```shell
curl -X POST "http://127.0.0.1:6100/peer/transactions"
-d '{"transactions":[<A valid transactions object>]}' 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "transaction":
      {
        "type":0,
        "amount":10000000,
        "fee":10000000,
        "recipientId":"Sa9JKodiNeM7tbYjxwEhvvG1kBczhQxTN3",
        "timestamp":9165933,
        "asset":{},
        "senderPublicKey":"03675c61dcc23eab75f9948c6510b54d34fced4a73d3c9f2132c76a29750e7a614",
        "signature":"304402201342810cdd2db452aff3b4c6367101a6973f40d7d4601647a8433c7bc547bde902202629f5fae8405097147edb8e10839d58dc56f1f154dfe3db3a3dcfd7acf4bdb9",
        "id":"477c43012b1720de6f924918ad1ee7e41fc74ef5ed30ed628ea3af877ad203f1"
      }
  }
]
```

JSON Response

### HTTP Request

`POST http://127.0.0.1:6100/peer/transactions`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
transactions | string<br>(header) | A valid transaction object
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100
