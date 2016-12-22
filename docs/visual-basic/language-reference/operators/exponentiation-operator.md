---
title: "^ Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.^"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "raising numbers to powers"
  - "^ operator [Visual Basic], exponention"
  - "square operator"
  - "^ operator [Visual Basic]"
  - "exponentiation operator [Visual Basic]"
  - "exponent"
  - "numbers, rasing"
  - "powers"
  - "arithmetic operators, exponentiation"
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ^ Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

数値のべき乗を求めます。  
  
## 構文  
  
```  
  
number ^ exponent  
```  
  
## 指定項目  
 `number`  
 必ず指定します。  任意の数式を指定します。  
  
 `exponent`  
 必ず指定します。  任意の数式を指定します。  
  
## 結果  
 結果は、`number` を `exponent` で累乗したもので、常に `Double` 値です。  
  
## サポートされている型  
 `Double`.  他の型のオペランドはすべて `Double` に変換されます。  
  
## 解説  
 Visual Basic は、すべての指数演算を [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md) で行います。  
  
 `exponent` の値は、小数、負の値、またはその両方です。  
  
 1 つの式の中で複数の指数演算が行われるとき、`^` 演算子は左から右の順に評価されます。  
  
> [!NOTE]
>  `^` 演算子は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `^` 演算子を使って数値のべき乗を求める例を次に示します。  結果は、最初のオペランドを第 2 のオペランドで累乗した数値です。  
  
 [!CODE [VbVbalrOperators#20](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#20)]  
  
 この例の結果は、次のようになります。  
  
 `exp1` が 4 \(2 の 2 乗\) に設定されます。  
  
 `exp2` が 19683 \(3 の 3 乗を 3 乗\) に設定されます。  
  
 `exp3` が \-125 \(\-5 の 2 乗\) に設定されます。  
  
 `exp4` が 625 \(\-5 の 4 乗\) に設定されます。  
  
 `exp5` が 2 \(8 の平方根\) に設定されます。  
  
 `exp6` が 0.5 \(1.0 を 8 の平方根で除算した商\) に設定されます。  
  
 この例ではかっこが重要な役割を果たしていることに注目してください。  *演算子の優先順位*のために、Visual Basic では通常 `^` 演算子を、単項 `–` 演算子よりも先に \(つまり最初に\) 実行します。  `exp4` および `exp6` をかっこなしで計算すると、次のような結果になります。  
  
 \-625 になります`exp4 = -5 ^ 4` は として – （第 4 の 5 乗）計算されます。  
  
 `exp6 = 8 ^ -1.0 / 3.0` は \(8 の –1 乗、0.125\) を 3.0 で除算した商となり、0.041666666666666666666666666666667 になります。  
  
## 参照  
 [^\= Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Arithmetic Operators](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)