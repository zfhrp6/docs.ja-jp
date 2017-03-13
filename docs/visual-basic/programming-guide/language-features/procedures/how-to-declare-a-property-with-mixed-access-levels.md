---
title: "How to: Declare a Property with Mixed Access Levels (Visual Basic) | Microsoft Docs"
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
  - "access levels, properties"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "mixed access levels"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], access levels"
  - "Property statement, declaring mixed access levels"
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Declare a Property with Mixed Access Levels (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロパティ上の `Get` および `Set` プロシージャに異なるアクセス レベルを割り当てるには、`Property` ステートメントでは制限のレベルを低くし、`Get` または `Set` ステートメントで制限のレベルを高くします。  混合アクセス レベルを使用すると、コード内の特定の部分がプロパティの値を取得できるようにし、他の特定の部分でその値を変更できるようにすることができます。  
  
 アクセス レベルの詳細については、「[Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
### 混合アクセス レベルでプロパティを宣言するには  
  
1.  通常どおりプロパティを宣言し、`Property` ステートメントで制限の緩いアクセス レベル \(`Public` など\) を指定します。  
  
2.  `Get` または `Set` プロシージャは、より制限の厳しいアクセス レベル \(`Friend` など\) を指定して宣言します。  
  
3.  その他のプロパティ プロシージャではアクセス レベルを指定しません。  `Property` ステートメントで宣言されたアクセス レベルが使用されます。  アクセスを制限できるのは、プロパティ プロシージャのうち 1 つだけです。  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     上の例では、`Get` プロシージャはプロパティと同じ `Protected` アクセスを持ち、`Set` プロシージャは `Private` アクセスを持ちます。  `employee` から派生したクラスは、`salary` の値を読み取ることができますが、この値を設定できるのは `employee` クラスのみです。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)