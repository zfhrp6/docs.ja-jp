---
title: "Array declared as for loop control variable cannot be declared with an initial size | Microsoft Docs"
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
  - "vbc32039"
  - "bc32039"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32039"
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Array declared as for loop control variable cannot be declared with an initial size
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`For Each` ループが配列をその *element* 反復変数として使用していますが、その配列が初期化されています。  
  
 このエラーが発生する様子を次のステートメントに示します。  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 1 つ目の `For Each` ステートメントは、`arrayList` の要素に正しい方法でアクセスしています。  2 つ目の `For Each` ステートメントはエラーを発生させます。  
  
 **Error ID:** BC32039  
  
### このエラーを解決するには  
  
-   *element* 反復変数の宣言から初期化の処理を削除します。  
  
## 参照  
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)