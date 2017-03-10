---
title: "Comparison Operators in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comparison operators, comparing strings"
  - "comparison operators, comparing objects"
  - "strings [Visual Basic], comparing"
  - "comparison operators"
  - "string comparison [Visual Basic], operators"
  - "objects [Visual Basic], comparing"
  - "numbers, comparing"
  - "Visual Basic code, operators"
  - "string comparison [Visual Basic]"
  - "numeric values, comparing"
  - "comparison operators, comparing numeric values"
  - "operators [Visual Basic], comparison"
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Comparison Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

比較演算子は 2 つの式を比較し、それらの値の関係を表す `Boolean` 値を返します。  比較演算子には、数値を比較する演算子、文字列を比較する演算子、およびオブジェクトを比較する演算子があります。  ここでは、これら 3 種類の演算子についてそれぞれ説明します。  
  
## 数値の比較  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、6 つの数値比較演算子を使って数値を比較します。  どの演算子も、数値に評価される 2 つの式をオペランドとして受け取ります。  次の表に、これらの演算子とそれぞれの使用例を示します。  
  
|\[演算子\]|テスト条件|例|  
|-------------|-----------|-------|  
|`=` \(等しい\)|1 番目の式の値と 2 番目の式の値が等しいかどうか。|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` \(等しくない\)|1 番目の式の値と 2 番目の式の値が等しくないかどうか。|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` \(より小さい\)|1 番目の式の値が 2 番目の式の値よりも小さいかどうか。|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` \(より大きい\)|1 番目の式の値が 2 番目の式の値よりも大きいかどうか。|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` \(以下\)|1 番目の式の値が 2 番目の式の値よりも小さい、または等しいかどうか。|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` \(以上\)|1 番目の式の値が 2 番目の式の値よりも大きい、または等しいかどうか。|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## 文字列の比較  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、数値比較演算子の他に [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md)を使用して文字列を比較します。  `Like` を使うと、パターンが指定できます。  このパターンと文字列とを比較し、一致した場合に結果が `True` になります。  それ以外の場合、結果は `False` になります。  数値演算子を使うと、次の例のように、並べ替え順序に基づいて文字列型 \(`String`\) の値を比較できます。  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 この例では、1 番目の文字列の最初の文字の並べ替え順序が 2 番目の文字列の最初の文字より前であるため、結果は `True` になります。  最初の文字が同じ文字であった場合は、両方の文字列の次の文字が比較されます。  また、次の例に示すように、等号演算子を使って文字列が等しいかどうかを調べることもできます。  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 一方の文字列全体がもう一方の文字列の先頭部分と一致している場合 \("aa" と "aaa" など\) は、長い方の文字列が短い方の文字列よりも大きいと見なされます。  次に例を示します。  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 並べ替え順序は、`Option Compare` の設定により、バイナリ モードの比較またはテキスト モードの比較が基になります。  詳細については、「[Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md)」を参照してください。  
  
## オブジェクトの比較  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、2 つのオブジェクト参照変数を[Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md)と [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)を使って比較します。  この 2 つの演算子のどちらを使っても、2 つの参照変数が同じオブジェクトのインスタンスを参照しているかどうかを調べることができます。  次に例を示します。  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/comparison-operators_1.vb)]  
  
 この例では、両方の変数が同じインスタンスを参照しているので、`x Is y` は `True` に評価されます。  この結果を次の例と比べてみてください。  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/comparison-operators_2.vb)]  
  
 この例では、`x Is y` は `False` になります。これは、変数は同じ型のオブジェクトを参照していますが、参照しているインスタンスが異なるためです。  
  
 2 つのオブジェクトが同じインスタンスをポイントしていないことを調べる場合は、`IsNot` 演算子を使うと `Not` と `Is` を合わせた不恰好な文法を使わずに済みます。  次に例を示します。  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/comparison-operators_3.vb)]  
  
 この例の `If a IsNot b` は、`If Not a Is b` と同じ意味になります。  
  
### オブジェクト型の比較  
 オブジェクトが特定の型かどうかを調べるには、`TypeOf`...`Is` の式を使います。  構文は次のとおりです。  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 `typename` にインターフェイスの型を指定すると、オブジェクトがそのインターフェイス型を実装している場合に、`TypeOf`...`Is` の式が `True` を返します。  `typename` にクラス型を指定すると、オブジェクトがそのクラスのインスタンスであるか、またはそのクラスの派生クラスのインスタンスである場合に `True` が返されます。  次に例を示します。  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/comparison-operators_4.vb)]  
  
 この例では、`x` の型が `Button` であり、`Control` から継承しているので、`TypeOf x Is Control` の式は `True` になります。  
  
 詳細については、「[TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md)」を参照してください。  
  
## 参照  
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operators](../../../../visual-basic/language-reference/operators/index.md)   
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)