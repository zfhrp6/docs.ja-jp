---
title: "How to: Return a Value from a Procedure (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "procedures, returning from"
  - "procedures, returning a value"
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Return a Value from a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Function` プロシージャは、 `Return` ステートメントを実行したとき、または `Exit Function` ステートメントか `End Function` ステートメントを実行したときに、呼び出し元のコードに値を返します。  
  
### Return ステートメントを使って値を返すには  
  
1.  プロシージャのタスクが完了するポイントに `Return` ステートメントを記述します。  
  
2.  キーワード `Return` に続けて、呼び出し元のコードに返す値を取得する式を定義します。  
  
3.  同じプロシージャ内に、複数の `Return` ステートメントを定義できます。  
  
     次の `Function` プロシージャは、直角三角形の最も長い辺 \(斜辺\) を計算し、結果を呼び出し元のコードに返します。  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     `hypotenuse` を呼び出す一般的な例は次のようになります。このコードは戻り値を格納します。  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### Exit Function または End Function を使用して値を返すには  
  
1.  `Function` プロシージャ内の少なくとも 1 か所で、値をプロシージャ名に代入します。  
  
2.  `Exit Function` ステートメントまたは `End Function` ステートメントを実行すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は直前にプロシージャ名に代入された値を返します。  
  
3.  同じプロシージャに複数の `Exit Function` ステートメントを定義できます。また、`Return` ステートメントと `Exit Function` ステートメントを同じプロシージャに混在させることもできます。  
  
4.  `Function` プロシージャには、`End Function` ステートメントを 1 つだけ定義できます。  
  
     詳細および使用例については、「[Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)」の「戻り値」を参照してください。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md)   
 [How to: Create a Procedure that Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)