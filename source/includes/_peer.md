# Peers

## Get a single peer

```shell
curl -X GET "http://127.0.0.1:6100/api/peers/get?ip={IP}&port={Port}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/peers/get?ip={IP}&port={Port} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "peer":
      {
        "ip":"215.130.200.190",
        "port":6100,
        "version":"0.0.2",
        "errors":0,
        "os":"linux4.13.0-26-generic",
        "height":836660,
        "status":"OK",
        "delay":37
      }
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/peers/get?ip={IP}&port={Port}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
ip | string<br>(query) | A valid server IP
port | integer<br>(query) | A valid server Port
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get all peers

```shell
curl -X GET "http://127.0.0.1:6100/api/peers" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/peers HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "peer":
      {
        "ip":"215.130.200.190",
        "port":6100,
        "version":"0.0.2",
        "errors":0,
        "os":"linux4.13.0-26-generic",
        "height":836660,
        "status":"OK",
        "delay":37
      }
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/peers`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
state  | integer<br>(query) | An unsigned integer that specifies the peer state.
port | integer<br>(query) | A valid peer Port
os | integer<br>(query) | A valid operating system
version | string<br>(query) | A valid node version
limit | integer<br>(query) | An unsigned integer that specifies the maximum number of records
offset | integer<br>(query) | An unsigned integer that specified the number of records to skip
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get the peer version

```shell
curl -X GET "http://127.0.0.1:6100/api/peers/version" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/peers/version HTTP/1.1
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

`GET http://127.0.0.1:6100/api/peers/version`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100
