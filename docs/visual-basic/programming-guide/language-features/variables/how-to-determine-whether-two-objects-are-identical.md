---
title: "How to: Determine Whether Two Objects Are Identical (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "testing, objects"
  - "objects [Visual Basic], comparing"
  - "object variables, determining identity"
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Determine Whether Two Objects Are Identical (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、ポインターが同一である場合、つまり双方の変数がメモリ内で同一のクラス インスタンスを指している場合は、2 つの変数参照は同一であると見なされます。  たとえば、Windows フォーム アプリケーションで、現在のインスタンス \(`Me`\) が `Form2` などの特定のインスタンスと同一であるかどうかを判別する際に比較することができます。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、ポインターを比較する 2 つの演算子が用意されています。  [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) では、オブジェクトが同じである場合 `True` が返されます。[IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) では、オブジェクトが異なる場合 `True` が返されます。  
  
## 2 つのオブジェクトが同じであるかどうかの確認  
  
#### 2 つのオブジェクトが同じであるかどうかを確認するには  
  
1.  `Boolean` 式を設定して 2 つのオブジェクトをテストします。  
  
2.  テストを実行する式では、2 つのオブジェクトにオペランドとして `Is` 演算子を使用します。  
  
     `Is` は、両方のオブジェクトが同じクラス インスタンスを指している場合 `True` を返します。  
  
## 2 つのオブジェクトが同一でないかどうかの確認  
 2 つのオブジェクトが同一でないかどうかを確認する場合があります。しかし、`If Not obj1 Is obj2` のように `Not` と `Is` を組み合わせて使用するのは大変面倒なことです。  このような場合に、`IsNot` 演算子を使用できます。  
  
#### 2 つのオブジェクトが同一でないかどうかを確認するには  
  
1.  `Boolean` 式を設定して 2 つのオブジェクトをテストします。  
  
2.  テストを実行する式では、2 つのオブジェクトにオペランドとして `IsNot` 演算子を使用します。  
  
     `IsNot` は、両方のオブジェクトが同じクラス インスタンスを指していない場合に `True` を返します。  
  
## 使用例  
 1 組の `Object` 変数が同じクラス インスタンスを指しているかどうかをテストする例を、次に示します。  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 前の例では、次の出力が表示されます。  
  
 `objA different from objB?  True`  
  
 `objA identical to objC?  True`  
  
## 参照  
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)