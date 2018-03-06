# Blocks

## Get block by id

```shell
curl -X GET "http://127.0.0.1/api/blocks/get?id={blockid}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/blocks/get?id={blockid} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "block":
      {
        "id":"17539280775357750950",
        "version":0,
        "timestamp":9068960,
        "height":833616,
        "previousBlock":"16727550229762671827",
        "numberOfTransactions":1,
        "totalAmount":17000000000,
        "totalFee":10000000,
        "reward":200000000,
        "payloadLength":32,
        "payloadHash":"d2db523d5f904f06e264a6cd07ae7eb3d910de3d8513f78c322ff62e889ead0f",
        "generatorPublicKey":"0352323bcc05b7eb8f67d30cf6c68c31f55fdb1ae502089ec53be7bd6066aa0cc3",
        "generatorId":"SekmmTz5t31QsRuiiQYxtBmhaZ3sTRJqTR",
        "blockSignature":"304402204fa031c043edf8b9eda482447424f515079e91f0babb6750804fc0fcea5ae60e022010b1d869b9cbe439035c381ff21366cc92bc36156c2f09a50c2eacb3122ca14c",
        "confirmations":1469,
        "totalForged":"210000000"
      }
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/blocks/get?id={blockid}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | string<br>(query) | SmartHoldem block id
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get all blocks

```shell
curl -X GET "http://127.0.0.1/api/blocks?limit={limit}&orderBy={orderByFieldName}&offset={offset}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/blocks?limit={limit}&orderBy={orderByFieldName}&offset={offset} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "blocks":
      [
        {
          "id":"9116970896546202944",
          "version":0,
          "timestamp":0,
          "height":1,
          "previousBlock":null,
          "numberOfTransactions":468,
          "totalAmount":24000000000000000,
          "totalFee":0,"reward":0,
          "payloadLength":98905,
          "payloadHash":"fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7",
          "generatorPublicKey":"03b2000d0e5042e82aed1fe7d7b556ba7cbc921406fe65cc3881652115f843fbb9",
          "generatorId":"SVx2j3NdZbDLfZ9HWS57NvqYg4c9grQLnx",
          "blockSignature":"30450221008f8426d8777668ed54147227577f86757d754e66872b9f1afd0b408431e4e2fc02200fed52f899e793beebefcea5d261ef04ef178ae5148ce74c33bee3cc6290daf7",
          "confirmations":835148,
          "totalForged":"0"
        },
        {
          "id":"16196929714027847359",
          "version":0,
          "timestamp":2018712,
          "height":2,
          "previousBlock":"9116970896546202944",
          "numberOfTransactions":2,
          "totalAmount":100000000,
          "totalFee":5510000000,
          "reward":0,
          "payloadLength":64,
          "payloadHash":"d10891c597ab873a024b6d3204c77919bc0c1cfc71637c8c280f2984719002ff",
          "generatorPublicKey":"024fb81d61afe6dec253236a210822f1c5fb93ee2f944751df5d0c4b1d0fb29059",
          "generatorId":"Sea51MNodyxQRdGGWpTpHj38ZnrKrDFaHk",
          "blockSignature":"3044022076254a6bd3e6b6c49c07309253000b8dc0ca0f0a6cd9e6b876f53ec685f274ee0220336400f106111a66932fa922867bc28d3c66fdf29bb65c93cf661be0d7278e7d",
          "confirmations":835147,
          "totalForged":"5510000000"
        }
      ],
    "count":835148
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/blocks?limit={limit}&orderBy={orderByFieldName}&offset={offset}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit | integer<br>(query) | An unsigned integer that specifies the maximum number of records.
orderBy | string<br>(query) | A string that specifies the column by which to sort the records.
offset | integer<br>(query) | An unsigned integer that specified the number of records to skip.
generatorPublicKey | string<br>(query) | A valid Public Key.
totalAmount | integer<br>(query) | amount
totalFee | integer<br>(query) | fee
reward | integer<br>(query) | reward
previousBlock | string<br>(query) |
height | integer<br>(query) | height
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100


## Get the BlockChain Epoch

```shell
curl -X GET "http://127.0.0.1/api/blocks/getEpoch" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/blocks/getEpoch HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "epoch":"2017-11-21T13:00:00.000Z"
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/blocks/getEpoch`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get the BlockChain Height

```shell
curl -X GET "http://127.0.0.1/api/blocks/getHeight" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/blocks/getHeight HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "height":835227,
    "id":"13808010658243907328"
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/blocks/getHeight`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get the BlockChain NetHash

```shell
curl -X GET "http://127.0.0.1/api/blocks/getNethash" 
-H "accept: application/json" 
-H "port: 6100"
```

```http
GET api/blocks/getHeight HTTP/1.1
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "nethash":"fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7"
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/blocks/getNethash`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
port | integer<br>(header) | 6100

## Get the Transaction Fee

```shell
curl -X GET "http://127.0.0.1/api/blocks/getFee" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/blocks/getFee HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "fee":10000000
  }
]
```

Get the transaction fee for sending "normal" transactions.

### HTTP Request

`GET http://127.0.0.1:6100/api/blocks/getFee`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100


## Get the Network Fees

```shell
curl -X GET "http://127.0.0.1/api/blocks/getFees" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/blocks/getFees HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "fees":
      {
        "send":10000000,
        "vote":100000000,
        "secondsignature":500000000,
        "delegate":5500000000,
        "multisignature":500000000
      }
  }
]
```

Get the all fees network.

### HTTP Request

`GET http://127.0.0.1:6100/api/blocks/getFees`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get the BlockChain Milestone

```shell
curl -X GET "http://127.0.0.1/api/blocks/getMilestone" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/blocks/getMilestone HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "milestone":0
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/blocks/getMilestone`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get the BlockChain Reward

```shell
curl -X GET "http://127.0.0.1/api/blocks/getReward" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/blocks/getReward HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "reward":200000000
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/blocks/getReward`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100
