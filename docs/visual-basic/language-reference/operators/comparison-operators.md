---
title: "Comparison Operators (Visual Basic) | Microsoft Docs"
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
  - "vb.<>"
  - "vb.>="
  - "vb.<="
  - "vb.>"
  - "vb.<"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "greater than or equal to operator [Visual Basic]"
  - ">= operator [Visual Basic]"
  - "= operator [Visual Basic]"
  - "< operator [Visual Basic]"
  - "less than operator [Visual Basic]"
  - "relational operators, syntax"
  - "Like operator [Visual Basic]"
  - "<> operator [Visual Basic]"
  - "> operator [Visual Basic]"
  - "equal operator [Visual Basic]"
  - "less than or equal to operator [Visual Basic]"
  - "symbols, operators"
  - "greater than operator [Visual Basic]"
  - "comparing values [Visual Basic]"
  - "operators [Visual Basic], relational"
  - "string comparison [Visual Basic]"
  - "not equal to comparison operator [Visual Basic]"
  - "<= operator [Visual Basic]"
  - "operators [Visual Basic], comparison"
  - "Is operator [Visual Basic]"
  - "comparison operators, Visual Basicl"
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comparison Operators (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Basic では以下の比較演算子が定義されています。  
  
 `<` 演算子  
  
 `<=` 演算子  
  
 `>` 演算子  
  
 `>=` 演算子  
  
 `=` 演算子  
  
 `<>` 演算子  
  
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 これらの演算子は、2 つの式を比較して、この 2 つが等しいかどうか、等しくない場合はどのように異なるかを判断します。  `Is`、`IsNot`、`Like` は、別のヘルプ トピックで解説します。  関係比較演算子は、このページで解説します。  
  
## 構文  
  
```  
  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  比較の結果を表す `Boolean` 値です。  
  
 `expression`  
 必ず指定します。  任意の式を指定します。  
  
 `comparisonoperator`  
 必ず指定します。  任意の関係比較演算子を指定します。  
  
 `object1`, `object2`  
 必ず指定します。  任意の参照オブジェクト名を指定します。  
  
 `string`  
 必ず指定します。  任意のブール型 \(`String`\) の式を指定します。  
  
 `pattern`  
 必ず指定します。  任意の文字列 \(`String`\) 式、または文字の範囲を指定します。  
  
## 解説  
 次の表は、比較演算子と条件の一覧です。この組み合わせにより、演算結果 `result` が `True`、`False` のどちらになるかが決まります。  
  
|\[演算子\]|`True` の条件|`False` の条件|  
|-------------|----------------|-----------------|  
|`<` \(より小さい\)|`expression1` \< `expression2`|`expression1` \>\= `expression2`|  
|`<=` \(以下\)|`expression1` \<\= `expression2`|`expression1` \> `expression2`|  
|`>` \(より大きい\)|`expression1` \> `expression2`|`expression1` \<\= `expression2`|  
|`>=` \(以上\)|`expression1` \>\= `expression2`|`expression1` \< `expression2`|  
|`=` \(等しい\)|`expression1` \= `expression2`|`expression1` \<\> `expression2`|  
|`<>` \(等しくない\)|`expression1` \<\> `expression2`|`expression1` \= `expression2`|  
  
> [!NOTE]
>  [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) は、代入演算子としても使用されます。  
  
 `Is` 演算子、`IsNot` 演算子、`Like` 演算子は、この表の演算子とは異なる特定の比較機能を持ちます。  
  
## 数値を比較する  
 単精度浮動小数点数型 \(`Single`\) の式を倍精度浮動小数点数型 \(`Double`\) の式と比較する場合は、単精度浮動小数点数型 \(`Single`\) 式が倍精度浮動小数点数型 \(`Double`\) 式に変換されます。  この動作は、Visual Basic 6 の場合と逆になっています。  
  
 同様に、10 進型 \(`Decimal`\) の式を単精度浮動小数点数型 \(`Single`\) または倍精度浮動小数点数型 \(`Double`\) の式と比較する場合は、10 進型 \(`Decimal`\) 式が単精度浮動小数点数型 \(`Single`\) または倍精度浮動小数点数型 \(`Double`\) 式に変換されます。  10 進型 \(`Decimal`\) 式では、1E\-28 よりも小さい小数値は失われます。  1E\-28 より小さい小数値が失われると、本来は等しくない 2 つの数値を比較すると、等しいと判断される可能性があります。  このため、等号 \(`=`\) を使用して 2 つの浮動小数点変数を比較する場合は注意が必要です。  2 つの数値の差の絶対値が許容差よりも小さいかどうかを確認することが推奨されます。  
  
### 浮動小数点の不正確性  
 浮動小数点数を扱う場合、これらの値がメモリ内で常に正確に表現されているわけではないことに注意してください。  これにより、値の比較や [Mod 演算子](../../../visual-basic/language-reference/operators/mod-operator.md) などの特定の演算が予期しない結果になることがあります。  詳細については、「[Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。  
  
## 文字列の比較  
 文字列を比較するとき、文字列式は `Option Compare` の設定によるアルファベット順の並べ替え順序を基に評価されます。  
  
 `Option Compare Binary` では、文字の内部バイナリ表現による並べ替え順序に基づいて文字列が比較されます。  並べ替え順序は、コード ページによって決まります。  次の例で、一般的なバイナリの並べ替え順序を示します。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` では、文字列比較は、大文字と小文字を区別しない、アプリケーションのロケールで決められたテキストの並べ替え順序に基づいて行われます。  `Option Compare Text` を設定して、上の例の文字を並べ替えると、次のテキストの並べ替え順序が適用されます。  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### ロケールの依存関係  
 `Option Compare Text` を設定すると、文字列比較の結果が、アプリケーションが実行されているロケールに依存します。  あるロケールでは同一であると判断される文字も、別のロケールでは異なる文字として扱われることがあります。  文字列比較を使用して重要な判断 \(ログオンを許可するかどうかなど\) をする場合は、ロケールの区別に十分注意してください。  `Option Compare Binary` を設定するか、ロケールを考慮する <xref:Microsoft.VisualBasic.Strings.StrComp%2A> を呼び出すかを検討してください。  
  
## 関係比較演算子を使った型宣言を省略したプログラミング  
 `Option Strict On` では、`Object` 式には関係比較演算子を使用できません。  `Option Strict` が `Off` の場合、および、`expression1` または `expression2` が `Object` 式の場合、実行時の型によって比較方法が決まります。  次の表は、式を比較する方法および比較した結果をオペランドのランタイム型に応じて示したものです。  
  
|オペランドの種類|比較の種類|  
|--------------|-----------|  
|両方が `String` の場合|文字列の並べ替え特性に基づいて並べ替え比較が行われます。|  
|両方が数値の場合|オブジェクトが `Double` に変換され、数値比較|  
|一方が数値、他方が `String` の場合|`String` は倍精度浮動小数点数型 \(`Double`\) に変換され、数値比較が行われます。  文字列型 \(`String`\) を倍精度浮動小数点数型 \(`Double`\) に変換できない場合は、<xref:System.InvalidCastException> がスローされます。|  
|一方または両方が文字列 \(`String`\) 以外の参照型の場合|<xref:System.InvalidCastException> がスローされます。|  
  
 数値の比較では、`Nothing` は 0 として扱われます。  文字列比較では、`Nothing` は `""` \(空の文字列\) として扱われます。  
  
## オーバーロード  
 関係比較演算子 \(`<`、  `<=`、`>`、`>=`、`=`、`<>`\) は*オーバーロード*できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  このようなクラスまたは構造体でこれらの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
 [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) は関係比較演算子としてのみオーバーロードでき、代入演算子としてはオーバーロードできないことに注意してください。  
  
## 使用例  
 式の比較に用いる関係比較演算子のさまざまな使用例を次に示します。  関係比較演算子は、指定した式が真 \(`True`\) かどうかを表す `Boolean` 型の結果を返します。  `>` 演算子と `<` 演算子を文字列に適用する場合は、通常のアルファベット順で文字列の比較が行われます。  この順序は、ロケールの設定に依存する可能性があります。  並べ替えが大文字と小文字を区別するかどうかは、[Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)の設定値によって決まります。  
  
 [!CODE [VbVbalrOperators#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#1)]  
  
 上の例では、最初の比較が `False` を返し、その他の比較が `True` を返します。  
  
## 参照  
 <xref:System.InvalidCastException>   
 [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)