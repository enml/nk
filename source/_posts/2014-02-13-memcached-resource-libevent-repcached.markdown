---
layout: post
title: "memcached专题：相关依赖资源-libevent-repcached"
description: memcached的依赖：libevent和repcached
date: 2014-02-13 23:17:23 +0800
comments: true
tags: memcached
categories: memcached
---

### 1. `memcached`

	# yum info memcached

如果发行版自带的memcached版本太旧，进入[memcached网站](https://code.google.com/p/memcached/), 下载源码自己安装，当前最新版本位1.4.15.


### 2. `libevent-devel`
	
	# yum info libevent libevent-devel

如果yum安装的版本太旧，进入[libevent网站](https://github.com/downloads/libevent/libevent/libevent-2.0.21-stable.tar.gz)，下载源码自行安装，当前最新版本位2.0.21


### 3. `repcached`

一种是补丁，一种是与memcached集成版。

集成版[下载地址](https://github.com/mdounin/memcached/tree/repcached)（最新支持1.4.13）

补丁版[下载地址](http://mdounin.ru/files/repcached-2.3.1-1.4.13.patch.gz) 或者[这里](https://github.com/usecide/repcached/)；repcached的[官方网站](http://repcached.lab.klab.org/)，但是好久没更新了。

安装请参考前一篇博文：[Memcached安装libevent-repcached-memcached](http://nkcoder.github.io/blog/20140213/memcached-install-libevent-repcached-memcached/)

