---
title: "Xor Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.Xor"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "exclusive OR operator"
  - "logical exclusion"
  - "operators [Visual Basic], exclusive or"
  - "exclusion operator"
  - "operators [Visual Basic], bitwise"
  - "bitwise operators, XOR operator"
  - "Xor operator [Visual Basic]"
  - "Xor keyword"
  - "bitwise comparison"
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Xor Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

2 つのブール \(`Boolean`\) 式の排他的論理和を求めます。または、2 つの数式のビットごとの排他を求めます。  
  
## 構文  
  
```  
  
result = expression1 Xor expression2  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  任意のブール変数または数値変数を指定します。  ブール式の比較の場合、`result` は 2 つの `Boolean` 値の排他的論理和です。  ビットごとの演算の場合、`result` は 2 つの数式のビットパターンの、ビットごとの排他的論理和を表す数値です。  
  
 `expression1`  
 必ず指定します。  任意のブール型 \(`Boolean`\) または数式を指定します。  
  
 `expression2`  
 必ず指定します。  任意のブール型 \(`Boolean`\) または数式を指定します。  
  
## 解説  
 ブール値の比較の場合、`result` が `True` になるのは、`expression1` と `expression2` の一方だけが `True` と評価される場合だけです。  つまり、`expression1` と `expression2` が反対の `Boolean` 値に評価される場合だけということです。  次の表は、2 つの式の値と演算結果 `result` の値の対応を示しています。  
  
|`expression1` の値|`expression2` の値|`result` の値|  
|----------------------|----------------------|-----------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  ブール式の比較の場合、`Xor` 演算子は必ず両方の式を評価します。これはプロシージャ呼び出しを作成する場合も同じです。  `Xor` の結果は必ず 2 つのオペランドによって決まるため、この演算子に相当するショートサーキットはありません。  *ショートサーキット*論理演算子については、「[AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)」と「[OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md)」を参照してください。  
  
 ビットごとの演算の場合、`Xor` 演算子は、2 つの数式内の対応するビットどうしの、ビット単位の比較を行います。次の表に従って、`result` 内の対応するビットがセットされます。  
  
|`expression1` のビット|`expression2` のビット|`result` 内のビット|  
|------------------------|------------------------|--------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  論理\/ビット処理演算子は他の算術演算子や関係演算子より優先順位が低いため、ビットごとの演算は、正確に実行されるようにかっこで囲む必要があります。  
  
 たとえば、5 `Xor` 3 の結果は 6 になります。  その理由は、5 と 3 を対応する 2 進数 \(それぞれ 101 と 011\) に変換してみるとわかります。  前出の表によると、101 Xor 011 の結果は 110 です。これは、10 進数の 6 を 2 進数で表した値です。  
  
## データ型  
 オペランドの一方が `Boolean` 式で、もう一方が数式の場合、Visual Basic は `Boolean` 式を数値 \(`True` は \-1、`False` は 0\) に変換してから、ビットごとの演算を実行します。  
  
 `Boolean` 式の比較の場合、結果のデータ型は `Boolean` になります。  ビットごとの比較の場合、結果のデータ型は `expression1` と `expression2` のデータ型に対して適切な数値型になります。  「[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「リレーショナルおよびビットごとの比較」の表を参照してください。  
  
## オーバーロード  
 `Xor` 演算子は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `Xor` 演算子を使って 2 つの式の排他的論理和を求める例を次に示します。  結果は、2 つの式のどちらか一方が `True` かどうかを表す `Boolean` 値です。  
  
 [!CODE [VbVbalrOperators#40](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#40)]  
  
 前の例では、`False`、`True`、`False` の結果を順に生成します。  
  
## 使用例  
 `Xor` 演算子を使って 2 つの数式のビットごとの排他的論理和を求める例を次に示します。  オペランド内の、対応するビットのどちらか一方だけが 1 にセットされている場合は、結果パターンにビットがセットされます。  
  
 [!CODE [VbVbalrOperators#41](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#41)]  
  
 前の例では、2、12、14 の結果を順に生成します。  
  
## 参照  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)