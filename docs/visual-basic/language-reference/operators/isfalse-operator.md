---
title: "IsFalse Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.isfalse"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AndAlso operator"
  - "IsFalse operator"
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# IsFalse Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

式が `False` かどうかを調べます。  
  
 `IsFalse` をコードの中で明示的に呼び出すことはできませんが、Visual Basic コンパイラはこれを使用して `AndAlso` 句からコードを生成します。  クラスまたは構造体を定義して、その型の変数を `AndAlso` 句で使用する場合は、そのクラスまたは構造体に対して `IsFalse` を定義する必要があります。  
  
 コンパイラは `IsFalse` 演算子と `IsTrue` 演算子を*一致したペア*と見なします。  つまり、一方を定義したら、もう一方も定義する必要があります。  
  
> [!NOTE]
>  `IsFalse` 演算子は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次のコード例では、`IsFalse` および `IsTrue` 演算子の定義を含む構造体の骨組みを定義します。  
  
 [!CODE [VbVbalrOperators#28](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#28)]  
  
## 参照  
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)