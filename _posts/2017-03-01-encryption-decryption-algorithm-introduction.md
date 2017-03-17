---
layout: post
title:  "[Encryption/Decryption] - Introduction"
date:   2017-03-01 12:07:54 +0800
categories: jekyll update
---

* 加密解密的基本用途：        
  1.身份认证      
  2.确定谁可以接收    

* 1.加解密  

* 2.签名  

* 3.证书  

### openssl  

  1.md5                               
                                
  2.sha                               
                                
  3.rsa                               
                                
  命令：                             
    openssl rsautl -verify -in 1 -inkey rsa_pubkey_for_server.pem -out out.txt -pubin  
                                
    openssl rsa -in rsa_pivkey_for_fctdev---.pem -pubout -out pub.txt

  4.base64                                
                                
  5.openssl如何支持multi-thread                               
                                
                                
### 用法                           
  1. 信息内容加密                               
     接收者的公钥: 用于加密                             
     接收者的私钥: 用于解密                             
      --------  验证接收者(保证数据私密性)                                
                                
  2. 数字签名                             
     发送者的私钥: 用于加密                             
     发送者的公钥: 用于解密                             
       --------  验证发送者(保证不可抵赖性、数据完整性)                             
                                
  3.证书                                
                                
                                
                                




