---
title: "Not Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Not"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Boolean expressions, negating"
  - "operators [Visual Basic], bitwise"
  - "negation operator"
  - "inverse bit values in variables"
  - "bitwise operators, NOT operator"
  - "bitwise comparison"
  - "Not operator [Visual Basic]"
  - "logical negation"
  - "operators [Visual Basic], negation"
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Not Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つのブール式の論理否定を求めます。また、2 つの数式のビットごとの否定を求めます。  
  
## 構文  
  
```  
  
result = Not expression  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  任意のブール型 \(`Boolean`\) または数式を指定します。  
  
 `expression`  
 必ず指定します。  任意のブール型 \(`Boolean`\) または数式を指定します。  
  
## 解説  
 `Boolean` 式の場合、次の表は、2 つの式の値と演算結果 `result` の値の対応を示しています。  
  
|`expression` の値|`result` の値|  
|---------------------|-----------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 数値の場合、`Not` 演算子は、数式に対してビット単位の反転も行います。次に示す真理値表に従って、演算結果 `result` の対応するビットがセットされます。  
  
|`expression` のビット|`result` 内のビット|  
|-----------------------|--------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  論理\/ビット処理演算子は他の算術演算子や関係演算子より優先順位が低いため、ビットごとの演算は、正確に実行されるようにかっこで囲む必要があります。  
  
## データ型  
 ブール値の否定では、結果のデータ型は `Boolean` です。  ビットごとの否定では、結果のデータ型は `expression` と同じです。  ただし、式が `Decimal` の場合、結果は `Long` になります。  
  
## オーバーロード  
 `Not` は *オーバーロード* できます。つまり、オペランドがクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次の例では、`Not` 演算子を使って 2 つの `Boolean` 式の論理否定を求めます。  結果は、式の値を反転させた `Boolean` 値です。  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 前の例では、`False` と `True` の結果を順に生成します。  
  
## 使用例  
 `Not` 演算子を使って、数式のビットごとの論理否定を求める例を次に示します。  結果パターンのビットは、符号ビットを含めて、オペランド パターンで対応するビットを反転した値にセットされます。  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 前の例では、–11、–9、–7 の結果を順に生成します。  
  
## 参照  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)