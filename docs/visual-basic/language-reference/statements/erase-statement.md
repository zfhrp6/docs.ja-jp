---
title: "Erase Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Erase"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Erase keyword"
  - "Erase statement"
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Erase Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

配列変数と、その配列変数の要素で使用されていたメモリを解放します。  
  
## 構文  
  
```  
Erase arraylist  
```  
  
## 指定項目  
 `arraylist`  
 必ず指定します。  消去する配列変数のリストを指定します。  複数の変数を指定するときは、コンマ \(,\) で区切ります。  
  
## 解説  
 `Erase` ステートメントを使用できるのは、プロシージャ レベルだけです。  つまり、プロシージャの中では配列を解放できますが、クラス レベルやモジュール レベルでは解放できません。  
  
 `Erase` ステートメントは、各配列変数に `Nothing` 値を割り当てるのと同じ結果になります。  
  
## 使用例  
 次に示す例では、`Erase` ステートメントを使って 2 つの配列を消去し、使用していたメモリを解放しています \(それぞれ、記憶要素が 1,000 と 100\)。  その後、`ReDim` ステートメントで 3 次元配列に新しい配列インスタンスを割り当てています。  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/erase-statement_1.vb)]  
  
## 参照  
 [Nothing](../../../visual-basic/language-reference/nothing.md)   
 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)