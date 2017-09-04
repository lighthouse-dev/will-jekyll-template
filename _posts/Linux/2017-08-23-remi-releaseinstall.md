---
layout: post
title: "CentOS6系にremiレポジトリを追加する"
date: 2017-08-23 03:00:22
image: '/assets/img/'
description: ""
tags:
- CentOS
categories:
- Linux
sitemap :
  changefreq : daily
  priority : 1.0
---

# 事前作業
* remi-releaseは、epel-releaseに依存性(dependency)がある。
* [CentOS6系にepel-releseをインストールする。](https://lighthouse-dev.github.io//epel-releaseInstall/)

<br>

# 確認

    $ rpm -qa | grep remi-release
    $ rpm -qa | grep epel-release
    epel-release-6-8.noarch

<br>

# remi-releaseをインストール

    $ yum install http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
    
    ... (省略)
    ===========================================================================================
    Package              Arch           Version                 Repository               Size
    ===========================================================================================
    Installing:
    remi-release         noarch         6.8-1.el6.remi          /remi-release-6         6.3 k

    Transaction Summary
    ===========================================================================================
    Install       1 Package(s)

    Total size: 6.3 k
    Installed size: 6.3 k
    Is this ok [y/N]: y


    $ ... (省略)
    Installed:
    remi-release.noarch 0:6.8-1.el6.remi                                                     

    Complete!

<br>

# 確認

    $ rpm -qa | grep remi-release
    remi-release-6.8-1.el6.remi.noarch



    $ yum list remi-release
    
    ... (省略)
    Installed Packages
    remi-release.noarch                     6.8-1.el6.remi                     @/remi-release-6



    $ yum repolist | grep remi
    * remi-safe: mirror.innosol.asia
    remi-safe                  Safe Remi's RPM repository for Enterprise Linu    881

<br><br>