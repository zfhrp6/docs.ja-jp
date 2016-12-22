---
title: "IsNot Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.isnot"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "IsNot operator"
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# IsNot Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

2 つのオブジェクト変数を比較します。  
  
## 構文  
  
```  
  
result = object1 IsNot object2  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  `Boolean` 値。  
  
 `object1`  
 必ず指定します。  任意の `Object` 変数または式です。  
  
 `object2`  
 必ず指定します。  任意の `Object` 変数または式です。  
  
## 解説  
 `IsNot`演算子は、2 つのオブジェクト参照が別のオブジェクトを参照しているかどうかを判定します。  ただし、値の比較は行われません。  `object1` と `object2` の両方がまったく同じオブジェクト インスタンスを参照している場合、`result` は `False` になります。それ以外の場合は、`result` は `True` です。  
  
 `IsNot` は `Is` 演算子の逆の働きをします。  `IsNot` の利点は、`Not` と `Is` を組み合わせて記述し、コードが読みづらくなるのを防げることです。  
  
 `Is` と `IsNot` 演算子を使用して、事前バインディング オブジェクトと遅延バインディング オブジェクトの両方をテストできます。  
  
> [!NOTE]
>  `TypeOf` 演算子から返される式を比較するために `IsNot` 演算子を使用することはできません。  代わりに、`Not` 演算子と `Is` 演算子を使用する必要があります。  
  
## 使用例  
 次のコード例では、`Is` 演算子と `IsNot` 演算子の両方を使用して、同じ比較を実行します。  
  
 [!CODE [VbVbalrOperators#29](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#29)]  
  
## 参照  
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [How to: Test Whether Two Objects Are the Same](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)