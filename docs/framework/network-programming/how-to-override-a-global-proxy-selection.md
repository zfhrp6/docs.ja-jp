---
title: "方法: グローバル プロキシの選択をオーバーライドする | Microsoft Docs"
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
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 方法: グローバル プロキシの選択をオーバーライドする
ポート 80 で `alternateproxy` というプロキシ サーバーとのグローバルなプロキシの選択を上書きこの例では、www.contoso.com に **\[WebRequest\]** を送信した示します。  
  
## 使用例  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   **\[System.Net\]** の名前空間への参照。  
  
## 参照  
 [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)   
 [プロキシを介したインターネットへのアクセス](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)