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
