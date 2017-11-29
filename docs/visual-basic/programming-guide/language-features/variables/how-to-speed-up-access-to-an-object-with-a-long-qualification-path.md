---
title: "方法: 長い修飾パスを持つオブジェクトに対するアクセス時間を短縮する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d91eeaeb034a4c8b4fefcffdf2fdebe72127d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>方法: 長い修飾パスを持つオブジェクトに対するアクセス時間を短縮する (Visual Basic)
いくつかのメソッドとプロパティの修飾パスを必要とするオブジェクトを頻繁にアクセスする場合は、修飾パスを繰り返しなしでコードを短縮できます。  
  
 2 つの方法が修飾パスの繰り返しを避けることができます。 オブジェクトを変数に割り当てることができますかで使用できる、`With`しています.`End With`ブロックします。  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>変数に代入することで、過度に修飾されたオブジェクトにアクセスを高速化  
  
1.  頻繁にアクセスしているオブジェクトの型の変数を宣言します。 宣言の初期化の部分で修飾パスを指定します。  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  オブジェクトのメンバーにアクセスするのにには、変数を使用します。  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>With を使用して、過度に修飾されたオブジェクトにアクセスを高速化しています.End With ブロック  
  
1.  修飾パスを格納、`With`ステートメントです。  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  内のオブジェクトのメンバーへのアクセス、`With`ブロックする前に、`End With`ステートメントです。  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [With...End With ステートメント](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
