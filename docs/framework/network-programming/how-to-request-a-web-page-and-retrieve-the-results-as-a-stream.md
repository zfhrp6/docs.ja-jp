---
title: "方法: Web ページを要求し、ストリームとして結果を取得する | Microsoft Docs"
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
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 方法: Web ページを要求し、ストリームとして結果を取得する
この例に Web ページを要求しストリームの結果を取得する方法を示します。  
  
## 使用例  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   <xref:System.IO> 名前空間および <xref:System.Net> 名前空間への参照。  
  
## 参照  
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)