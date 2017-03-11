---
title: "Initializer expected | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30996"
  - "bc30996"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30996"
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Initializer expected
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

次の例では、初期化リストが空のオブジェクト初期化子を使用して、クラスのインスタンスを宣言しています。  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 次の例のように、初期化子リスト内で少なくとも 1 つのフィールドまたはプロパティが初期化されている必要があります。  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Error ID:** BC30996  
  
### このエラーを解決するには  
  
1.  初期化子内で少なくとも 1 つのフィールドまたはプロパティを初期化します。オブジェクト初期化子は使用しません。  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)