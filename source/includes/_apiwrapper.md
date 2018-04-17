# JS API Wrapper

## Installation

```shell
# install
npm install https://github.com/smartholdem/sthjs-wrapper --save
```

## Initialization

Before you begin, choose a network to initialize a list of nodes in that network

```js
// init
var smartholdemApi = require("sth-api");
var network = "main" //or "dev"
smartholdemApi.init(network);
```

## -- JS Accounts --
Account related API calls.

## Get balance

Get the balance of an account.

> **Request**

```js
var smartholdemApi = require("sth-api")
smartholdemApi.getBalance("Address of the account", (error, success, response) => {
    console.log(response);
});
```

> Response

```json
{
  "success": true,
  "balance": Balance of account (Integer String),
  "unconfirmedBalance": "Unconfirmed balance of account (Integer String)"
}
```

## Get account public key

Get the public key of an account. If the account does not exist the API call will return an error.

> **Request**

```js
var smartholdemApi = require("sth-api")
smartholdemApi.getPublicKey("Address of the account", (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "publicKey": "Public key of account. (Hex String)"
}
```

## Get account

Returns account information of an address.

> **Request**

```js
var smartholdemApi = require("sth-api")
smartholdemApi.getAccount("Address of the account", (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "account": {
    "address": "Address of account. (String)",
    "unconfirmedBalance": "Unconfirmed balance of account. (String)",
    "balance": "Balance of account. (String)",
    "publicKey": "Public key of account. (Hex String)",
    "unconfirmedSignature": "If account enabled second signature, but it's still not confirmed. (0 or 1)",
    "secondSignature": "If account enabled second signature. (0 or 1)",
    "secondPublicKey": "Second signature public key. (Hex String)"
  }
}
```
## Get votes of account
Get votes by account address.

> **Request**

```js
var smartholdemApi = require("sth-api")
smartholdemApi.getVotes("Address of the account", (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "delegates": [
    {
        username: Delegate Name (String),
        address: Delegate Address (String),
        publicKey: Delegate public key (String),
        vote: Number of votes (Integer String),
        producedBlocks: Number of Blocks Produces (Integer),
        missedBlocks: Number of missed blocks (Integer),
        rate: Delegate rank (Integer)
        approval: Percent approval (float)
        productivity: Percent blocks forged (float)
    }
    ...
  ]
}
```

## -- JS Blocks --
Blocks manage API.

## Get block
Get block by id.

```js
var smartholdemApi = require("sth-api")
smartholdemApi.getBlock("id: Id of block", (err, success, response) => {
  console.log(response);
});
```

> **Response**

```json
{
    "success": true,
    "block": {
        "id": "Id of block. (String)",
        "version": "Version of block. (Integer)",
        "timestamp": "Timestamp of block. (Integer)",
        "height": "Height of block. (Integer)",
        "previousBlock": "Previous block id. (String)",
        "numberOfTransactions": "Number of transactions. (Integer)",
        "totalAmount": "Total amount of block. (Integer)",
        "totalFee": "Total fee of block. (Integer)",
        "payloadLength": "Payload length of block. (Integer)",
        "payloadHash": "Payload hash. (Hex String)",
        "generatorPublicKey": "Generator public key. (Hex String)",
        "generatorId": "Generator id. (String)",
        "blockSignature": "Block signature. (Hex)"
    }
}
```

## Get blocks
Get all blocks.

```js
var smartholdemApi = require("sth-api")
var parameters = {
  "totalFee: total fee of block. (Integer)",
  "totalAmount: total amount of block. (Integer)",
  "previousBlock: previous block of need block. (String)",
  "height: height of block. (Integer)",
  "generatorPublicKey: generator id of block in hex. (String)",
  "limit: limit of blocks to add to response. Default to 20. (Integer)",
  "offset: offset to load blocks. (Integer)",
  "orderBy: field name to order by. Format: fieldname:orderType. Example: height:desc, timestamp:asc (String)"
};

smartholdemApi.getBlocks(parameters, (error, success, response) => {
  console.log(response);
});
```

All parameters joins by OR.

> **Response**
```
{
  "success": true,
  "blocks": [
    "array of blocks"
  ]
}
```

## Get blockchain fee
Get transaction fee for sending "normal" transactions.

```js
var smartholdemApi = require("sth-api")

smartholdemApi.getBlockchainFee((error, success, response) => {
  console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "fee": "fee amount"
}
```

## Get blockchain height
Get blockchain height.

```js
var smartholdemApi = require("sth-api")

smartholdemApi.getBlockchainHeight((error, success, response) => {
  console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "height": Height of blockchain. (Integer)
}
```

## Get forged by account
Get amount forged by account.

```js
var smartholdemApi = require("sth-api")

smartholdemApi.getForgedByAccount("Delegate public key (String)",
                          (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "sum": Forged amount (Integer)
}
```

## -- JS Delegates --
Delegates API.

**Enable delegate on account**

Calls for delegates

## Get delegate
Get delegate by username.

> **Request**

```js
var smartholdemApi = require("sth-api");

smartholdemApi.getDelegate("username of delegate", (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
    "success": true,
    "delegate": {
        username: Delegate Name (String),
        address: Delegate Address (String),
        publicKey: Delegate public key (String),
        vote: Number of votes (Integer String),
        producedBlocks: Number of Blocks Produces (Integer),
        missedBlocks: Number of missed blocks (Integer),
        rate: Delegate rank (Integer)
        approval: Percent approval (float)
        productivity: Percent blocks forged (float)
    }
}
```

## Get delegates
Get delegates list.

> **Request**

```js
var smartholdemApi = require("sth-api");
var parameters = {
  "limit: Limit to show. Integer. (Integer)",
  "offset: Offset (Integer)",
  "orderBy: Order by field (String)"
};

smartholdemApi.getDelegates(parameters, (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "delegates": [Array of delegate objects]
}
```

## Get Next Forgers
Get delegates next in line to forge

> **Request**

```js
var smartholdemApi = require("sth-api");
smartholdemApi.getNextForgers((error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "currentBlock": Current block height (Integer),
  "currentSlot": Current slot (integer),
  "delegates": [Array of delegate public keys in order of forging]
}
```


## Get votes of account
Get votes by account address.

> **Request**

```js
var smartholdemApi = require("sth-api");
smartholdemApi.getVotes("Address of the account. (String)", (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "delegates": [array of delegates]
}
```

## Get voters
Get voters of delegate.

> **Request**

```js
var smartholdemApi = require("sth-api");
smartholdemApi.getVoters("Public key of delegate. (String)", (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "accounts": [array of accounts who voted for delegate]
}
```

