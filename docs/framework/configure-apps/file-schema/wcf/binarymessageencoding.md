---
title: "&lt;binaryMessageEncoding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;binaryMessageEncoding&gt;
ネットワーク上で Windows Communication Foundation \(WCF\) メッセージをバイナリにエンコードするバイナリ メッセージ エンコーダーを定義します。  
  
## 構文  
  
```  
  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10” />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|maxReadPoolSize|新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。  プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。  既定値は 64 です。|  
|maxSessionSize|エンコーディングに使用されるバッファーのサイズをバイト単位で設定する正の整数。  バッファーが大きくなると、作業セットのサイズの増加時に、エンコーディングの速度が高まります。  既定値は 2048 です。|  
|maxWritePoolSize|新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。  プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。  既定値は 16 です。|  
|messageVersion|使用または予想される SOAP メッセージおよび WS\-Addressing のバージョンを指定します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。  この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<binding\>](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## 解説  
 エンコーディングは、メッセージをバイト シーケンスに変換するプロセスです。  デコードは、その逆のプロセスです。  WCF \(Windows Communication Foundation\) には、SOAP メッセージのエンコードとして、テキスト、バイナリ、および MTOM \(Message Transmission Optimization Mechanism\) の 3 種類があります。  
  
 `binaryMessageEncoding` 要素は、XML 用の .NET バイナリ形式を指定します。この要素には、使用する文字エンコーディング、SOAP バージョン、および WS\-Addressing バージョンを指定するオプションがあります。  バイナリ メッセージ エンコーダーは、ネットワーク上で Windows Communication Foundation \(WCF\) メッセージをバイナリにエンコードします。  このエンコーディングによりメッセージ転送は非常に高速になりますが、WS\-\* 標準に基づいた相互運用性は失われます。  
  
## 使用例  
  
```  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>   
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>   
 [メッセージ エンコーディング](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)   
 [メッセージ エンコーダーを選択する](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)