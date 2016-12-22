---
title: "Operator Procedures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, procedures"
  - "procedures, operator"
  - "Visual Basic code, operators"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "overloaded operators"
  - "operator overloading"
  - "operator procedures"
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operator Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

演算子プロシージャは、定義したクラスまたは構造体で、標準の演算子 \(`*`、`<>`、`And` など\) の動作を定義する一連の [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ステートメントです。  これは、*演算子のオーバーロード*ともいいます。  
  
## 演算子プロシージャを定義する場合  
 クラスまたは構造体を定義する場合、そのクラスまたは構造体の型で変数を宣言できます。  このような変数は、式の一部として演算にかかわる必要のある場合があります。  このためには、この変数は演算子のオペランドである必要があります。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、基本データ型でのみ演算子を定義します。  演算子の動作は、オペランドのいずれか、または両方が、そのクラスまたは構造体の型である場合に定義できます。  
  
 詳細については、「[Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)」を参照してください。  
  
## 演算子プロシージャの種類  
 演算子プロシージャは次のいずれかの種類です。  
  
-   引数がクラスまたは構造体の型である、単項演算子の定義。  
  
-   少なくとも 1 つの引数がクラスまたは構造体の型である、二項演算子の定義。  
  
-   引数がクラスまたは構造体の型である、変換演算子の定義。  
  
-   クラスまたは構造体の型を返す変換演算子の定義。  
  
 変換演算子は常に単項であり、定義する演算子として常に `CType` を使用します。  
  
## 宣言の構文  
 演算子プロシージャを宣言する構文は次のとおりです。  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`   ``  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 `Widening` または `Narrowing` キーワードは、型変換演算子にのみ使用します。  型変換演算子の演算子記号は常に [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)です。  
  
 二項演算子を定義するには 2 つのオペランドを宣言し、型変換演算子を含む単項演算子を定義するには 1 つのオペランドを宣言します。  すべてのオペランドは `ByVal` で宣言する必要があります。  
  
 各オペランドの宣言は、[Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)にパラメーターを宣言する場合と同じです。  
  
### \[データ型\]  
 定義済みのクラスまたは構造体で演算子を定義するので、最低でも 1 つのオペランドはそのクラスまたは構造体の型である必要があります。  型変換演算子では、オペランドまたは戻り値の型が、クラスまたは構造体のデータ型である必要があります。  
  
 詳細については、「[Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)」を参照してください。  
  
## 呼び出し構文  
 式の中で演算子記号を使用することで、暗黙的に演算子プロシージャを呼び出すことができます。  オペランドは、定義済みの演算子の場合と同じように指定します。  
  
 演算子プロシージャを暗黙的に呼び出す構文は次のとおりです。  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`  
  
### 宣言と呼び出しの説明  
 次の構造体は、符号付き 128 ビットの整数値を、上位と下位の構成部分として格納します。  `+` 演算子を定義し、2 つの  `veryLong`  値を追加し、最終的な  `veryLong`  値を生成します。  
  
 [!code-vb[VbVbcnProcedures#23](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 次の例では、 `veryLong` で定義された `+` 演算子の一般的な呼び出しを示します。  
  
 [!code-vb[VbVbcnProcedures#24](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 使用例を含む詳細については、「[Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703)」を参照してください。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [How to: Call an Operator Procedure](../Topic/How%20to:%20Call%20an%20Operator%20Procedure%20\(Visual%20Basic\).md)   
 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)