---
title: "RemoveHandler ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
dev_langs:
- VB
helpviewer_keywords:
- RemoveHandler keyword
- RemoveHandler statement
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
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
ms.openlocfilehash: 6e614a1dce4894dcd18509854f3cae149665cbf0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="removehandler-statement"></a><span data-ttu-id="cdcd3-102">RemoveHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="cdcd3-102">RemoveHandler Statement</span></span>
<span data-ttu-id="cdcd3-103">イベントとイベント ハンドラーの間の関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="cdcd3-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdcd3-104">構文</span><span class="sxs-lookup"><span data-stu-id="cdcd3-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="cdcd3-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="cdcd3-105">Parts</span></span>  
  
|<span data-ttu-id="cdcd3-106">用語</span><span class="sxs-lookup"><span data-stu-id="cdcd3-106">Term</span></span>|<span data-ttu-id="cdcd3-107">定義</span><span class="sxs-lookup"><span data-stu-id="cdcd3-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="cdcd3-108">処理されるイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="cdcd3-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="cdcd3-109">現在、イベントを処理するプロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="cdcd3-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdcd3-110">コメント</span><span class="sxs-lookup"><span data-stu-id="cdcd3-110">Remarks</span></span>  
 <span data-ttu-id="cdcd3-111">`AddHandler`と`RemoveHandler`ステートメントを使用すると、起動して、プログラムの実行中にいつでも、特定のイベントのイベント処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="cdcd3-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdcd3-112">カスタム イベントの場合、`RemoveHandler`ステートメントで呼び出されるイベントの`RemoveHandler`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="cdcd3-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="cdcd3-113">カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="cdcd3-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdcd3-114">例</span><span class="sxs-lookup"><span data-stu-id="cdcd3-114">Example</span></span>  
 <span data-ttu-id="cdcd3-115">[!code-vb[VbVbalrEvents&17;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cdcd3-115">[!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdcd3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdcd3-116">See Also</span></span>  
 <span data-ttu-id="cdcd3-117">[AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cdcd3-117">[AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span></span>  
<span data-ttu-id="cdcd3-118"> [ハンドル](../../../visual-basic/language-reference/statements/handles-clause.md) </span><span class="sxs-lookup"><span data-stu-id="cdcd3-118"> [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) </span></span>  
<span data-ttu-id="cdcd3-119"> [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cdcd3-119"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="cdcd3-120"> [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="cdcd3-120"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
