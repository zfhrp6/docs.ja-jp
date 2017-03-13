---
title: "IsFalse Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.isfalse"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AndAlso operator"
  - "IsFalse operator"
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# IsFalse Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

式が `False` かどうかを調べます。  
  
 `IsFalse` をコードの中で明示的に呼び出すことはできませんが、Visual Basic コンパイラはこれを使用して `AndAlso` 句からコードを生成します。  クラスまたは構造体を定義して、その型の変数を `AndAlso` 句で使用する場合は、そのクラスまたは構造体に対して `IsFalse` を定義する必要があります。  
  
 コンパイラは `IsFalse` 演算子と `IsTrue` 演算子を*一致したペア*と見なします。  つまり、一方を定義したら、もう一方も定義する必要があります。  
  
> [!NOTE]
>  `IsFalse` 演算子は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次のコード例では、`IsFalse` および `IsTrue` 演算子の定義を含む構造体の骨組みを定義します。  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## 参照  
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)