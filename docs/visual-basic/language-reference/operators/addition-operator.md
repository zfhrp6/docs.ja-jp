---
title: "+ Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.+"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arithmetic operators, addition"
  - "+ operator"
  - "concatenation operators, syntax"
  - "strings [Visual Basic], concatenating"
  - "sum operator"
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# + Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

2 つの数を加算するか、数値式の正の値を返します。  2 つの文字列式を連結するためにも使用できます。  
  
## 構文  
  
```  
  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`expression1`|必ず指定します。  任意の数式または文字列式を指定します。|  
|`expression2`|`+` 演算子が負の値を計算している場合を除き、必ず指定します。  任意の数式または文字列式を指定します。|  
  
## 結果  
 `expression1` と `expression2` がどちらも数値の場合、結果は 2 つの合計を計算した値になります。  
  
 `expression2` が指定されなければ、`+` 演算子は*単項*恒等演算子となり、式の値は変わりません。  つまり、演算において `expression1` の符号が保持されるため、`expression1` が負であれば結果は負になります。  
  
 `expression1` と `expression2` がどちらも文字列であれば、結果は 2 つの値を連結した文字列になります。  
  
 `expression1` と `expression2` の型が異なる場合は、2 つの型、内容、および [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) の設定に応じて異なる処理が行われます。  詳細については、「解説」の表を参照してください。  
  
## サポートされている型  
 unsigned 型と浮動小数点型を含むすべての数値型、および 10 進型 \(`Decimal`\)、文字列型 \(`String`\)。  
  
## 解説  
 一般に、`+` は可能であれば加算を行い、両方の式が文字列の場合にだけ連結を行います。  
  
 どちらの式も `Object` でない場合、Visual Basic は次の処理を行います。  
  
|||  
|-|-|  
|式のデータ型|コンパイラによる処理|  
|両方の式が数値型 \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、または `Double`\) の場合|加算。  結果のデータ型は、`expression1` と `expression2` のデータ型に適した数値型です。  「[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「整数演算」の表を参照してください。|  
|両方の式が文字列型 \(`String`\) の場合|文字列連結。|  
|一方が数値データ型で他方が文字列の場合|`Option Strict` が `On` であれば、コンパイル エラーが発生します。<br /><br /> `Option Strict` が `Off` であれば、`String` が `Double` に暗黙的に変換されて加算されます。<br /><br /> `String` を倍精度浮動小数点数型 \(`Double`\) に変換できない場合は、<xref:System.InvalidCastException> 例外がスローされます。|  
|一方が数値で他方が [Nothing](../../../visual-basic/language-reference/nothing.md) の場合|`Nothing` を値 0 として加算が行われます。|  
|一方が文字列で他方が `Nothing` の場合|`Nothing` を値 "" として連結が行われます。|  
  
 一方の式が `Object` 式である場合、Visual Basic は次の処理を行います。  
  
|||  
|-|-|  
|式のデータ型|コンパイラによる処理|  
|`Object` 式に数値が格納され、もう一方が数値型の場合|`Option Strict` が `On` であれば、コンパイル エラーが発生します。<br /><br /> `Option Strict` が `Off` であれば、加算が行われます。|  
|`Object`式に数値が格納され、もう一方が文字列型の場合`String` 型です。|`Option Strict` が `On` であれば、コンパイル エラーが発生します。<br /><br /> `Option Strict` が `Off` であれば、`String` が `Double` に暗黙的に変換されて加算されます。<br /><br /> `String` を倍精度浮動小数点数型 \(`Double`\) に変換できない場合は、<xref:System.InvalidCastException> 例外がスローされます。|  
|`Object` 式に文字列が格納され、もう一方が数値型の場合|`Option Strict` が `On` であれば、コンパイル エラーが発生します。<br /><br /> `Option Strict` が `Off` であれば、文字列の `Object` が `Double` に暗黙的に変換されて加算されます。<br /><br /> 文字列の \(`Object`\) を倍精度浮動小数点数型 \(`Double`\) に変換できない場合は、<xref:System.InvalidCastException> 例外がスローされます。|  
|`Object`式に文字列が格納され、もう一方が `String` 型です。|`Option Strict` が `On` であれば、コンパイル エラーが発生します。<br /><br /> `Option Strict` が `Off` であれば、`Object` が `String` に暗黙的に変換されて連結されます。|  
  
 両方の式が `Object` である場合、Visual Basic は次の処理を行います \(`Option Strict Off` の場合のみ\)。  
  
|||  
|-|-|  
|式のデータ型|コンパイラによる処理|  
|両方の `Object` 式に数値が格納されている場合|加算。|  
|両方の `Object` 式が文字列型 \(`String`\) である場合|文字列連結。|  
|一方の `Object` 式に数値が格納され、他方に文字列が格納されている場合|文字列の `Object` を倍精度浮動小数点数型 \(`Double`\) に暗黙的に変換して加算します。<br /><br /> 文字列の `Object` を数値に変換できない場合は、<xref:System.InvalidCastException> 例外がスローされます。|  
  
 いずれかの `Object` 式が [Nothing](../../../visual-basic/language-reference/nothing.md) または <xref:System.DBNull> に評価される場合、`+` 演算子はそれを値 "" の `String` として扱います。  
  
> [!NOTE]
>  `+` 演算子を使用すると、加算と文字列連結のどちらが行われるのか、事前にはわかりにくい場合があります。  連結に `&` 演算子を使用することで、あいまいさがなくなり、プログラムの可読性が向上します。  
  
## オーバーロード  
 `+` 演算子は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `+` 演算子を使って数値を加算する例を次に示します。  両方のオペランドが数値であれば、Visual Basic は算術演算を行います。  算術演算の結果は、2 つのオペランドの合計になります。  
  
 [!CODE [VbVbalrOperators#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#6)]  
  
 `+` 演算子を使用して、文字列を連結することもできます。  両方のオペランドが文字列であれば、Visual Basic はこれらを連結します。  連結結果は 2 つのオペランドの内容を前後につなげた単一の文字列になります。  
  
 オペランドの型が同じでない場合、結果は [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) の設定によって異なります。  `Option Strict` が `On` であれば、結果は次の例のようになります。  
  
 [!CODE [VbVbalrOperators#53](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#53)]  
  
 [!CODE [VbVbalrOperators#50](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#50)]  
[!CODE [VbVbalrOperators#51](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#51)]  
  
 `Option Strict` が `Off` であれば、結果は次の例のようになります。  
  
 [!CODE [VbVbalrOperators#54](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#54)]  
  
 [!CODE [VbVbalrOperators#50](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#50)]  
[!CODE [VbVbalrOperators#52](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#52)]  
  
 あいまいさをなくすため、連結には `+` 演算子ではなく `&` 演算子を使うようにしてください。  
  
## 参照  
 [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)   
 [Concatenation Operators](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Arithmetic Operators](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)