---
title: "How to: Sort An Array in Visual Basic | Microsoft Docs"
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
  - "Array.Sort"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arrays [Visual Basic], sorting"
  - "examples [Visual Basic], arrays"
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Sort An Array in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

次に示すのは、`zooAnimals` という名前の `String` オブジェクトの配列を宣言し、値を代入してから、アルファベット順に並べ替える例です。  
  
## 使用例  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   Mscorlib.dll および <xref:System> 名前空間にアクセスします。  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   空の配列である場合 \(<xref:System.ArgumentNullException> クラス\)。  
  
-   多次元の配列である場合 \(<xref:System.RankException> クラス\)。  
  
-   配列の 1 つ以上の要素が <xref:System.IComparable> インターフェイスを実装していない場合 \(<xref:System.InvalidOperationException> クラス\)。  
  
## 参照  
 <xref:System.Array.Sort%2A?displayProperty=fullName>   
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)