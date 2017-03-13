---
title: "How to: Call a Property Procedure (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, properties"
  - "procedures, calling"
  - "properties [Visual Basic], property procedures"
  - "procedure calls, property procedures"
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Call a Property Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロパティ プロシージャは、プロパティに値を格納するか、プロパティの値を取得することによって呼び出します。  プロパティのアクセス方法は、変数へのアクセス方法と同じです。  
  
 プロパティの `Set` プロシージャは値を格納し、`Get` プロシージャは値を取得します。  しかし、これらのプロシージャを名前で明示的に呼び出すことはありません。  変数の値を格納および取得するのと同じように、代入ステートメントまたは式の中でプロパティを使用します。  すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] がプロパティのプロシージャを呼び出します。  
  
### プロパティの Get プロシージャを呼び出すには  
  
1.  プロパティ名を、変数名と同様に式の中で使用します。  プロパティは、変数や定数を使用できる場所で使用できます。  
  
     または  
  
     代入ステートメントの等号 \(`=`\) 記号の後ろにプロパティ名を使用します。  
  
     次の例では、<xref:Microsoft.VisualBasic.DateAndTime.Now%2A> プロパティの `Get` プロシージャを呼び出して、値を読み取ります。  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  プロパティが引数を受け取る場合、プロパティ名に続けて、かっこで囲んだ引数リストを指定します。  指定する引数がない場合は、かっこを省略することもできます。  
  
3.  かっこ内の引数リストに、引数をコンマで区切って指定します。  引数は、プロパティがパラメーターを定義したのと同じ順序で渡します。  
  
 プロパティの値は、変数や定数を指定した場合と同じように式の中で使用されます。式の結果は、代入ステートメントの左側にある変数またはプロパティに格納されます。  
  
### プロパティの Set プロシージャを呼び出すには  
  
1.  代入ステートメントの左側にプロパティ名を指定します。  
  
     次の例では、<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> プロパティの `Set` プロシージャを呼び出して、値を設定します。  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  プロパティが引数を受け取る場合、プロパティ名に続けて、かっこで囲んだ引数リストを指定します。  指定する引数がない場合は、かっこを省略することもできます。  
  
3.  かっこ内の引数リストに、引数をコンマで区切って指定します。  引数は、プロパティがパラメーターを定義したのと同じ順序で渡します。  
  
 代入ステートメントの右側で生成された値が、プロパティに格納されます。  
  
## 参照  
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)   
 [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)