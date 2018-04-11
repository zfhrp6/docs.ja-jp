---
title: AddHandler ステートメント
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a><span data-ttu-id="5f832-102">AddHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="5f832-102">AddHandler Statement</span></span>
<span data-ttu-id="5f832-103">実行時にイベントをイベント ハンドラーに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="5f832-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f832-104">構文</span><span class="sxs-lookup"><span data-stu-id="5f832-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="5f832-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="5f832-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="5f832-106">処理するイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="5f832-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="5f832-107">イベントを処理するプロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="5f832-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f832-108">コメント</span><span class="sxs-lookup"><span data-stu-id="5f832-108">Remarks</span></span>  
 <span data-ttu-id="5f832-109">`AddHandler`と`RemoveHandler`ステートメントでは、開始およびプログラムの実行中にいつでもイベントの処理を停止することができます。</span><span class="sxs-lookup"><span data-stu-id="5f832-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="5f832-110">署名、`eventhandler`プロシージャは、イベントのシグネチャと一致する必要があります`event`です。</span><span class="sxs-lookup"><span data-stu-id="5f832-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="5f832-111">`Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。</span><span class="sxs-lookup"><span data-stu-id="5f832-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="5f832-112">`AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。</span><span class="sxs-lookup"><span data-stu-id="5f832-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="5f832-113">`Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="5f832-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="5f832-114">詳細については、次を参照してください。[処理](../../../visual-basic/language-reference/statements/handles-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f832-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f832-115">カスタム イベントの場合、`AddHandler`ステートメントには、イベントが呼び出される`AddHandler`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="5f832-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="5f832-116">カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f832-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f832-117">例</span><span class="sxs-lookup"><span data-stu-id="5f832-117">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5f832-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f832-118">See Also</span></span>  
 [<span data-ttu-id="5f832-119">RemoveHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="5f832-119">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="5f832-120">Handles</span><span class="sxs-lookup"><span data-stu-id="5f832-120">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="5f832-121">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="5f832-121">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="5f832-122">イベント</span><span class="sxs-lookup"><span data-stu-id="5f832-122">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
