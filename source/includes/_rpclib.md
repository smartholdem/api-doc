# RPC Daemon

## How To Use It

All calls should be made from the server where RPC is running at ( i.e., localhost or 127.0.0.1 ). 
The RPC server should never be publicly accessible. 
If you wish to access smartholdem-rpc from a remote address, you can whitelist the address with `--allow <address>`. 
Addresses allow you to use wildcards, eg. `192.168.1.* or 10.0.*.*.`
If you do want to allow access from all remotes, start smartholdem-rpc with the `--allow-remote` commandline switch. This can be dangerous.
This is an additional library. Works as a bitcoind.

```shell
git clone https://github.com/smartholdem/smartholdem-rpc.git
cd smartholdem-rpc
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.0/install.sh 2>/dev/null | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
nvm install 6.9.5 >>install.log
nvm use 6.9.5 >>install.log
nvm alias default 6.9.5
npm install -g npm
npm install forever -g
npm install grunt-cli -g
npm install

forever start server.js
```

- install Node.JS
- install forever npm install -g forever
- git clone https://github.com/smartholdem/smartholdem-rpc.git
- install smartholdem-rpc: npm install
- start RPC server: forever start server.js
- stop RPC server: forever stop server.js

`default port 8282`

<aside class="warning">
Security Warning! All calls should be made from the server where RPC is running at localhost or 127.0.0.1. The RPC server should never be publicly accessible.
</aside>

## Get account balance from address

```shell
curl -X GET "http://127.0.0.1:8282/mainnet/account/{address}"
-H "accept: application/json" 
```

> RESPONSE Get account balance from address

```json
[
  {
    "success":true,
    "account":
      {
        "address":"SUeGCt31AHwTZVcfZQwpPVL4jEUCtMMDTg",
        "unconfirmedBalance":"1440865700000000",
        "balance":"1440865700000000",
        "publicKey":"02babe75fc3f053e041f2258b11727c81b21bb690e69f2ea99b3121223b7536e56",
        "unconfirmedSignature":0,
        "secondSignature":0,
        "secondPublicKey":null,
        "multisignatures":[],
        "u_multisignatures":[]
      }
  }
]
```

`GET http://127.0.0.1:8282/mainnet/account/{address}`

## Create account from Pass Phrase

```shell
curl -X POST "http://127.0.0.1:8282/mainnet/account" 
-d '{"passphrase":"TestPassWord"}'
-H "Content-Type: application/json"
```

> RESPONSE Create account from Pass Phrase

```json
[
 {
  "success":true,
  "account":
    {
      "publicKey":"02f83b9419d8edbaeb095e05eba4c1685c25443bbf848125392960f38b315b6eb0",
      "address":"ScXk96ma9D1m2w7bFbNUKx1yjbWCCEYMY5"
    }
 }
]
```

`POST http://127.0.0.1:8282/mainnet/account`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
passphrase | string<br>(query) | secret passphrase

## Create/Get account from BIP38

Create (or get if already existing) account and encrypt using bip38

```shell
curl -X POST "http://127.0.0.1:8282/mainnet/account/bip38" 
-d '{"bip38":"MasterPassword", "userid":"useridstring"}'
-H "Content-Type: application/json"
```

> RESPONSE

```json
[
  {
    "success":true,
    "publicKey":"0371a0038eebac8f7e47e0bd10128a3dbe951d96bb09560cf972c05c31edb1cc2e",
    "address":"SWSbAHmCrovRfMzQwkuhMoymMPXDZBw5jx",
    "wif":"6PYR6wexqVbcfGjUo6gKKW7nYaVowVo3qSDXjXRsLTBDWTepH22kbLMsJT"
  }
]
```

`POST http://127.0.0.1:8282/mainnet/account/bip38`

<aside class="info">
If you want to create several accounts for one user, you need to use a different userid.
</aside>


### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
bip38 | string<br>(query) | master password
userid | string<br>(query) | any username

## GET backup account from userid

```shell
curl -X GET "http://127.0.0.1:8282/{network}/account/bip38/{userid}"
-H "accept: application/json" 
```

{network} - mainnet or testnet

> RESPONSE

```json
[
  {
    "success":true,
    "wif":"6PYR6wexqVbcfGjUo6gKKW7nYaVowVo3qSDXjXRsLTBDWTepH22kbLMsJT"
  }
]
```

`GET http://127.0.0.1:8282/{network}/account/bip38`

## Get last transactions from address

```shell
curl -X GET "http://127.0.0.1:8282/{network}/transactions/{address}"
-H "accept: application/json" 
```

{network} - mainnet or testnet

> RESPONSE

```json
[
  {
    "success":true,
    "transactions":
      [
        {
          "id":"c025f70cb32b9cfbf9160b95237c92d41644e1fdd4ead4a0052a07ffb5b97921",
          "blockid":"15547375374841204258",
          "type":0,
          "timestamp":9156817,
          "amount":17000000000,
          "fee":10000000,
          "senderId":"Sf6y6bFqdPiXt9qupmTdpJFJwBWmMCfs43",
          "recipientId":"SZg73u3rVrqwahfZ2tU6G1E3YwDs52tMeW",
          "senderPublicKey":"03e340952f7d726d8598b4ae68e88e583b39735c35b489559e082c705dba50376e",
          "signature":"3045022100a2d732a3139ddbdaf27b9335894544fbcf590604c7e5a60a1ec72f295348f86402202f415d115c3390a6a45e81fec8c5f0177511aa421fd4ceb448262b334233ca96",
          "asset":{},
          "confirmations":927
        },
        {
          "id":"41616c6d8393a55b3c911b400b14433e83ee3e3caf4dcedfb1684019b8566a3c",
          "blockid":"13256355616806784710",
          "type":0,
          "timestamp":9156745,
          "amount":17000000000,
          "fee":10000000,
          "senderId":"Sf6y6bFqdPiXt9qupmTdpJFJwBWmMCfs43",
          "recipientId":"SkaPmhW8FwiZ1g64yEnyvcGRpY9ZyauPjz",
          "senderPublicKey":"03e340952f7d726d8598b4ae68e88e583b39735c35b489559e082c705dba50376e",
          "signature":"30440220141c637637bc40e14a5d49ada9257b487faff1061835c730325c05595fb7b582022065f8f0259baf41f49cba2b163b0d4934e12ca3a20239c36dce1e870bf9660cf7",
          "asset":{},
          "confirmations":935
        },
        ...
      ],
    "count":"132"
  }
]
```

`GET http://127.0.0.1:8282/{network}/transactions/{address}`

## Create a transaction

```shell
curl -X POST "http://127.0.0.1:8282/{network}/transaction" 
-d '{"recipientId":"<address>","amount":"<AmountInSatoshi>","passphrase":"<SenderAddressPassPhrase>"}'
-H "Content-Type: application/json"
```

> RESPONSE

```json
[
  {
    "success":true,
    "transaction":
      {
        "type":0,
        "amount":10000000,
        "fee":10000000,
        "recipientId":"Sa9JKodiNeM7tbYjxwEhvvG1kBczhQxTN3",
        "timestamp":9165933,
        "asset":{},
        "senderPublicKey":"03675c61dcc23eab75f9948c6510b54d34fced4a73d3c9f2132c76a29750e7a614",
        "signature":"304402201342810cdd2db452aff3b4c6367101a6973f40d7d4601647a8433c7bc547bde902202629f5fae8405097147edb8e10839d58dc56f1f154dfe3db3a3dcfd7acf4bdb9",
        "id":"477c43012b1720de6f924918ad1ee7e41fc74ef5ed30ed628ea3af877ad203f1"
      }
  }
]
```

`POST http://127.0.0.1:8282/{network}/transaction`

Example:

`curl -H "Content-Type: application/json" -X POST "http://127.0.0.1:8081/mainnet/transaction" -d '{"recipientId":"Sa9JKodiNeM7tbYjxwEhvvG1kBczhQxTN3","amount":"10000000","passphrase":"this is a test"}'`

<aside class="info">
Note that if the transaction has been created via the RPC it has been stored internally, as such only the transaction id is needed to broadcast/rebroadcast it. Otherwise if created outside of this RPC server, pass the whole transaction body as the POST payload.
</aside>

## Broadcast transaction

```shell
curl -X POST "http://127.0.0.1:8282/{network}/broadcast" 
-d '{"id":"<id of the transaction>"}'
-H "Content-Type: application/json"
```

> RESPONSE

```json
[
  {
    "success":true,
    "transaction":
      {
        "type":0,
        "amount":10000000,
        "fee":10000000,
        "recipientId":"Sa9JKodiNeM7tbYjxwEhvvG1kBczhQxTN3",
        "timestamp":9165933,
        "asset":{},
        "senderPublicKey":"03675c61dcc23eab75f9948c6510b54d34fced4a73d3c9f2132c76a29750e7a614",
        "signature":"304402201342810cdd2db452aff3b4c6367101a6973f40d7d4601647a8433c7bc547bde902202629f5fae8405097147edb8e10839d58dc56f1f154dfe3db3a3dcfd7acf4bdb9",
        "id":"477c43012b1720de6f924918ad1ee7e41fc74ef5ed30ed628ea3af877ad203f1"
      }
  }
]
```

`POST http://127.0.0.1:8282/{network}/broadcast`

Example: 

`curl -X POST "http://127.0.01:8282/mainnet/broadcast" -H "accept: application/json" -H "content-type: application/json" -d '{"id":"477c43012b1720de6f924918ad1ee7e41fc74ef5ed30ed628ea3af877ad203f1"}'`

## Create a transaction using bip38

```shell
curl -X POST "http://127.0.0.1:8282/{network}/transaction/bip38" 
-d '{"recipientId":"<recipientId>","amount":"<in satoshis>","bip38":"<password to encode wif>","userid":"<useridBip38>"}'
-H "Content-Type: application/json"
```

> RESPONSE

```json
[
  {
    "success":true,
    "transaction":
      {
        "type":0,
        "amount":10000000,
        "fee":10000000,
        "recipientId":"Sa9JKodiNeM7tbYjxwEhvvG1kBczhQxTN3",
        "timestamp":9165933,
        "asset":{},
        "senderPublicKey":"03675c61dcc23eab75f9948c6510b54d34fced4a73d3c9f2132c76a29750e7a614",
        "signature":"304402201342810cdd2db452aff3b4c6367101a6973f40d7d4601647a8433c7bc547bde902202629f5fae8405097147edb8e10839d58dc56f1f154dfe3db3a3dcfd7acf4bdb9",
        "id":"477c43012b1720de6f924918ad1ee7e41fc74ef5ed30ed628ea3af877ad203f1"
      }
  }
]
```

`POST http://127.0.0.1:8282/{network}/broadcast`

Example: 

`curl -X POST "http://127.0.01:8282/mainnet/broadcast" -H "accept: application/json" -H "content-type: application/json" -d '{"id":"477c43012b1720de6f924918ad1ee7e41fc74ef5ed30ed628ea3af877ad203f1"}'`
