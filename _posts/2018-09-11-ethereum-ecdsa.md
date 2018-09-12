---
layout: post
title: 이더리움에서의 전자서명
tags: [ethereum, public key, digital signature algorithm, ]
excerpt_separator: <!--more-->
---

이더리움은 타원곡선암호화(ECC: Elliptic Curve Cryptography)방식을 통해(비트코인과 마찬가지로 타원곡선의 Domain Parameter로 secp256k1을 사용) 계정의 생성/관리 및 트랜잭션을 검증합니다. (타원곡선암호화 방식을 따른 전자서명 알고리즘은 ECDSA(Elliptic Curve Digital Signature Algorithm)라고도 부릅니다.)

이더리움에서는 이 ECC 방식을 통해 계정의 개인키(Private Key)와 공개키(Public Key)를 생성합니다. 이때, 생성된 공개키키의 Hash 값의 마지막 20 bytes가 바로 계정 Address가 됩니다. \[1]

계정과 관련하여 KeyStore파일(UTC) 생성 및 암호화/복호화 원리는 [이 글](https://medium.com/hexlant/%EC%9D%B4%EB%8D%94%EB%A6%AC%EC%9B%80-keystore-%ED%8C%8C%EC%9D%BC-utc-%EC%83%9D%EC%84%B1-%EB%B0%8F-%EC%95%94%ED%98%B8%ED%99%94-%EB%B3%B5%ED%98%B8%ED%99%94-%EC%9B%90%EB%A6%AC-1-2-d417cb605bf) 에서 참고

일반적으로 디지털 서명을 통해 데이터가 누구에게서 보내진 것인지를 검증하는 과정은 다음과 같습니다.
1) Alice가 보내고자 하는 메시지를 해시하여 자신의 개인키(Private key)로 서명(암호화)하고 이를 기존 데이터와 함께 Bob에게 전송 (메시지 + 메시지희 해시를 서명한 값)
2) Bob은 이를 받아 서명한 값을 Alice의 공개키(Public key)로 복호화하여 나온 해시값을 메시지의 해시값과 비교


이러한 과정에서 Alice의 서명을 검증하려면 상대방은 반드시 Alice의 공개키를 알고 있어야 합니다. 그런데, 이더리움의 트랜잭션의 정보들을 보면 보내는 사람의 공개키가 어디에도 없습니다. 그러면 대체 어떻게 이더리움에선 트랜잭션의 서명을 검증하는 걸까요?

이더리움에서 사용한 타원곡선암호화(ECC)방식(혹은 ECDSA)이 이를 가능하게 합니다. 해당 알고리즘에서는 보내는 메시지와 그에 대한 서명값만 있다면 이를 통해 공개키를 복원해낼 수 있습니다. 


\[1]: http://ethdocs.org/en/latest/account-management.html?highlight=address#keyfiles
