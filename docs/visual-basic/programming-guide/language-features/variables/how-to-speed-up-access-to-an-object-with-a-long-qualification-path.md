---
title: '方法: 長い修飾パスを持つオブジェクトに対するアクセス時間を短縮する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: d52d13feb0f85065c0623b5937f558b841c036dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650200"
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
