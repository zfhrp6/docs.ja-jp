---
title: ".NET Framework 型の文字列への変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# .NET Framework 型の文字列への変換
.NET Framework 型を文字列に変換するには、**ToString** メソッドを使用します。  **ToString** メソッドは、渡された型の文字列表現を返します。  XML スキーマ \(XSD\) 仕様に対応する形式で文字列を返す .NET Framework 型を、次の表に示します。  
  
|.NET Framework 型|返される文字列型|  
|----------------------|--------------|  
|Boolean|"true"、"false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"\-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"\-INF"|  
|DateTime|形式は、yyyy\-MM\-ddTHH:mm:sszzzzzz およびそのサブセットです。|  
|Timespan|PnYnMnTnHnMnS の形式。たとえば、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。|  
  
## 参照  
 [XML データ型の変換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)   
 [文字列の .NET Framework データ型への変換](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)