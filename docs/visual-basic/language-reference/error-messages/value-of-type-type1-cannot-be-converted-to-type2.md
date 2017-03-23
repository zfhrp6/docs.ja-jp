---
title: "Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31194"
  - "bc31194"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31194"
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

型 'type1' の値を 'type2' に変換できません。'\<parentElement\>' の最初の要素の文字列値は、'Value' プロパティを使用して取得できます。  
  
 XML リテラルを指定の型に暗黙的にキャストしようとしました。  XML リテラルを指定の型に暗黙的にキャストすることはできません。  
  
 **エラー ID:** BC31194  
  
### このエラーを解決するには  
  
-   XML リテラルの `Value` プロパティを使用して、その値を `String` として参照します。  別の型変換関数である `CType` 関数、または <xref:System.Convert> クラスを使用して、値を指定の型にキャストします。  
  
## 参照  
 <xref:System.Convert>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)