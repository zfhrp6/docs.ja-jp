---
title: "ラムダ式は、このイベント ハンドラーからは削除されません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42326
- vbc42326
dev_langs:
- VB
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7afe8160a25130cd92722df527d9567192912292
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="dd4d0-102">ラムダ式はこのイベント ハンドラーから削除されません</span><span class="sxs-lookup"><span data-stu-id="dd4d0-102">Lambda expression will not be removed from this event handler</span></span>
<span data-ttu-id="dd4d0-103">ラムダ式はこのイベント ハンドラーから削除されません。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="dd4d0-104">ラムダ式を変数に代入し、変数を使用して追加し、イベントを削除します。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>  
  
 <span data-ttu-id="dd4d0-105">イベント ハンドラーにラムダ式を使用している場合は、意図した動作が見えない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="dd4d0-106">コンパイラは、同一である場合でも、各ラムダ式の定義用の新しいメソッドを生成します。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="dd4d0-107">そのため、次のコードが表示されます`False`します。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-107">Therefore, the following code displays `False`.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1  
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1  
        Console.WriteLine(fun1 = fun2)  
    End Sub  
  
    Delegate Function ChangeInteger(ByVal x As Integer) As Integer  
  
End Module  
```  
  
 <span data-ttu-id="dd4d0-108">イベント ハンドラーにラムダ式を使用している場合、予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="dd4d0-109">次の例では、ラムダ式で追加`AddHandler`では削除されませんが、`RemoveHandler`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Sub Main()  
  
        ' The following line adds one listener to the event.  
        AddHandler ProcessInteger, Function(m As Integer) m  
  
        ' The following statement searches the current listeners   
        ' for a match to remove. However, this lambda is not the same  
        ' as the previous one, so nothing is removed.  
        RemoveHandler ProcessInteger, Function(m As Integer) m  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="dd4d0-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-110">By default, this message is a warning.</span></span> <span data-ttu-id="dd4d0-111">警告を非表示または警告をエラーとして処理する方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="dd4d0-112">**エラー ID:** BC42326</span><span class="sxs-lookup"><span data-stu-id="dd4d0-112">**Error ID:** BC42326</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dd4d0-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="dd4d0-113">To correct this error</span></span>  
  
-   <span data-ttu-id="dd4d0-114">警告を回避し、ラムダ式を削除するラムダ式を変数に代入し、両方で、変数を使用して、`AddHandler`と`RemoveHandler`ステートメントは、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Dim PrintHandler As ProcessIntegerEventHandler  
  
    Sub Main()  
  
        ' Assign the lambda expression to a variable.  
        PrintHandler = Function(m As Integer) m  
  
        ' Use the variable to add the listener.  
        AddHandler ProcessInteger, PrintHandler  
  
        ' Use the variable again when you want to remove the listener.  
        RemoveHandler ProcessInteger, PrintHandler  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd4d0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd4d0-115">See Also</span></span>  
 <span data-ttu-id="dd4d0-116">[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="dd4d0-116">[Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="dd4d0-117"> [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md) </span><span class="sxs-lookup"><span data-stu-id="dd4d0-117"> [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md) </span></span>  
<span data-ttu-id="dd4d0-118"> [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="dd4d0-118"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
