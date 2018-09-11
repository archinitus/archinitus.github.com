---
layout: post
title: 이더리움에서의 전자서명
tags: [ethereum, public key, digital signature algorithm, ]
excerpt_separator: <!--more-->
---

이더리움은 계정 생성을 위해 타원곡선암호화(ECC: Elliptic Curve Cryptography)방식을 사용하며,
비트코인과 마찬가지로 타원곡선의 Domain Parameter로 secp256k1을 사용한다. 
이더리움에서 address는 public key의 Hash값의 마지막 20 bytes이다. \[1]: http://ethdocs.org/en/latest/account-management.html?highlight=address#keyfiles

[1]: http://ethdocs.org/en/latest/account-management.html?highlight=address#keyfiles
