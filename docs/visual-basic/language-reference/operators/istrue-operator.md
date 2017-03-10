---
title: "IsTrue Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.istrue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "IsTrue operator"
  - "OrElse operator [Visual Basic]"
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# IsTrue Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

式が `True` かどうかを調べます。  
  
 `IsTrue` をコードの中で明示的に呼び出すことはできませんが、Visual Basic コンパイラはこれを使用して `OrElse` 句からコードを生成します。  クラスまたは構造体を定義し、`OrElse` 句でその型の変数を使用する場合、そのクラスまたは構造体で `IsTrue` を定義する必要があります。  
  
 コンパイラは `IsTrue` および `IsFalse` 演算子を *一致したペア*と見なします。  つまり、一方を定義したら、もう一方も定義する必要があります。  
  
## IsTrue のコンパイラによる使用  
 クラスまたは構造体を定義した場合、その型の変数を `For`、`If`、`Else` `If`、または `While` ステートメントまたは `When` 句で使用できます。  この場合、コンパイラは条件をテストするために、この型を `Boolean` 値に変換する演算子が必要です。  適切な演算子は次の順序で検索されます。  
  
1.  クラスまたは構造体から `Boolean` への拡大変換演算子  
  
2.  クラスまたは構造体から `Boolean?` への拡大変換演算子  
  
3.  クラスまたは構造体上の `IsTrue` 演算子  
  
4.  `Boolean` から `Boolean?` への変換が含まれない `Boolean?` への縮小変換  
  
5.  クラスまたは構造体から `Boolean` への縮小変換演算子  
  
 `Boolean` への変換、または `IsTrue` 演算子を定義していない場合、コンパイラはエラーを返します。  
  
> [!NOTE]
>  `IsTrue` は *オーバーロード* できます。つまり、オペランドがクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次のコード例では、`IsFalse` および `IsTrue` 演算子の定義を含む構造体の骨組みを定義します。  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/istrue-operator_1.vb)]  
  
## 参照  
 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md)