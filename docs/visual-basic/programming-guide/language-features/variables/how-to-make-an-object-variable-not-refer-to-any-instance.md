---
title: "方法: オブジェクト変数がインスタンスを参照しないようにする (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b33aef06300bf35b7138ec5b40747532a77140a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="bdf8a-102">方法: オブジェクト変数がインスタンスを参照しないようにする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdf8a-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="bdf8a-103">設定するすべてのオブジェクトのインスタンスからオブジェクト変数の関連付けを解除することができます[Nothing](../../../../visual-basic/language-reference/nothing.md)です。</span><span class="sxs-lookup"><span data-stu-id="bdf8a-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="bdf8a-104">すべてのオブジェクトのインスタンスからオブジェクト変数の関連付けを解除するには</span><span class="sxs-lookup"><span data-stu-id="bdf8a-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="bdf8a-105">変数を設定`Nothing`代入ステートメントでします。</span><span class="sxs-lookup"><span data-stu-id="bdf8a-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="bdf8a-106">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="bdf8a-106">Robust Programming</span></span>  
 <span data-ttu-id="bdf8a-107">設定されているオブジェクト変数のメンバーにアクセスしようとすると、コード`Nothing`、<xref:System.NullReferenceException>に発生します。</span><span class="sxs-lookup"><span data-stu-id="bdf8a-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="bdf8a-108">オブジェクト変数を設定する場合`Nothing`多くの場合、またはのメンバー アクセスで囲むことをお勧め、変数が初期化されていませんが可能ですが場合、は、`Try...Catch...Finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="bdf8a-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bdf8a-109">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="bdf8a-109">.NET Framework Security</span></span>  
 <span data-ttu-id="bdf8a-110">機密情報や機密データを格納するオブジェクトをオブジェクト変数を使用する場合、変数に設定することができます`Nothing`ときアクティブに処理するいないとそれらのオブジェクトのいずれか。</span><span class="sxs-lookup"><span data-stu-id="bdf8a-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="bdf8a-111">これにより、データにアクセスする悪意のあるコードが発生する可能性が減少します。</span><span class="sxs-lookup"><span data-stu-id="bdf8a-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf8a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdf8a-112">See Also</span></span>  
 <xref:System.NullReferenceException>  
 [<span data-ttu-id="bdf8a-113">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="bdf8a-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="bdf8a-114">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="bdf8a-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="bdf8a-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="bdf8a-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="bdf8a-116">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="bdf8a-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="bdf8a-117">例外のトラブルシューティング : System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="bdf8a-117">Troubleshooting Exceptions: System.NullReferenceException</span></span>](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
