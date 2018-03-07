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

`http://127.0.0.1:8282/{network}/account/bip38/{userid}`
