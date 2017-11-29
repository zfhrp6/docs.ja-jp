---
title: "方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)"
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
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eec9a2fc687f481ab40313e35cbde81c25b81ae8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="feaff-102">方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feaff-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="feaff-103">いくつかのような場合があること、アプリケーションのメモリ使用量を低く抑える必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="feaff-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="feaff-104">カスタム イベントでは、アプリケーションが、処理するイベントに対してだけメモリを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="feaff-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="feaff-105">既定では、クラスは、イベントを宣言すると、コンパイラは、イベント情報を格納するフィールドのメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="feaff-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="feaff-106">場合は、クラスには未使用のイベントが多く、不必要にメモリを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="feaff-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="feaff-107">Visual Basic が提供するイベントの既定の実装を使用する代わりに、メモリ使用量をより慎重に管理するのにカスタム イベントを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="feaff-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feaff-108">例</span><span class="sxs-lookup"><span data-stu-id="feaff-108">Example</span></span>  
 <span data-ttu-id="feaff-109">この例では 1 つのインスタンスを使用するクラス、<xref:System.ComponentModel.EventHandlerList>で格納されているクラス、`Events`使用中のイベントに関する情報を格納するためのフィールドです。</span><span class="sxs-lookup"><span data-stu-id="feaff-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="feaff-110"><xref:System.ComponentModel.EventHandlerList>クラスは、最適化された一覧クラスにデリゲートを保持するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="feaff-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="feaff-111">クラスの使用中のすべてのイベント、`Events`どのような方法で各イベントが処理を追跡するフィールドです。</span><span class="sxs-lookup"><span data-stu-id="feaff-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="feaff-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="feaff-112">See Also</span></span>  
 <xref:System.ComponentModel.EventHandlerList>  
 [<span data-ttu-id="feaff-113">イベント</span><span class="sxs-lookup"><span data-stu-id="feaff-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="feaff-114">方法: カスタム イベントを宣言してブロックを回避する</span><span class="sxs-lookup"><span data-stu-id="feaff-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
