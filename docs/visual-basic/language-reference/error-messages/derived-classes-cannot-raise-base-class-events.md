---
title: 派生クラスで基本クラスのイベントを発生させることはできません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="87c3e-102">派生クラスで基本クラスのイベントを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="87c3e-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="87c3e-103">宣言されている宣言領域からのみイベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="87c3e-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="87c3e-104">そのため、クラスは、その他のクラス、1 つでも派生元からイベントを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="87c3e-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="87c3e-105">**エラー ID:** BC30029</span><span class="sxs-lookup"><span data-stu-id="87c3e-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="87c3e-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="87c3e-106">To correct this error</span></span>  
  
-   <span data-ttu-id="87c3e-107">移動、`Event`ステートメントまたは`RaiseEvent`もように、同じクラス内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="87c3e-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c3e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="87c3e-108">See Also</span></span>  
 [<span data-ttu-id="87c3e-109">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="87c3e-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="87c3e-110">RaiseEvent ステートメント</span><span class="sxs-lookup"><span data-stu-id="87c3e-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
