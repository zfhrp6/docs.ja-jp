---
title: イベント&#39; &lt;eventname1&gt; &#39;イベントを実装できません&#39; &lt;eventname2&gt; &#39;インターフェイスで&#39;&lt;インターフェイス&gt;&#39;ため。デリゲート型&#39; &lt;delegate1&gt; &#39;と&#39; &lt;delegate2&gt; &#39;が一致しません
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 41f5984458eb17db04f20b292a0d80783093dcb4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="cc30e-102">イベント&#39; &lt;eventname1&gt; &#39;イベントを実装できません&#39; &lt;eventname2&gt; &#39;インターフェイスで&#39;&lt;インターフェイス&gt;&#39;ため。デリゲート型&#39; &lt;delegate1&gt; &#39;と&#39; &lt;delegate2&gt; &#39;が一致しません</span><span class="sxs-lookup"><span data-stu-id="cc30e-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
<span data-ttu-id="cc30e-103">イベントのデリゲート型がインターフェイスでイベントのデリゲート型と一致しないために、Visual Basic では、イベントを実装できません。</span><span class="sxs-lookup"><span data-stu-id="cc30e-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="cc30e-104">このエラーは、インターフェイス内で複数のイベントを定義して、同じイベントと共にそれらを実装しようとする場合に、発生します。</span><span class="sxs-lookup"><span data-stu-id="cc30e-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="cc30e-105">実装されたすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定する場合にのみ、イベントは 2 つ以上のイベントを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="cc30e-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="cc30e-106">**エラー ID:** BC31423</span><span class="sxs-lookup"><span data-stu-id="cc30e-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc30e-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="cc30e-107">To correct this error</span></span>  
  
-   <span data-ttu-id="cc30e-108">イベントを個別に実装します。</span><span class="sxs-lookup"><span data-stu-id="cc30e-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="cc30e-109">または</span><span class="sxs-lookup"><span data-stu-id="cc30e-109">—or—</span></span>  
  
-   <span data-ttu-id="cc30e-110">インターフェイスを使用して、イベントを定義、`As`構文と同じデリゲート型を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc30e-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc30e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc30e-111">See Also</span></span>  
 [<span data-ttu-id="cc30e-112">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="cc30e-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="cc30e-113">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="cc30e-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="cc30e-114">イベント</span><span class="sxs-lookup"><span data-stu-id="cc30e-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
