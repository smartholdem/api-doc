# Loader

## Get the BlockChain Status

```shell
curl -X GET "http://127.0.0.1/api/loader/status" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/loader/status HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "loaded":false,
    "now":836088,
    "blocksCount":0
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/loader/status`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get the synchronisation status of the client

```shell
curl -X GET "http://127.0.0.1/api/loader/status/sync" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/loader/status/sync HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "syncing":false,
    "blocks":1,
    "height":836128,
    "id":"11305115970511710322"
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/loader/status/sync`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Auto-configure the client loader

```shell
curl -X GET "http://127.0.0.1/api/loader/autoconfigure" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/loader/autoconfigure HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "network":
      {
        "nethash":"fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7",
        "token":"STH",
        "symbol":"STH",
        "explorer":"https://blockexplorer.smartholdem.io",
        "version":63
      }
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/loader/autoconfigure`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100
