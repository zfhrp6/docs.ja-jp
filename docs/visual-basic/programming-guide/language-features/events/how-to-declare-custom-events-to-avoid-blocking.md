---
title: "方法: (Visual Basic の場合) がブロックされないようにするカスタム イベントを宣言する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
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
ms.openlocfilehash: 52181d1c307e4e312f4511719e540fd6d5bfcfa8
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="5ea2a-102">方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ea2a-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="5ea2a-103">その&1; つのイベント ハンドラーが後続のイベント ハンドラーをブロックしない重要な場合は、いくつかの状況にもあります。</span><span class="sxs-lookup"><span data-stu-id="5ea2a-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="5ea2a-104">カスタム イベントは、そのイベント ハンドラーを非同期的に呼び出すイベントを許可します。</span><span class="sxs-lookup"><span data-stu-id="5ea2a-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="5ea2a-105">既定では、イベント宣言のバッキング ストア フィールドは、すべてのイベント ハンドラーを順番に結合したマルチキャスト デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="5ea2a-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="5ea2a-106">これは、1 つのハンドラーに完了までに時間がある場合は、パラメーターを妨げる他のハンドラーが完了するまでことを意味します。</span><span class="sxs-lookup"><span data-stu-id="5ea2a-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="5ea2a-107">(正常に動作するイベント ハンドラーは、時間のかかる処理を妨げる可能性のある操作を実行する必要があることはありません) します。</span><span class="sxs-lookup"><span data-stu-id="5ea2a-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="5ea2a-108">Visual Basic ではイベントの既定の実装を使用する代わりに、イベント ハンドラーを非同期的に実行するのにカスタム イベントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ea2a-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ea2a-109">例</span><span class="sxs-lookup"><span data-stu-id="5ea2a-109">Example</span></span>  
 <span data-ttu-id="5ea2a-110">この例では、`AddHandler`アクセサーは、の各ハンドラーのデリゲートを追加、`Click`イベントを<xref:System.Collections.ArrayList>に格納されている、`EventHandlerList`フィールド</xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="5ea2a-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="5ea2a-111">コードを発生させるのと、 `Click` 、イベント、`RaiseEvent`アクセサーが非同期的を使用してすべてのイベント ハンドラーのデリゲートを呼び出す、<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>メソッド</xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>。</span><span class="sxs-lookup"><span data-stu-id="5ea2a-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="5ea2a-112">そのメソッドでは、ワーカー スレッドで各ハンドラーが呼び出され、ハンドラーは、互いをブロックできませんので、すぐに返します。</span><span class="sxs-lookup"><span data-stu-id="5ea2a-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 <span data-ttu-id="5ea2a-113">[!code-vb[VbVbalrEvents #&27;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ea2a-113">[!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea2a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ea2a-114">See Also</span></span>  
 <span data-ttu-id="5ea2a-115"><xref:System.Collections.ArrayList></xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="5ea2a-115"><xref:System.Collections.ArrayList></span></span>   
 <span data-ttu-id="5ea2a-116"><xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span><span class="sxs-lookup"><span data-stu-id="5ea2a-116"><xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span></span>   
<span data-ttu-id="5ea2a-117"> [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ea2a-117"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="5ea2a-118"> [方法: カスタム イベントを宣言してメモリを節約する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)</span><span class="sxs-lookup"><span data-stu-id="5ea2a-118"> [How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)</span></span>
