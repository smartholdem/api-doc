# JS API Wrapper

## Installation

https://github.com/smartholdem/sthjs-wrapper

```shell
# install
npm install --save sthjs-wrapper
```

## Initialization

Before you begin, choose a network to initialize a list of nodes in that network

```js
// init
var smartholdemApi = require("sthjs-wrapper");
var network = "main" //or "dev"
smartholdemApi.init(network);
```

## -- JS Accounts --
Account related API calls.

## Get balance

Get the balance of an account.

> **Request**

```js
var smartholdemApi = require("sthjs-wrapper")
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
var smartholdemApi = require("sthjs-wrapper")
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
var smartholdemApi = require("sthjs-wrapper")
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
var smartholdemApi = require("sthjs-wrapper")
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
var smartholdemApi = require("sthjs-wrapper")
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
var smartholdemApi = require("sthjs-wrapper")
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
var smartholdemApi = require("sthjs-wrapper")

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
var smartholdemApi = require("sthjs-wrapper")

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
var smartholdemApi = require("sthjs-wrapper")

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
var smartholdemApi = require("sthjs-wrapper");

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
var smartholdemApi = require("sthjs-wrapper");
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
var smartholdemApi = require("sthjs-wrapper");
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
var smartholdemApi = require("sthjs-wrapper");
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
var smartholdemApi = require("sthjs-wrapper");
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

## -- JS Peers --
Peers API.

## Get peers list
Get peers list by parameters.

> **Request**

```js
var smartholdemApi = require("sthjs-wrapper")
smartholdemApi.getPeersList((error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "peers": [
    {
        ip: IP Address (String),
        port: Port number (Integer),
        version: Node version (String),
        errors: Errors (Integer),
        os: Operating System (String),
        height: Block height (Integer),
        status: Node status (String),
        delay: Ping (Integer)
    }
    ...
  ]
}
```

## Get peer
Get peer by ip and port

> **Request**

```js
var smartholdemApi = require("sthjs-wrapper")

smartholdemApi.getPeer("ip: Ip of peer. (String)",
               "port: Port of peer. (Integer)",
               (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "peer": {peer object}
}
```

## Get peer version, build time
Get peer version and build time

> **Request**

```js
var smartholdemApi = require("sthjs-wrapper")
smartholdemApi.getPeerVersion((error, success, response) => {
  console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "version": "version of SmartHoldem Peer",
  "build": "time of build"
}
```

## -- JS Transactions --
API calls related to transactions


## Create Transaction
Creates a transaction object to be sent

> **Example**

```js
var smartholdemApi = require("sthjs-wrapper");
var options = {
  vendorField: "Smartbridge field (optional)",
  secondPassphrase: "Sender second passphrase (optional)"
};
var transaction = smartholdemApi.createTransaction("Sender passphrase",
                      "Address of recipient",
                      "Amount to send in 10^8 (Integer)",
                      options);
console.log(transaction);
```

## Create Delegate Transaction
Creates a delegate registration transaction to be sent

> **Example**

```js
var smartholdemApi = require("sthjs-wrapper");
var transaction = smartholdemApi.createDelegateTransaction("Passphrase",
                      "Delegate name",
                      "Second passphrase (optional)");
console.log(transaction);
```

## Create Second Signature Transaction
Creates a second signature transaction to be sent

> **Example**

```js
var smartholdemApi = require("sthjs-wrapper");
var transaction = smartholdemApi.createSecondSignatureTransaction("Passphrase",
                      "Second passphrase");
console.log(transaction);
```

## Create Vote Transaction
Creates a vote transaction to be sent

> **Example**

```js
var smartholdemApi = require("sthjs-wrapper");
var transaction = smartholdemApi.createVoteTransaction("Passphrase",
                      ["+58199578191950019299181920120128129"] //Array of vote strings
                      "Second passphrase");
console.log(transaction);
```

## Send transactions
Broadcasts an array of transactions to multiple nodes

> **Example**

```js
var smartholdemApi = require("sthjs-wrapper");
var transaction = smartholdemApi.sendTransactions([Transactions array], (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
    success: true,
    transactionIds: [
    "ID of transaction that was sent (String)",
    "ID of transaction that was sent (String)",
    "ID of transaction that was sent (String)",
    ...
    ]
}
```

## Get list of transactions
Transactions list matched by provided parameters.

> **Request**

```js
var smartholdemApi = require("sthjs-wrapper");

var parameters = {
  "blockId": "Block id of transaction. (String)",
  "senderId": "Sender address of transaction. (String)",
  "recipientId": "Recipient of transaction. (String)",
  "limit": "Limit of transaction to send in response. Default: 20. Max: 50 (Integer number)",
  "offset": "Offset to load. (Integer number)",
  "orderBy": "Name of column to order. After column name must go 'desc' or 'asc' to choose order type. Example: orderBy=timestamp:desc (String)"
};

smartholdemApi.getTransactionsList(parameters, (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "transactions": [
    {
        id: Transaction ID (String),
        blockid: Block ID (Integer String),
        type: Transaction type (Integer),
        timestamp: Seconds since genesis block (Integer),
        amount: Transaction amount (Integer)
        fee: Transaction fee (Integer),
        venderField: Vender field/Smartbridge (String),
        senderId: Sender address (String),
        recipientId: Recipient address (String),
        senderPublicKey: Sender public key (String),
        signature: Transaction signature (String),
        asset: Asset (Object),
        confirmations: Number of confirmations (Integer)
    }
    count: Number of results (String)
  ]
}
```

## Get transaction
Transaction matched by id.

> **Request**

```js
var smartholdemApi = require("sthjs-wrapper");
smartholdemApi.getTransaction("String of transaction (String)", (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "transaction": {Transaction Object}
}
```

## Get unconfirmed transaction
Get unconfirmed transaction by id.

> **Request**

```js
var smartholdemApi = require("sthjs-wrapper");
smartholdemApi.getUnconfirmedTransaction("String of transaction (String)", (error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
  "success": true,
  "transaction": {Transaction Object}
}
```

## Get list of unconfirmed transactions
Get list of unconfirmed transactions.

> **Request**

```js
var smartholdemApi = require("sthjs-wrapper");
smartholdemApi.getUnconfirmedTransactions((error, success, response) => {
    console.log(response);
});
```

> **Response**

```json
{
    "success" : true,
    "transactions" : [list of transaction objects]
}
```
