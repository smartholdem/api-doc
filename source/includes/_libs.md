# Libraries

Additional Libraries

## RPC Daemon

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

How To Use It:

- install Node.JS
- install forever npm install -g forever
- git clone https://github.com/smartholdem/smartholdem-rpc.git
- install smartholdem-rpc: npm install
- start RPC server: forever start server.js
- stop RPC server: forever stop server.js

default port 8282

### Accounts:

Get account balance from address:

`GET https://127.0.0.1:8282/mainnet/account/{address}`

> Get account balance

```shell
curl -X GET "http://127.0.0.1:8282/mainnet/account/{address}" -H "accept: application/json" 
```

> RESPONSE

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

<aside class="warning">
Security Warning! All calls should be made from the server where RPC is running at localhost or 127.0.0.1. The RPC server should never be publicly accessible.
</aside>
