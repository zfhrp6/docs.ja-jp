---
title: "イベント &quot;&lt;eventname1&gt;&quot;イベントを実装できない&quot;&lt;eventname2&gt;&quot;にインターフェイス&quot;&lt;インターフェイス&gt;&quot; ため、デリゲート型の&lt;delegate1&gt;&quot;と&quot;&lt;delegate2&gt;&quot; が一致しない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
dev_langs:
- VB
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
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
ms.openlocfilehash: 340547d3673b651e988a6c1167bf7043360b04e4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="5b371-102">イベント '&lt;eventname1&gt;'イベントを実装できない'&lt;eventname2&gt;'にインターフェイス'&lt;インターフェイス&gt;' ため、デリゲート型の&lt;delegate1&gt;'と'&lt;delegate2&gt;' が一致しません。</span><span class="sxs-lookup"><span data-stu-id="5b371-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5b371-103">イベントのデリゲート型がインターフェイスでイベントのデリゲート型と一致しないために、イベントを実装することはできません。</span><span class="sxs-lookup"><span data-stu-id="5b371-103"> cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="5b371-104">このエラーは、インターフェイス内で複数のイベントを定義して、同じイベントと共にそれらを実装しようとする場合に、発生します。</span><span class="sxs-lookup"><span data-stu-id="5b371-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="5b371-105">実装されたすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定する場合にのみ、イベントは&2; つ以上のイベントを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="5b371-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="5b371-106">**エラー ID:** BC31423</span><span class="sxs-lookup"><span data-stu-id="5b371-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5b371-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5b371-107">To correct this error</span></span>  
  
-   <span data-ttu-id="5b371-108">イベントを個別に実装します。</span><span class="sxs-lookup"><span data-stu-id="5b371-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="5b371-109">または</span><span class="sxs-lookup"><span data-stu-id="5b371-109">—or—</span></span>  
  
-   <span data-ttu-id="5b371-110">インターフェイスを使用して、イベントを定義、`As`構文し、同じデリゲート型を指定します。</span><span class="sxs-lookup"><span data-stu-id="5b371-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b371-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b371-111">See Also</span></span>  
 <span data-ttu-id="5b371-112">[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5b371-112">[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="5b371-113"> [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5b371-113"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="5b371-114"> [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="5b371-114"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
