---
title: "方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a36c855efb67752674615a61f2fa701974ce5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="455f1-102">方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="455f1-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="455f1-103">いくつかのような場合があるその 1 つのイベント ハンドラーが後続のイベント ハンドラーをブロックしない必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="455f1-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="455f1-104">カスタム イベントは、そのイベント ハンドラーを非同期的に呼び出すイベントを許可します。</span><span class="sxs-lookup"><span data-stu-id="455f1-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="455f1-105">既定では、イベント宣言のバッキング ストア フィールドは、すべてのイベント ハンドラーを順番に結合したマルチキャスト デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="455f1-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="455f1-106">つまり、1 つのハンドラーでは、完了に時間がかかる場合、ブロック、他のハンドラーが完了するまでです。</span><span class="sxs-lookup"><span data-stu-id="455f1-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="455f1-107">(正常に動作するイベント ハンドラーは、時間のかかるまたはブロックしている可能性がある操作を実行する必要があることはありません)。</span><span class="sxs-lookup"><span data-stu-id="455f1-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="455f1-108">Visual Basic が提供するイベントの既定の実装を使用する代わりに、イベント ハンドラーを非同期的に実行するのにカスタム イベントを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="455f1-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="455f1-109">例</span><span class="sxs-lookup"><span data-stu-id="455f1-109">Example</span></span>  
 <span data-ttu-id="455f1-110">この例では、`AddHandler`アクセサーは、の各ハンドラーのデリゲートを追加、`Click`イベントを<xref:System.Collections.ArrayList>に格納されている、`EventHandlerList`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="455f1-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="455f1-111">ときにコードが発生し、`Click`イベント、`RaiseEvent`アクセサーが非同期的を使用してすべてのイベント ハンドラーのデリゲートを呼び出す、<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="455f1-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="455f1-112">そのメソッドでは、ワーカー スレッドで各ハンドラーが呼び出され、ハンドラーが互いをブロックできませんので、すぐに返します。</span><span class="sxs-lookup"><span data-stu-id="455f1-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="455f1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="455f1-113">See Also</span></span>  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [<span data-ttu-id="455f1-114">イベント</span><span class="sxs-lookup"><span data-stu-id="455f1-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="455f1-115">方法: カスタム イベントを宣言してメモリを節約する</span><span class="sxs-lookup"><span data-stu-id="455f1-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
