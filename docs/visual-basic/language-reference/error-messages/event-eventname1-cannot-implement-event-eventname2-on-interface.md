---
title: "イベント &#39;&lt;eventname1&gt;&#39; を実装できませんイベント &#39;&lt; 。eventname2&gt;&#39;インターフェイス &#39; 上の;&lt;インターフェイス&gt;&#39;のためですデリゲート型 &#39;&lt; 。delegate1&gt;&#39; と &#39;&lt;delegate2&gt;&#39; が一致しません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords: BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0fcbbf8a6e23270e4dcbf9d813c773e1522a92a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="9b57c-102">イベント &#39;&lt;eventname1&gt;&#39; を実装できませんイベント &#39;&lt; 。eventname2&gt;&#39;インターフェイス &#39; 上の;&lt;インターフェイス&gt;&#39;のためですデリゲート型 &#39;&lt; 。delegate1&gt;&#39; と &#39;&lt;delegate2&gt;&#39; が一致しません</span><span class="sxs-lookup"><span data-stu-id="9b57c-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="9b57c-103">イベントのデリゲート型がインターフェイスでイベントのデリゲート型と一致しないために、イベントを実装することはできません。</span><span class="sxs-lookup"><span data-stu-id="9b57c-103"> cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="9b57c-104">このエラーは、インターフェイス内で複数のイベントを定義して、同じイベントと共にそれらを実装しようとする場合に、発生します。</span><span class="sxs-lookup"><span data-stu-id="9b57c-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="9b57c-105">実装されたすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定する場合にのみ、イベントは 2 つ以上のイベントを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="9b57c-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="9b57c-106">**エラー ID:** BC31423</span><span class="sxs-lookup"><span data-stu-id="9b57c-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9b57c-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9b57c-107">To correct this error</span></span>  
  
-   <span data-ttu-id="9b57c-108">イベントを個別に実装します。</span><span class="sxs-lookup"><span data-stu-id="9b57c-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="9b57c-109">または</span><span class="sxs-lookup"><span data-stu-id="9b57c-109">—or—</span></span>  
  
-   <span data-ttu-id="9b57c-110">インターフェイスを使用して、イベントを定義、`As`構文と同じデリゲート型を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b57c-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b57c-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b57c-111">See Also</span></span>  
 [<span data-ttu-id="9b57c-112">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b57c-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="9b57c-113">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b57c-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="9b57c-114">イベント</span><span class="sxs-lookup"><span data-stu-id="9b57c-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
