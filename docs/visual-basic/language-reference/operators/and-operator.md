---
title: "And Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.And"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operators [Visual Basic], bitwise"
  - "logical conjunction"
  - "bitwise AND operator [Visual Basic]"
  - "conjunction operator"
  - "And operator [Visual Basic]"
  - "bitwise operators, AND operator"
  - "operators [Visual Basic], conjunction"
  - "bitwise comparison"
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# And Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つのブール \(`Boolean`\) 式の論理積を求めます。または、2 つの数式のビットごとの積を求めます。  
  
## 構文  
  
```  
  
result = expression1 And expression2  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  任意のブール型 \(`Boolean`\) または数式を指定します。  ブール式の比較の場合、`result` は 2 つの `Boolean` 値の論理積になります。  ビットごとの演算の場合、`result` は 2 つの数式のビットパターンの、ビットごとの論理積を表す数値になります。  
  
 `expression1`  
 必ず指定します。  任意のブール型 \(`Boolean`\) または数式を指定します。  
  
 `expression2`  
 必ず指定します。  任意のブール型 \(`Boolean`\) または数式を指定します。  
  
## 解説  
 ブール値の比較の場合、`result` が `True` になるのは、`expression1` と `expression2` がどちらも `True` に評価される場合だけです。  次の表は、2 つの式の値と演算結果 `result` の値の対応を示しています。  
  
|`expression1` の値|`expression2` の値|`result` の値|  
|----------------------|----------------------|-----------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  ブール式の比較の場合、`And` 演算子は必ず両方の式を評価します。これは式がプロシージャ呼び出しを実行する場合も同じです。  [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) は*ショートサーキット*を実行します。つまり、`expression1` が `False` であれば、`expression2` は評価されません。  
  
 数値に対して使用された場合、`And` 演算子は、2 つの数式内で同じ位置にあるビットごとに比較を行います。次の表に従って、`result` に対応するビットがセットされます。  
  
|`expression1` のビット|`expression2` のビット|`result` 内のビット|  
|------------------------|------------------------|--------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  論理演算子やビット処理演算子は、他の算術演算子や関係演算子より優先順位が低いため、正しい結果を得るにはビットごとの演算をかっこで囲む必要があります。  
  
## データ型  
 オペランドの一方が `Boolean` 式で、もう一方が数式の場合、Visual Basic は `Boolean` 式を数値 \(`True` は \-1、`False` は 0\) に変換してから、ビットごとの演算を実行します。  
  
 ブール式どうしの比較の場合、結果のデータ型は `Boolean` になります。  ビットごとの比較の場合、結果のデータ型は `expression1` と `expression2` のデータ型に対して適切な数値型になります。  「[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「リレーショナルおよびビットごとの比較」の表を参照してください。  
  
> [!NOTE]
>  `And` 演算子は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `And` 演算子を使って 2 つの式の論理積を求める例を次に示します。  結果は、2 つの式の両方が `True` かどうかを表す `Boolean` 値です。  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 先の例では、`True`、`False` という結果がそれぞれ生成されます。  
  
## 使用例  
 `And` 演算子を使って、2 つの数式のビットごとの論理積を求める例を次に示します。  2 つのオペランドの対応するビットが両方とも 1 にセットされていれば、結果パターンにビットがセットされます。  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 先の例では 8、2、0 という結果がそれぞれ生成されます。  
  
## 参照  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)