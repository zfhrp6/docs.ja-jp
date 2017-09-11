---
title: "AddHandler ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
dev_langs:
- VB
helpviewer_keywords:
- AddHandler statement
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
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
ms.openlocfilehash: cd821a568a35f33c722c1631eb7fbaf8f877cf4f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="addhandler-statement"></a><span data-ttu-id="5fbeb-102">AddHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="5fbeb-102">AddHandler Statement</span></span>
<span data-ttu-id="5fbeb-103">実行時にイベントをイベント ハンドラーに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fbeb-104">構文</span><span class="sxs-lookup"><span data-stu-id="5fbeb-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="5fbeb-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="5fbeb-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="5fbeb-106">処理するイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="5fbeb-107">イベントを処理するプロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fbeb-108">コメント</span><span class="sxs-lookup"><span data-stu-id="5fbeb-108">Remarks</span></span>  
 <span data-ttu-id="5fbeb-109">`AddHandler`と`RemoveHandler`ステートメントを使用すると、起動して、プログラムの実行中にいつでもイベント処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="5fbeb-110">署名、`eventhandler`プロシージャは、イベントのシグネチャと一致する必要があります`event`します。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="5fbeb-111">`Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="5fbeb-112">`AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="5fbeb-113">`Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="5fbeb-114">詳細については、次を参照してください。[処理](../../../visual-basic/language-reference/statements/handles-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fbeb-115">カスタム イベントの場合、`AddHandler`ステートメントで呼び出されるイベントの`AddHandler`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="5fbeb-116">カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="5fbeb-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fbeb-117">例</span><span class="sxs-lookup"><span data-stu-id="5fbeb-117">Example</span></span>  
 <span data-ttu-id="5fbeb-118">[!code-vb[VbVbalrEvents&17;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5fbeb-118">[!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fbeb-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fbeb-119">See Also</span></span>  
 <span data-ttu-id="5fbeb-120">[RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5fbeb-120">[RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span></span>  
<span data-ttu-id="5fbeb-121"> [ハンドル](../../../visual-basic/language-reference/statements/handles-clause.md) </span><span class="sxs-lookup"><span data-stu-id="5fbeb-121"> [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) </span></span>  
<span data-ttu-id="5fbeb-122"> [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5fbeb-122"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="5fbeb-123"> [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="5fbeb-123"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
