---
layout: post
title: "CentOS6系にepel-releseをインストールする。"
date: 2017-08-23 02:23:51
image: '/assets/img/'
description: 'epel-releseをインストール'
tags:
- Linux
- CentOS
categories:
- Linux
---

# 確認

    $ yum repolist

    ... (省略)
    repo id                               repo name                                        status
    base                                  CentOS-6 - Base                                  6,575
    extras                                CentOS-6 - Extras                                   35
    updates                               CentOS-6 - Updates                                 298
    repolist: 6,908
    
>

    $ rpm -qa epel-release
    $ yum list epel-release

    ... (省略)
    Available Packages
    epel-release.noarch                                6-8                                 extras


# epel インストール

    $ yum install epel-release

    ... (省略)
    =============================================================================================
    Package                   Arch                Version             Repository           Size
    =============================================================================================
    Installing:
    epel-release              noarch              6-8                 extras               14 k

    Transaction Summary
    =============================================================================================
    Install       1 Package(s)

    Total download size: 14 k
    Installed size: 22 k
    Is this ok [y/N]: y

	
    ... (省略)
    Installed:
    epel-release.noarch 0:6-8                                                                  

    Complete!

[※ epel-releaseで検索し、最新バージョンを確認する。](http://dl.fedoraproject.org/pub/epel/6/x86_64/)


# 確認

    $ rpm -qa epel-release
    epel-release-6-8.noarch

>

    $ yum list installed epel-release

    ... (省略)
    Installed Packages
    epel-release.noarch                                6-8                                @extras

>

    $ yum repolist
    
    ... (省略)
    repo id                 repo name                                                      status
    base                    CentOS-6 - Base                                                 6,575
    epel                    Extra Packages for Enterprise Linux 6 - x86_64                 11,768
    extras                  CentOS-6 - Extras                                                  35
    updates                 CentOS-6 - Updates                                                298
    repolist: 18,676


<br><br>