---
title: "RemoveHandler ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82d130c6536df7d72977a028333293b4e0ee89de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="removehandler-statement"></a><span data-ttu-id="fbf06-102">RemoveHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="fbf06-102">RemoveHandler Statement</span></span>
<span data-ttu-id="fbf06-103">イベントとイベント ハンドラー間の関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="fbf06-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf06-104">構文</span><span class="sxs-lookup"><span data-stu-id="fbf06-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="fbf06-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="fbf06-105">Parts</span></span>  
  
|<span data-ttu-id="fbf06-106">用語</span><span class="sxs-lookup"><span data-stu-id="fbf06-106">Term</span></span>|<span data-ttu-id="fbf06-107">定義</span><span class="sxs-lookup"><span data-stu-id="fbf06-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="fbf06-108">処理されるイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="fbf06-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="fbf06-109">現在、イベントを処理するプロシージャの名前です。</span><span class="sxs-lookup"><span data-stu-id="fbf06-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbf06-110">コメント</span><span class="sxs-lookup"><span data-stu-id="fbf06-110">Remarks</span></span>  
 <span data-ttu-id="fbf06-111">`AddHandler`と`RemoveHandler`ステートメントでは、開始およびプログラムの実行中にいつでも、特定のイベントのイベント処理を停止することができます。</span><span class="sxs-lookup"><span data-stu-id="fbf06-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbf06-112">カスタム イベントの場合、`RemoveHandler`ステートメントには、イベントが呼び出される`RemoveHandler`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="fbf06-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="fbf06-113">カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="fbf06-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbf06-114">例</span><span class="sxs-lookup"><span data-stu-id="fbf06-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fbf06-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbf06-115">See Also</span></span>  
 [<span data-ttu-id="fbf06-116">AddHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="fbf06-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="fbf06-117">Handles</span><span class="sxs-lookup"><span data-stu-id="fbf06-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="fbf06-118">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="fbf06-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="fbf06-119">イベント</span><span class="sxs-lookup"><span data-stu-id="fbf06-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
