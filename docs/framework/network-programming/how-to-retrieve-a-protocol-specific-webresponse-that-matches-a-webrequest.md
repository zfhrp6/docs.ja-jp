---
title: "方法: WebRequest に一致するプロトコル固有の WebResponse を取得する | Microsoft Docs"
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
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 方法: WebRequest に一致するプロトコル固有の WebResponse を取得する
この例で WebRequest に一致するプロトコル対応する WebResponse を取得する方法を示します。  
  
## 使用例  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   **\[System.Net\]** の名前空間への参照。  
  
## 参照  
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)