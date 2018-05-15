---
title: '方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: d19c91d66e458ca2317dc049d517b92fa7406ef6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="da64c-102">方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da64c-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="da64c-103">いくつかのような場合があること、アプリケーションのメモリ使用量を低く抑える必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="da64c-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="da64c-104">カスタム イベントでは、アプリケーションが、処理するイベントに対してだけメモリを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="da64c-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="da64c-105">既定では、クラスは、イベントを宣言すると、コンパイラは、イベント情報を格納するフィールドのメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="da64c-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="da64c-106">場合は、クラスには未使用のイベントが多く、不必要にメモリを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="da64c-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="da64c-107">Visual Basic が提供するイベントの既定の実装を使用する代わりに、メモリ使用量をより慎重に管理するのにカスタム イベントを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="da64c-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da64c-108">例</span><span class="sxs-lookup"><span data-stu-id="da64c-108">Example</span></span>  
 <span data-ttu-id="da64c-109">この例では 1 つのインスタンスを使用するクラス、<xref:System.ComponentModel.EventHandlerList>で格納されているクラス、`Events`使用中のイベントに関する情報を格納するためのフィールドです。</span><span class="sxs-lookup"><span data-stu-id="da64c-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="da64c-110"><xref:System.ComponentModel.EventHandlerList>クラスは、最適化された一覧クラスにデリゲートを保持するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="da64c-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="da64c-111">クラスの使用中のすべてのイベント、`Events`どのような方法で各イベントが処理を追跡するフィールドです。</span><span class="sxs-lookup"><span data-stu-id="da64c-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="da64c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="da64c-112">See Also</span></span>  
 <xref:System.ComponentModel.EventHandlerList>  
 [<span data-ttu-id="da64c-113">イベント</span><span class="sxs-lookup"><span data-stu-id="da64c-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="da64c-114">方法: カスタム イベントを宣言してブロックを回避する</span><span class="sxs-lookup"><span data-stu-id="da64c-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
