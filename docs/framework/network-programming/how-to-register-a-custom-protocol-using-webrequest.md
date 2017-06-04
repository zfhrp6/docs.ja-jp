---
title: "方法: WebRequest を使用してカスタム プロトコルを登録する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 方法: WebRequest を使用してカスタム プロトコルを登録する
この例では、対応する classthat プロトコルを登録する方法を他の場所で定義されますが表示されます。  この例では、`CustomWebRequestCreator` ユーザーが実行されたオブジェクトに実装 `CustomWebRequest` のオブジェクトを返品 **\[作成\]** 方法です。  コード例は、注文プロトコルを実行する `CustomWebRequest` コードを書き込んだいます。  
  
## 使用例  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
 <xref:System.Net> の名前空間への参照。  
  
## 参照  
 [プラグ可能なプロトコルのプログラミング](../../../docs/framework/network-programming/programming-pluggable-protocols.md)