---
title: "How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic) | Microsoft Docs"
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
  - "variables [Visual Basic], accessing"
  - "variables [Visual Basic], object"
  - "With statement"
  - "With block"
  - "object variables, accessing"
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

複数のメソッドおよびプロパティの修飾パスを必要とするオブジェクトに頻繁にアクセスする場合、修飾パスを繰り返さないことによりコーディングの時間を短縮できます。  
  
 修飾パスの繰り返しを回避するには、2 つの方法があります。  変数にオブジェクトを割り当てるか、またはオブジェクトを `With`...`End With` ブロックで使用します。  
  
### 過度に修飾されたオブジェクトを変数に割り当ててそれに対するアクセス時間を短縮するには  
  
1.  頻繁にアクセスするオブジェクトの型の変数を宣言します。  宣言の初期化の部分で修飾パスを指定します。  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  変数を使用してオブジェクトのメンバーにアクセスします。  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### With...End With ブロックを使用して、過度に修飾されたオブジェクトへのアクセス時間を短縮するには  
  
1.  `With` ステートメントに修飾パスを挿入します。  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  `End With` ステートメントの前の部分で、`With` ブロックの内でオブジェクトのメンバーにアクセスします。  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## 参照  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)