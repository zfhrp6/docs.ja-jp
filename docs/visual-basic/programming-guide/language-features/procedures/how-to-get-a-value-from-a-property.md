---
title: "How to: Get a Value from a Property (Visual Basic) | Microsoft Docs"
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
  - "property values"
  - "Visual Basic code, procedures"
  - "values, properties"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], values"
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Get a Value from a Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロパティの値を取得するには、式にプロパティ名を含めます。  
  
 値を取得するのはプロパティの `Get` プロシージャですが、このプロシージャの名前を指定して呼び出すのではありません。  プロパティは、変数を使用するときと同じように使用します。  すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] がプロパティのプロシージャを呼び出します。  
  
### プロパティから値を取得するには  
  
1.  プロパティ名を、変数名と同様に式の中で使用します。  プロパティは、変数や定数を使用できる場所で使用できます。  
  
     または  
  
     代入ステートメントの等号 \(`=`\) 記号の後ろにプロパティ名を使用します。  
  
     次の例は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の `Now` プロパティの値を読み込みます。`Get` プロシージャが暗黙的に呼び出されています。  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  プロパティが引数を受け取る場合、プロパティ名に続けて、かっこで囲んだ引数リストを指定します。  指定する引数がない場合は、かっこを省略することもできます。  
  
3.  かっこ内の引数リストに、引数をコンマで区切って指定します。  引数は、プロパティがパラメーターを定義したのと同じ順序で渡します。  
  
 プロパティの値は、変数や定数を指定した場合と同じように式の中で使用されます。式の結果は、代入ステートメントの左側にある変数またはプロパティに格納されます。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)