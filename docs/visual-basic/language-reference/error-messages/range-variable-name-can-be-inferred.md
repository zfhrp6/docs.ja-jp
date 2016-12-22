---
title: "Range variable name can be inferred only from a simple or qualified name with no arguments | Microsoft Docs"
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
  - "vbc36599"
  - "bc36599"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36599"
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Range variable name can be inferred only from a simple or qualified name with no arguments
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

1 つ以上の引数を受け取るプログラミング要素が LINQ クエリに含まれています。  コンパイラは、このプログラミング要素から範囲変数を推論できません。  
  
 **Error ID:** BC36599  
  
### このエラーを解決するには  
  
1.  次のコードに示すように、プログラミング要素に明示的な変数名を指定します。  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias = SampleFunction(var1), var1  
```  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)