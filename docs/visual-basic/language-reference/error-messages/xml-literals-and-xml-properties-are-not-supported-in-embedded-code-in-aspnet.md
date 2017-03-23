---
title: "XML literals and XML properties are not supported in embedded code within ASP.NET | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31200"
  - "bc31200"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31200"
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# XML literals and XML properties are not supported in embedded code within ASP.NET
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません。XML 機能を使用するには、コードを分離コードに移動してください。  
  
 XML リテラルまたは XML 軸プロパティが ASP.NET ファイルの埋め込みコード \(`<%= =>`\) の中で定義されています。  
  
 **エラー ID:** BC31200  
  
### このエラーを解決するには  
  
-   XML リテラルまたは XML 軸プロパティが含まれているコードを ASP.NET 分離コード ファイルに移動します。  
  
## 参照  
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)