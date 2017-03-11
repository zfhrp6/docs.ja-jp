---
title: "How to: Use a Class that Defines Operators (Visual Basic) | Microsoft Docs"
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
  - "operator procedures, calling"
  - "procedures, operator"
  - "procedures, calling"
  - "examples [Visual Basic], CType"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "return values, Operator procedures"
  - "operator overloading"
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# How to: Use a Class that Defines Operators (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

独自の演算子を定義するクラスまたは構造体を使用している場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] でこれらの演算子にアクセスできます。  
  
 クラスまたは構造体で演算子を定義することを、演算子を*オーバーロード*するといいます。  
  
## 使用例  
 次の例では、SQL 文字列と [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 文字列を相互に変換する変換演算子 \([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)\) を定義する SQL 構造体 <xref:System.Data.SqlTypes.SqlString> にアクセスします。  SQL 文字列を [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 文字列に変換するには `CType(`*SQL 文字列式*, `String)` を使用し、逆の変換を行うには `CType(`*Visual Basic 文字列式*, <xref:System.Data.SqlTypes.SqlString>`)` を使用します。  
  
 [!code-vb[VbVbcnProcedures#30](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-use-a-class-that-_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-use-a-class-that-_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString> 構造体は、`String` から <xref:System.Data.SqlTypes.SqlString> へ、そして <xref:System.Data.SqlTypes.SqlString> から `String` への変換を行う変換演算子 \([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)\) を定義します。  `title` を `jobTitle` に代入するステートメントは最初の演算子を使用し、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 関数の呼び出しは 2 つ目の演算子を使用します。  
  
## コードのコンパイル  
 使用しているクラスまたは構造体が、必要な演算子を定義していることを確認してください。  クラスまたは構造体が、オーバーロード可能なすべての演算子を定義しているとは限りません。  利用可能な演算子の一覧については、「[Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)」 を参照してください。  
  
 ソース ファイルの先頭に、SQL 文字列用の適切な `Imports` ステートメントを含めます \(この場合は、<xref:System.Data.SqlTypes>\)。  
  
 プロジェクトには、System.Data および System.XML への参照が必要です。  
  
## 参照  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)