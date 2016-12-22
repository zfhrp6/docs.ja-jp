---
title: "How to: Put a Value in a Property (Visual Basic) | Microsoft Docs"
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
  - "property values"
  - "Visual Basic code, procedures"
  - "values, properties"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], values"
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Put a Value in a Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プロパティにデータを格納するには、代入ステートメントの左側にプロパティ名を置きます。  
  
 プロパティの `Set` プロシージャは値を格納しますが、このプロシージャを明示的に名前で呼び出すことはありません。  プロパティは、変数を使用するときと同じように使用します。  すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] がプロパティのプロシージャを呼び出します。  
  
### プロパティに値を格納するには  
  
1.  代入ステートメントの左側にプロパティ名を指定します。  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の `TimeOfDay` プロパティの `Set` プロシージャを暗黙的に呼び出して、このプロパティを正午に設定する例を次に示します。  
  
     [!code-vb[VbVbcnProcedures#11](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  プロパティが引数を受け取る場合、プロパティ名に続けて、かっこで囲んだ引数リストを指定します。  指定する引数がない場合は、かっこを省略することもできます。  
  
3.  かっこ内の引数リストに、引数をコンマで区切って指定します。  引数は、プロパティがパラメーターを定義したのと同じ順序で渡します。  
  
4.  代入ステートメントの右側で生成された値が、プロパティに格納されます。  
  
## 参照  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Get a Value from a Property](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)