---
title: "Inside Node.Js I/O"
datePublished: Wed Jan 25 2023 05:59:15 GMT+0000 (Coordinated Universal Time)
cuid: cldb9altj000209mnbnfibrfd
slug: inside-nodejs-io
canonical: https://dev.to/rwik/inside-node-js-i-o-13jc
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/g5jpH62pwes/upload/b34a7822c4eae00a985c064a7df4da71.jpeg
tags: javascript, asynchronous, nodejs

---

Node.Js introduces itself as a asynchronous event driven JavaScript runtime. To achieve this asynchronous nature , node uses a open source library called [libuv](https://libuv.org/).

libuv even though built for Node , it is not exclusive to Node.js. There are plenty of other [projects](https://github.com/libuv/libuv/wiki/Projects-that-use-libuv) which uses libuv.

While network i/o is asynchronous , the same can't be said for disk i/o .  
libuv uses single threaded operation to use event loop and produce asynchronous network i/o . Mostly lib pool APIs are not thread safe as it is designed to work in single threaded mode only.

Disk i/o has some platform specific differences . Every major APIs for disk I/O has it's own limitations, this also increases complexity. So libuv uses blocking disk operations using thread pool.