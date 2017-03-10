---
title: "Object Variables in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, about object variables"
  - "variables [Visual Basic], object"
  - "objects [Visual Basic], accessing"
  - "object variables"
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Object Variables in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数では、直接に値を格納する他に、オブジェクトを参照することもできます。  変数に値を代入する場合と同様に、変数にオブジェクトへの参照を代入すると、次のような利点が得られます。  
  
-   変数名は、多くの場合、オブジェクト自体にアクセスする場合に必要なメソッドやプロパティへの完全パスに比べて短く覚えやすいものになります。  
  
-   メソッドやプロパティを通じてオブジェクト自体に何度もアクセスするより、オブジェクトを参照する変数を使う方が効率的です。  
  
-   変数は、コードの実行中に、他のオブジェクトを参照するように変更できます。  
  
## コードを短くする  
 オブジェクト変数を使用すると、コードを短くできます。  次の例では、メソッドおよびプロパティの完全パスを使用して <xref:System.Windows.Forms.Control> オブジェクトにアクセスします。  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 この場合、コントロールのオブジェクト変数を使用すると、コードが短くなり、実行時間を短縮できます。  オブジェクト変数を宣言する場合、変数に代入する特定のクラスを指定する必要があります \(この場合は `Control`\)。  変数にオブジェクトを代入した後は、変数を参照先のオブジェクトと同じように扱うことができます。  オブジェクトのプロパティを設定または取得したり、オブジェクトのメソッドを使用したりできます。  次の例では、オブジェクト変数を使用して、上の例のコードを単純化しています。  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## 参照  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [How to: Speed Up Access to an Object with a Long Qualification Path](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)