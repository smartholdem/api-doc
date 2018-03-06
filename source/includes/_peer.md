# Peers

## Get a single peer

```shell
curl -X GET "http://127.0.0.1/api/peers/get?ip={IP}&port={Port}" 
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
