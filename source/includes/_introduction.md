# Introduction

[![Build Status](https://travis-ci.org/smartholdem/api-doc.svg?branch=master)](https://travis-ci.org/smartholdem/api-doc)
[![Release](https://img.shields.io/github/release/smartholdem/api-doc.svg)](https://github.com/smartholdem/api-doc/releases/latest)

Welcome to the official documentation SmartHoldem API! You can use our API to access SmartHoldem API endpoints Node-A.

We have language bindings in Shell, HTTP!
You can view code examples in the dark area to the right,
and you can switch the programming language of the examples with the tabs in the top right.


connect to the mainnet api, use the link to node: <code>http://127.0.0.1:6100/api/</code>

parameter | type | request | mainnet
--------- | ------- | ----------- | -----------
nethash | string | header | fc46bfaf9379121dd6b09f5014595c7b7bd52a0a6d57c5aff790b42a73c76da7
port | integer | header | 6100


connect to the devnet api, use the link to node: <code>http://80.211.38.83:6101/api/</code>

parameter | type | request | devnet
--------- | ------- | ----------- | -----------
nethash | string | header | 3a6d2bec6798dedea99a1e6c64120a3876781b85e46bb75908aba07ffda61360
port | integer | header | 6101
addr version | integer | - | 30
slip 44 | integer | - | 1
