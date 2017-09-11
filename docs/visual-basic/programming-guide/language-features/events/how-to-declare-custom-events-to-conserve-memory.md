---
title: "方法: (Visual Basic) のメモリを節約するためにカスタム イベントを宣言する |Microsoft ドキュメント"
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
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: 11
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
ms.openlocfilehash: 130cbda875d6a56f826aefea341d233ea4b3731d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="91af8-102">方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91af8-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="91af8-103">いくつかのような場合があること、アプリケーションのメモリ使用量を低く抑える必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="91af8-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="91af8-104">カスタム イベントを使うアプリケーションが、処理するイベントに対してだけメモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="91af8-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="91af8-105">既定では、クラスは、イベントを宣言すると、コンパイラは、イベント情報を格納するフィールドのメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="91af8-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="91af8-106">クラスの未使用のイベントが多くの場合、不要なメモリを消費します。</span><span class="sxs-lookup"><span data-stu-id="91af8-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="91af8-107">Visual Basic ではイベントの既定の実装を使用する代わりに、メモリ使用量をより注意深く管理するのにカスタム イベントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="91af8-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91af8-108">例</span><span class="sxs-lookup"><span data-stu-id="91af8-108">Example</span></span>  
 <span data-ttu-id="91af8-109">この例では、クラスが&1; つのインスタンスを使用して、<xref:System.ComponentModel.EventHandlerList>に格納されているクラス、`Events`使用中のイベントに関する情報を格納するためのフィールド</xref:System.ComponentModel.EventHandlerList>。</span><span class="sxs-lookup"><span data-stu-id="91af8-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="91af8-110"><xref:System.ComponentModel.EventHandlerList>クラスは、最適化されたリスト クラスのデリゲートを保持するために設計されています</xref:System.ComponentModel.EventHandlerList>。</span><span class="sxs-lookup"><span data-stu-id="91af8-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="91af8-111">クラス使用中のすべてのイベント、`Events`どのような方法には、各イベントが処理を追跡するフィールドです。</span><span class="sxs-lookup"><span data-stu-id="91af8-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 <span data-ttu-id="91af8-112">[!code-vb[VbVbalrEvents #&22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="91af8-112">[!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91af8-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="91af8-113">See Also</span></span>  
 <span data-ttu-id="91af8-114"><xref:System.ComponentModel.EventHandlerList></xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="91af8-114"><xref:System.ComponentModel.EventHandlerList></span></span>   
<span data-ttu-id="91af8-115"> [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="91af8-115"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="91af8-116"> [方法: カスタム イベントを宣言してブロックを回避する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)</span><span class="sxs-lookup"><span data-stu-id="91af8-116"> [How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)</span></span>
