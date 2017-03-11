---
title: "How to: Create a Procedure that Returns a Value (Visual Basic) | Microsoft Docs"
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
  - "procedures, returning a value"
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Create a Procedure that Returns a Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

呼び出し元のコードに体を返すには、`Function` プロシージャを使用します。  
  
### 値を返すプロシージャを作成するには  
  
1.  その他のプロシージャの外部で、`Function` ステートメントと `End Function` ステートメントを使用します。  
  
2.  `Function` ステートメントの中では、`Function` キーワードの後にプロシージャの名前とかっこで囲んだパラメーター リストを指定します。  
  
3.  かっこの後には `As` 句で、返された値のデータ型を指定します。  
  
4.  プロシージャのコード ステートメントは、`Function` と `End Function` ステートメントの間に記述します。  
  
5.  `Return` ステートメントを使用して、呼び出し元のコードに値を返します。  
  
     次の `Function` プロシージャは、直角三角形の最も長い辺 \(斜辺\) を他の 2 つの辺の値を基に計算します。  
  
     [!code-vb[VbVbcnProcedures#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-create-a-procedur_1.vb)]  
  
     `hypotenuse` の一般的な呼び出しを次に示します。  
  
     [!code-vb[VbVbcnProcedures#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-create-a-procedur_2.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [How to: Return a Value from a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)