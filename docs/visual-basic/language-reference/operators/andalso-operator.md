---
title: "AndAlso Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AndAlso"
  - "AndAlso"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "short-circuiting"
  - "AndAlso operator"
  - "operators [Visual Basic], short-circuiting"
  - "operators [Visual Basic], conjunction"
  - "short-circuit evaluation"
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# AndAlso Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つの式の論理積を簡略的に求めます。  
  
## 構文  
  
```  
  
result = expression1 AndAlso expression2  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`result`|必ず指定します。  任意のブール型 \(`Boolean`\) の式を指定します。  結果は、2 つの式の比較結果を表すブール値になります。|  
|`expression1`|必ず指定します。  任意のブール型 \(`Boolean`\) の式を指定します。|  
|`expression2`|必ず指定します。  任意のブール型 \(`Boolean`\) の式を指定します。|  
  
## 解説  
 コンパイルされたコードで、1 つの式の結果によってはもう 1 つの式の評価を省略できる場合、そこで使用される論理演算子を*ショートサーキット*と呼びます。  最初に評価される式の結果によって演算の最終結果が決まる場合は、もう 1 つの式によって最終結果が変わることはないため、その式を評価する必要はありません。  省略される側の式が複雑な場合や、プロシージャの呼び出しを含む場合は、ショートサーキットによってパフォーマンスを向上できます。  
  
 両方の式の評価が `True` の場合、`result` は `True` になります。  次の表は、2 つの式の値と演算結果 `result` の値の対応を示しています。  
  
||||  
|-|-|-|  
|`expression1` の値|`expression2` の値|`result` の値|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|\(評価しない\)|`False`|  
  
## データ型  
 `AndAlso` 演算子は、[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) のみに対して定義されます。  Visual Basic は、各オペランドを必要に応じて `Boolean` に変換し、完全な `Boolean` に対して演算を実行します。  結果を数値型に割り当てる場合、Visual Basic は結果を `Boolean` からこのデータ型に変換します。  これにより、予期しない動作が起きることがあります。  たとえば、`5 AndAlso 12` の結果は、`Integer` に変換すると `–1` になります。  
  
## オーバーロード  
 [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) と [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) は*オーバーロード*できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  `And` および `IsFalse` 演算子をオーバーロードすると、`AndAlso` 演算子の動作に影響します。  `And` および `IsFalse` をオーバーロードしているクラスまたは構造体で `AndAlso` を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `AndAlso` 演算子を使って 2 つの式の論理積を求める例を次に示します。  結果は、結合された式全体が真かどうかを表すブール値です。  最初の式が `False` の場合、2 番目の式は評価されません。  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_1.vb)]  
  
 前の例では、`True`、`False`、`False` の結果を順に生成します。  `secondCheck` の計算では、最初の式が `False` であるため、2 番目の式は評価されません。  しかし、`thirdCheck` の計算では、2 番目の式が評価されます。  
  
## 使用例  
 次の例では、配列の要素の中から指定された値を検索する `Function` プロシージャを示します。  配列が空の場合、また、配列の長さが限度を超えている場合、`While` ステートメントは配列の要素を検索値に対してテストしません。  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_2.vb)]  
  
## 参照  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [And Operator](../../../visual-basic/language-reference/operators/and-operator.md)   
 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)