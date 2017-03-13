---
title: "How to: Define an Operator (Visual Basic) | Microsoft Docs"
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
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "operators [Visual Basic], defining"
  - "procedures, operator"
  - "Visual Basic code, operators"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "operator procedures, about operator procedures"
  - "return values, Operator procedures"
  - "operator overloading"
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Define an Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

クラスまたは構造体を定義してあれば、オペランドの一方または両方が、このクラスまたは構造体のデータ型であるときの、標準の演算子 \(`*`、`<>`、`And` など\) の動作を定義できます。  
  
 標準の演算子を、クラスまたは構造体の演算子プロシージャとして定義します。  すべての演算子プロシージャは `Public` `Shared` である必要があります。  
  
 クラスまたは構造体で演算子を定義することを、演算子を*オーバーロード*するといいます。  
  
## 使用例  
 次の例では、構造体  `height` の `+` 演算子を定義しています。  この構造体では、フィート単位とインチ単位の高さを扱います。  1 *インチ*は 2.54 センチメートル、1 *フィート* は 12 インチです。  値の正規化 \(12.0 以下のインチ\) を確実にするために、コンストラクターは *モジュロ* 12 の演算を実行します。  `+` 演算子は、コンストラクターを使って正規化された値を生成します。  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 `height`  構造体をテストするためには、次のコードを使用してください。  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 使用例を含む詳細については、「[Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703)」を参照してください。  
  
## 参照  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)