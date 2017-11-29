---
title: "&#39;です。&lt;eventname&gt;&#39; は、イベントで、直接呼び出すことができません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords: BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb987c957a28aa37c40ad975b945c20da4690f6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="91e42-102">&#39;です。&lt;eventname&gt;&#39; は、イベントで、直接呼び出すことができません</span><span class="sxs-lookup"><span data-stu-id="91e42-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="91e42-103">' <`eventname`>' は、イベントで、これは直接呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="91e42-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="91e42-104">使用して、`RaiseEvent`イベントを発生させるステートメントです。</span><span class="sxs-lookup"><span data-stu-id="91e42-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="91e42-105">プロシージャ呼び出しでは、プロシージャの名前のイベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="91e42-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="91e42-106">イベント ハンドラーは、プロシージャが、イベント自体シグナリング デバイス、発生および処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91e42-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="91e42-107">**エラー ID:** BC32022</span><span class="sxs-lookup"><span data-stu-id="91e42-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="91e42-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="91e42-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="91e42-109">使用して、`RaiseEvent`イベントを通知し、それを処理する手順を起動するステートメント。</span><span class="sxs-lookup"><span data-stu-id="91e42-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e42-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="91e42-110">See Also</span></span>  
 [<span data-ttu-id="91e42-111">RaiseEvent ステートメント</span><span class="sxs-lookup"><span data-stu-id="91e42-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
