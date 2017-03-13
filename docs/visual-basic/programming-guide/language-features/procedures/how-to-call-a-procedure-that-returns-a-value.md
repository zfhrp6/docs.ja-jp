---
title: "How to: Call a Procedure That Returns a Value (Visual Basic) | Microsoft Docs"
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
  - "procedure calls, returning values"
  - "Visual Basic code, procedures"
  - "procedures, calling"
  - "procedures, returning a value"
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Call a Procedure That Returns a Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Function` プロシージャは呼び出し元のコードに値を返します。  これを呼び出すには、代入ステートメントの右側または式の中に、名前と引数を指定します。  
  
### Function プロシージャを式内で呼び出すには  
  
1.  変数の場合と同様に、`Function` プロシージャの名前を使用します。  `Function` プロシージャ呼び出しは、式内の、変数または定数を使用できる場所で使用できます。  
  
2.  プロシージャ名に、かっこで囲んだ引数リストを指定します。  指定する引数がない場合は、かっこを省略することもできます。  しかし、かっこを使用した方がコードが読みやすくなります。  
  
3.  かっこ内の引数リストに、引数をコンマで区切って指定します。  引数は、`Function` プロシージャの対応するパラメーターの定義と同じ順序で指定する必要があります。  
  
     また、1 つまたは複数の引数を名前で渡すこともできます。  詳細については、「[Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)」を参照してください。  
  
4.  プロシージャから返される値は、変数や定数の値と同じように式の一部となります。  
  
### 代入ステートメントで Function プロシージャを呼び出すには  
  
1.  代入ステートメントの等号 \(`=`\) 記号の後ろに `Function` プロシージャの名前を使用します。  
  
2.  プロシージャ名に、かっこで囲んだ引数リストを指定します。  指定する引数がない場合は、かっこを省略することもできます。  しかし、かっこを使用した方がコードが読みやすくなります。  
  
3.  かっこ内の引数リストに、引数をコンマで区切って指定します。  名前で渡す場合を除き、引数は、`Function` プロシージャがパラメーターを定義したのと同じ順序で渡します。  
  
4.  プロシージャから返される値は、代入ステートメントの左側の変数またはプロパティに格納されます。  
  
## 使用例  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の <xref:Microsoft.VisualBasic.Interaction.Environ%2A> を呼び出して、オペレーティング システムの環境変数の値を取得する例を次に示します。  最初の行では `Environ` を式から呼び出し、2 行目ではこれを代入ステートメントから呼び出します。  `Environ` は、唯一の引数として変数名を受け取ります。  変数の値が呼び出し元のコードに返されます。  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## 参照  
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [How to: Create a Procedure that Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [How to: Return a Value from a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [How to: Call a Procedure that Does Not Return a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)