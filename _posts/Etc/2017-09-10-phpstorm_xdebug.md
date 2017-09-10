---
layout: post
title: "PhpStorm + Xdebugでリモートデスクトップ"
date: 2017-09-10 20:17:12
image: '/assets/img/posts/Etc/'
description:
tags:
- PhpStorm
- xdebug
categories:
- ETC
sitemap :
  changefreq : daily
  priority : 1.0
---

# PhpStorm + Xdebugでリモートデスクトップ

## Xdebug?
* デバック及びプロファイリング機能を提供するPHP拡張モデュール
* PECLを用いてインストール可能

<br><br>

## 1. Xdebugをインストール（CentOS）

### php-devel、php-pearをインストール
    $ yum install php-devel
    $ yum install php-pear

<br>

### gcc、gcc-c++、autoconf、automakeをインストール
    $ yum install gcc gcc-c++ autoconf automake

<br>

### Xdebugをインストール
    $ pecl install Xdebug

※エラーになる場合

	// yum --enablerepo=remi-phpバージョン install php-devel php-pear
	
	$ yum --enablerepo=remi-php56 install php-devel php-pear
	
<br>

### /etc/php.iniを修正

    $ vi /etc/php.ini

↓以下を追加

```/etc/php.ini
[xdebug]
zend_extension="/usr/lib64/php/modules/xdebug.so"
xdebug.default_enable = 1
xdebug.remote_enable = 1
xdebug.remote_port = 9000
xdebug.remote_handler = dbgp
xdebug.remote_autostart = 1
xdebug.profiler_output_dir = "/tmp"
xdebug.max_nesting_level = 1000
xdebug.idekey = "PHPSTORM" //PhpSTORMで設定したideKey
xdebug.remote_host=xxx.xxx.xxx.xxx
```

<br>

### Apacheをリスタート

    $ service httpd restart


<br><br>

## 2. PhpStormでの設定

### リモートホストの設定

1. Remote Hostを表示
    > [ Tools > Deployment > Browse Remote Host ]をクリックする

2. サーバーを登録
    > [ Tools > Deployment > Configuration... ]　を開く
    ![](/assets/img/posts/Etc/Deployment1.png)
    `[test SFTP connection]` をクリックし、成功することを確認

    ![](/assets/img/posts/Etc/Deployment2.png)

<br>


### PHPリモートデバッグの設定

>  [ Run > Edit Configurations... ]　を開く

![](/assets/img/posts/Etc/Run_Debug_Configurations.png)

1. PHP Remote Debugをクリック  
2. 名前、サーバーIPアドレス、Ide Key(※php.iniで設定したKey)  
などを設定する

<br>
<br>

これでPhpStorm + Xdebugでリモートデスクトップ環境構築完了！
