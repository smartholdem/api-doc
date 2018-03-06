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

## Get the BlockChain status

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
