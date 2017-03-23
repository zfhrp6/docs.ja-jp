---
title: "&amp; Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.&"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "And (&) operator"
  - "ampersand operator (&)"
  - "& operator"
  - "concatenation operators, syntax"
  - "strings [Visual Basic], concatenating"
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# &amp; Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つの式に対して文字列連結を行います。  
  
## 構文  
  
```  
  
result = expression1 & expression2  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  文字列 \(`String`\) 変数またはオブジェクト \(`Object`\) 変数を指定します。  
  
 `expression1`  
 必ず指定します。  文字列型 \(`String`\) に拡大変換されるデータ型の式です。  
  
 `expression2`  
 必ず指定します。  文字列型 \(`String`\) に拡大変換されるデータ型の式です。  
  
## 解説  
 `expression1` または `expression2` のデータ型が文字列型 \(`String`\) でなくても文字列型 \(`String`\) に拡大変換される場合は、文字列型 \(`String`\) に変換されます。  いずれかのデータ型が文字列型 \(`String`\) に拡大変換されない場合は、コンパイラでエラーが発生します。  
  
 通常、演算結果 `result` のデータ型は文字列型 \(`String`\) です。  どちらか、または両方の式の評価が [Nothing](../../../visual-basic/language-reference/nothing.md) の場合、または、<xref:System.DBNull.Value?displayProperty=fullName> の値を持つ場合、"" という値を持つ文字列として扱われます。  
  
> [!NOTE]
>  `&` 演算子は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
> [!NOTE]
>  アンパサンド \(&\) 文字を使用して、`Long` 型として変数を指定することもできます。  詳細については、「[Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)」を参照してください。  
  
## 使用例  
 `&` 演算子を使って文字列の連結を行う例を次に示します。  結果は、2 つの文字列オペランドの連結を表す文字列値になります。  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## 参照  
 [&\= Operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Concatenation Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)