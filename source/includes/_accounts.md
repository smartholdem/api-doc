# Accounts

## Get the balance of an account

```shell
curl -X GET "http://127.0.0.1:6100/api/accounts/getBalance?address={address}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
```

```http
GET api/accounts/getBalance?address={address} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success": true,
    "balance": "45848090000000",
    "unconfirmedBalance": "45848090000000"
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/accounts/getBalance?address={address}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
address | string<br>(query) | SmartHoldem Address
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

<aside class="success">
balance & unconfirmedBalance should be equal
</aside>

## Get the public key of an account

```shell
curl -X GET "http://127.0.0.1:6100/api/accounts/getPublickey?address={address}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2"
```

```http
GET api/accounts/getPublickey?address={address} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success": true,
    "publicKey": "030751d7c998d7f6c901bd78fb1516413d05f1384121af9b69ff6eb3a76f7107e9"
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/accounts/getPublickey?address={address}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
address | string<br>(query) | SmartHoldem Address
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100


## Get the delegate fee of an account

```shell
curl -X GET "http://127.0.0.1:6100/api/accounts/delegates/fee" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2"
```

```http
GET api/accounts/delegates/fee HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success": true,
    "fee": "5500000000"
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/accounts/delegates/fee`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get the delegates of an account

```shell
curl -X GET "http://127.0.0.1:6100/api/accounts/delegates?address={address}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
```

```http
GET api/accounts/delegates?address={address} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success": true,
    "delegates": [
      {
        "username":"bitshill",
        "address":"SPvhZpt4qEYHLrUDqeHhu1H1qtmkK3xovH",
        "publicKey":"030751d7c998d7f6c901bd78fb1516413d05f1384121af9b69ff6eb3a76f7107e9",
        "vote":"45848090000000",
        "producedblocks":1466,
        "missedblocks":2172,
        "rate":71,
        "approval":0.19,
        "productivity":0
      }
    ]
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/accounts/delegates?address={address}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
address | string<br>(query) | SmartHoldem Address
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Returns account information of an address

```shell
curl -X GET "http://127.0.0.1:6100/api/accounts?address={address}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2"
```

```http
GET api/accounts?address={address} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "account":
      {
        "address":"SPvhZpt4qEYHLrUDqeHhu1H1qtmkK3xovH",
        "unconfirmedBalance":"45848090000000",
        "balance":"45848090000000",
        "publicKey":"030751d7c998d7f6c901bd78fb1516413d05f1384121af9b69ff6eb3a76f7107e9",
        "unconfirmedSignature":0,
        "secondSignature":0,
        "secondPublicKey":null,
        "multisignatures":[],
        "u_multisignatures":[]
      }
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/accounts?address={address}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
address | string<br>(query) | SmartHoldem Address
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get a list of top accounts

```shell
curl -X GET "http://127.0.0.1:6100/api/accounts/top?limit={limit}&offset={offset}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2"
```

```http
GET api/accounts/top?limit={limit}&offset={offset} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "accounts":[
      {
        "address":"SUeGCt31AHwTZVcfZQwpPVL4jEUCtMMDTg",
        "balance":"1440865700000000",
        "publicKey":"02babe75fc3f053e041f2258b11727c81b21bb690e69f2ea99b3121223b7536e56"
      },
      {
        "address":"STwo9GdFTNeCJZkbQYuqBRnN1jgPqsKrr6",
        "balance":"800001000000000",
        "publicKey":null
      },
      {
        "address":"SMTku8XXxSDcnYxvWsfX5D2AMZwVjdrBe6",
        "balance":"720000000000000",
        "publicKey":null
      }
    ]
  }
]
```

Return JSON.

### HTTP Request

`GET http://127.0.0.1:6100/api/accounts/top?limit={limit}&offset={offset}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit  | integer<br>(query) | An unsigned integer that specifies the maximum number of records.
offset | integer<br>(query) | An unsigned integer that specified the number of records to skip.
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

<aside class="info">
Your node must be running with a parameter <code>TOP=true forever start app.js</code>
<br>if <code>"publicKey":null</code> this address did not have outgoing transactions
</aside>
