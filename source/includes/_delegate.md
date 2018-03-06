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
q | string<br>(query) | A search query
limit | integer<br>(query) | An unsigned integer that specifies the maximum number of records
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get a list of voters for a delegate

```shell
curl -X GET "http://127.0.0.1/api/delegates/voters?publicKey={publicKey}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/delegates/voters?publicKey={publicKey} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "accounts":
      [
        {
          "username":"gendelegate_8",
          "address":"Sgx3VdXJyKGdNrtLP6J569zuWrevqA4qc1",
          "publicKey":"02202a328734a92dda73673e8d163cd33a1047b05ca3c83508011883557f4c843e",
          "balance":"16498890000000"
        },
        {
          "username":null,
          "address":"SRsTDAb5UvxpubvhR4xN4PBP3zsAjn88wH",
          "publicKey":"03b04b6afc16b57923021d3f3eb89dc4efc8d7e975a1ecbfbeaca40ea4d61485b4",
          "balance":"2631764374584"
        }
      ]
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/delegates/voters?publicKey={publicKey}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
publicKey  | string<br>(query) | A valid Public Key
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get a single delegate

```shell
curl -X GET "http://127.0.0.1/api/delegates/get?publicKey={publicKey}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/delegates/get?publicKey={publicKey} HTTP/1.1
nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
host: 127.0.0.1:6100
```

> The above command returns JSON structured like this:

```json
[
  {
    "success":true,
    "delegate":
      {
        "username":"tomray",
        "address":"SMNwAWtVnkPjYrLG9wgtpwRG3nwxVQpL3x",
        "publicKey":"0393dbe9e234b98b66c517b8ebff2b8c6649dd2fab9c33dd14616c4551458e6dff",
        "vote":"228633454374584",
        "producedblocks":10314,
        "missedblocks":237,
        "rate":4,
        "approval":0.95,
        "productivity":97.75
      }
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/delegates/get?publicKey={publicKey}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
publicKey  | string<br>(query) | A valid Public Key
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

## Get all delegates

```shell
curl -X GET "http://127.0.0.1/api/delegates?limit={limit}&offset={offset}" 
-H "accept: application/json" 
-H "nethash: fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7" 
-H "version: 0.0.2" 
-H "port: 6100"
```

```http
GET api/delegates/get?limit={limit}&offset={offset} HTTP/1.1
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
          "username":"terra",
          "address":"SkLRQb6cFPdCpVDNLyQKtwUeUtwH3Mm5yf",
          "publicKey":"0364b75b76624a97776bccc602e4a21864ac2f792b097841a2f6e2495d994b463b",
          "vote":"120074817218230",
          "producedblocks":6389,
          "missedblocks":333,
          "rate":65,
          "approval":0.5,
          "productivity":0
        },
        {
          "username":"old_susanin",
          "address":"SkK3c5UfZoa2T9fTM2iEw81HxqS7EisrTm",
          "publicKey":"027a4f588f2ebd3498fb94e3b468139b9ab4a4cc9a0044dfe5ac8bc3c2f48a909f",
          "vote":"113259700000000",
          "producedblocks":1058,
          "missedblocks":360,
          "rate":66,
          "approval":0.47,
          "productivity":0
        }
      ],
    "totalCount":234
  }
]
```

JSON Response

### HTTP Request

`GET http://127.0.0.1:6100/api/delegates?limit={limit}&offset={offset}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
orderBy   | string<br>(query) | A string that specifies the column by which to sort the records.
limit    | integer<br>(query) | An unsigned integer that specifies the maximum number of records.
offset   | integer<br>(query) | An unsigned integer that specified the number of records to skip.
nethash | string<br>(header) | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
version | string<br>(header) | 0.0.2
port | integer<br>(header) | 6100

