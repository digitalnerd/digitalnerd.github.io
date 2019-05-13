---
layout: post
title: Install Node.js
---
## Install Node.js to CentOS 7
```bash
$ sudo yum install -y gcc-c++ make
$ curl -sL https://rpm.nodesource.com/setup_10.x | sudo -E bash -
$ sudo yum install -y nodejs
$ node -v
v10.15.3
$ npm -v
6.4.1
```
