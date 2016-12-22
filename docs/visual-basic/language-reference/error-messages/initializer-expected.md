---
title: "Initializer expected | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
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
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Initializer expected
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

次の例では、初期化リストが空のオブジェクト初期化子を使用して、クラスのインスタンスを宣言しています。  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 次の例のように、初期化子リスト内で少なくとも 1 つのフィールドまたはプロパティが初期化されている必要があります。  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Error ID:** BC30996  
  
### このエラーを解決するには  
  
1.  初期化子内で少なくとも 1 つのフィールドまたはプロパティを初期化します。オブジェクト初期化子は使用しません。  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)