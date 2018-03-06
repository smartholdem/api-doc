# Delegate

## Get the count of delegates

```shell
curl -X GET "http://127.0.0.1/api/delegates/count" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/delegates/count HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "count":234
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/delegates/count`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Search for specific delegates

```shell
curl -X GET "http://127.0.0.1/api/delegates/search?q={DelegateName}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/delegates/search?q={DelegateName} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "delegates":
      [
        {
          "username":"davinchi",
          "address":"SRSDXgqkDpkdvfLWymW4GkXfqqhDydDpKn",
          "publicKey":"02be233e7d9e46407cdcdc5793a792b52f399cab61ccd8eb256a32a6cd06b5b7d3",
          "vote":"274851156039575",
          "producedblocks":13026,
          "missedblocks":58
        }
      ]
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/delegates/search?q={DelegateName}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
q | string<br>(query) | A search query.
limit | integer<br>(query) | An unsigned integer that specifies the maximum number of records.
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100
