---
title: "OrElse Operator (Visual Basic) | Microsoft Docs"
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
  - "OrElse"
  - "vb.OrElse"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "short-circuiting"
  - "operators [Visual Basic], short-circuiting"
  - "operators [Visual Basic], disjunction"
  - "short-circuit evaluation"
  - "OrElse operator [Visual Basic]"
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# OrElse Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

2 つの式の包括的論理和を簡略的に求めます。  
  
## 構文  
  
```  
  
result = expression1 OrElse expression2  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  任意のブール型 \(`Boolean`\) の式を指定します。  
  
 `expression1`  
 必ず指定します。  任意のブール型 \(`Boolean`\) の式を指定します。  
  
 `expression2`  
 必ず指定します。  任意のブール型 \(`Boolean`\) の式を指定します。  
  
## 解説  
 コンパイルされたコードで、1 つの式の結果によってはもう 1 つの式の評価を省略できる場合、そこで使用される論理演算子を*ショートサーキット*と呼びます。  最初に評価される式の結果によって演算の最終結果が決まる場合は、もう 1 つの式によって最終結果が変わることはないため、その式を評価する必要はありません。  省略される側の式が複雑な場合や、プロシージャの呼び出しを含む場合は、ショートサーキットによってパフォーマンスを向上できます。  
  
 一方の式、または両方の式が `True` に評価される場合、`result` は `True` になります。  次の表は、2 つの式の値と演算結果 `result` の値の対応を示しています。  
  
|`expression1` の値|`expression2` の値|`result` の値|  
|----------------------|----------------------|-----------------|  
|`True`|\(評価しない\)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## データ型  
 `OrElse` 演算子は、[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) のみに対して定義されます。  Visual Basic は、各オペランドを必要に応じて `Boolean` に変換し、完全な `Boolean` に対して演算を実行します。  結果を数値型に割り当てる場合、Visual Basic は結果を `Boolean` からこのデータ型に変換します。  これにより、予期しない動作が起きることがあります。  たとえば、`5 OrElse 12` の結果を整数 \(`Integer`\) に変換すると、`–1` になります。  
  
## オーバーロード  
 [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) と [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  `Or` 演算子と `IsTrue` 演算子のオーバーロードは、`OrElse` 演算子の動作に影響を与えます。  コードが、`Or` および `IsTrue` をオーバーロードするクラスや構造体で `OrElse` を使用している場合は、再定義された後の動作を必ず理解するようにしてください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `OrElse` 演算子を使って 2 つの式の論理和を求める例を次に示します。  結果は、2 つの式のどちらかが真かどうかを表すブール値です。  最初の式が真 \(`True`\) の場合、2 番目の式は評価されません。  
  
 [!CODE [VbVbalrOperators#37](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#37)]  
  
 先の例では、`True`、`True`、`False` という結果がそれぞれ生成されます。  `firstCheck` の計算では、最初の式が `True` であるため、2 番目の式は評価されません。  一方、`secondCheck` の計算では、2 番目の式も評価されます。  
  
## 使用例  
 2 つのプロシージャ呼び出しを含む `If`...`Then` ステートメントの例を次に示します。  最初の呼び出しが `True` を返した場合、2 番目のプロシージャは呼び出されません。  このため、2 番目のプロシージャがコードのこの部分で必ず処理されるべき重要なタスクを実行する場合に、予期しない結果が返される可能性があります。  
  
 [!CODE [VbVbalrOperators#38](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#38)]  
  
## 参照  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md)   
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)