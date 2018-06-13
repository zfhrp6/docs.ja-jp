---
title: RemoveHandler ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 0d982768707948bd6c616445509e16a462b86f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597989"
---
# <a name="removehandler-statement"></a><span data-ttu-id="e2438-102">RemoveHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2438-102">RemoveHandler Statement</span></span>
<span data-ttu-id="e2438-103">イベントとイベント ハンドラー間の関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="e2438-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2438-104">構文</span><span class="sxs-lookup"><span data-stu-id="e2438-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="e2438-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="e2438-105">Parts</span></span>  
  
|<span data-ttu-id="e2438-106">用語</span><span class="sxs-lookup"><span data-stu-id="e2438-106">Term</span></span>|<span data-ttu-id="e2438-107">定義</span><span class="sxs-lookup"><span data-stu-id="e2438-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="e2438-108">処理されるイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="e2438-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="e2438-109">現在、イベントを処理するプロシージャの名前です。</span><span class="sxs-lookup"><span data-stu-id="e2438-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2438-110">コメント</span><span class="sxs-lookup"><span data-stu-id="e2438-110">Remarks</span></span>  
 <span data-ttu-id="e2438-111">`AddHandler`と`RemoveHandler`ステートメントでは、開始およびプログラムの実行中にいつでも、特定のイベントのイベント処理を停止することができます。</span><span class="sxs-lookup"><span data-stu-id="e2438-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2438-112">カスタム イベントの場合、`RemoveHandler`ステートメントには、イベントが呼び出される`RemoveHandler`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="e2438-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="e2438-113">カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="e2438-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2438-114">例</span><span class="sxs-lookup"><span data-stu-id="e2438-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e2438-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2438-115">See Also</span></span>  
 [<span data-ttu-id="e2438-116">AddHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2438-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="e2438-117">Handles</span><span class="sxs-lookup"><span data-stu-id="e2438-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="e2438-118">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2438-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="e2438-119">イベント</span><span class="sxs-lookup"><span data-stu-id="e2438-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
