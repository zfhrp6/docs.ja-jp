---
title: "Is Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.is"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comparison operators"
  - "equivalent objects"
  - "TypeOf...Is expression"
  - "Is operator [Visual Basic]"
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Is Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つのオブジェクト変数を比較します。  
  
## 構文  
  
```  
  
result = object1 Is object2  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  任意のブール型 \(`Boolean`\) の値を指定します。  
  
 `object1`  
 必ず指定します。  任意のオブジェクト名を指定します。  
  
 `object2`  
 必ず指定します。  任意のオブジェクト名を指定します。  
  
## 解説  
 `Is` 演算子は、2 つのオブジェクト参照が同じオブジェクトを参照しているかどうかを判定します。  ただし、値の比較は行われません。  `object1` と `object2` の両方がまったく同じオブジェクト インスタンスを参照している場合、`result` は `True` になります。それ以外の場合は、`result` は `False` です。  
  
 `Is` を `TypeOf` キーワードと共に使用して `TypeOf`...`Is` 式を作成し、オブジェクト変数がデータ型と互換性があるかどうかをテストできます。  
  
> [!NOTE]
>  `Is` キーワードは、[Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) でも使用されます。  
  
## 使用例  
 次の例では、`Is` 演算子を使用して、1 組のオブジェクト参照を比較します。  結果は、2 つのオブジェクトが同じかどうかを示す `Boolean` 値に割り当てられます。  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/is-operator_1.vb)]  
  
 この例で示すように、`Is` 演算子は、事前バインディングされたオブジェクトと遅延バインディングされたオブジェクトの両方をテストするのに使用できます。  
  
## 参照  
 [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)