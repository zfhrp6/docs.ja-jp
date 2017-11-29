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
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="4ccfc-102">方法: 長い修飾パスを持つオブジェクトに対するアクセス時間を短縮する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ccfc-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="4ccfc-103">いくつかのメソッドとプロパティの修飾パスを必要とするオブジェクトを頻繁にアクセスする場合は、修飾パスを繰り返しなしでコードを短縮できます。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="4ccfc-104">2 つの方法が修飾パスの繰り返しを避けることができます。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="4ccfc-105">オブジェクトを変数に割り当てることができますかで使用できる、`With`しています.`End With`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="4ccfc-106">変数に代入することで、過度に修飾されたオブジェクトにアクセスを高速化</span><span class="sxs-lookup"><span data-stu-id="4ccfc-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1.  <span data-ttu-id="4ccfc-107">頻繁にアクセスしているオブジェクトの型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="4ccfc-108">宣言の初期化の部分で修飾パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="4ccfc-109">オブジェクトのメンバーにアクセスするのにには、変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="4ccfc-110">With を使用して、過度に修飾されたオブジェクトにアクセスを高速化しています.End With ブロック</span><span class="sxs-lookup"><span data-stu-id="4ccfc-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1.  <span data-ttu-id="4ccfc-111">修飾パスを格納、`With`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="4ccfc-112">内のオブジェクトのメンバーへのアクセス、`With`ブロックする前に、`End With`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4ccfc-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4ccfc-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ccfc-113">See Also</span></span>  
 [<span data-ttu-id="4ccfc-114">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="4ccfc-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="4ccfc-115">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="4ccfc-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
