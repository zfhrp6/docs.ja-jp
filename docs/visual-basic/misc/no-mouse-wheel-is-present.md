---
title: "マウスのホイールが存在しません"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrMouse_NoWheelIsPresent
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 43d91abd8178f2ac00a42af2168388f2f7b94cbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="no-mouse-wheel-is-present"></a><span data-ttu-id="7b26c-102">マウスのホイールが存在しません</span><span class="sxs-lookup"><span data-stu-id="7b26c-102">No mouse wheel is present</span></span>
<span data-ttu-id="7b26c-103">`My.Computer.Mouse.WheelScrollLines` プロパティが呼び出されましたが、マウスにスクロール ホイールがありません。</span><span class="sxs-lookup"><span data-stu-id="7b26c-103">The `My.Computer.Mouse.WheelScrollLines` property was called, but the mouse has no scroll wheel.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7b26c-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7b26c-104">To correct this error</span></span>  
  
-   <span data-ttu-id="7b26c-105">`My.Computer.Mouse.WheelExists` プロパティを呼び出す前に `My.Computer.Mouse.WheelScrollLines` プロパティを調べて、マウスにスクロール ホイールがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b26c-105">Check the `My.Computer.Mouse.WheelExists` property to see if the mouse has a scroll wheel before calling the `My.Computer.Mouse.WheelScrollLines` property.</span></span>  
  
     <span data-ttu-id="7b26c-106">または</span><span class="sxs-lookup"><span data-stu-id="7b26c-106">-or-</span></span>  
  
-   <span data-ttu-id="7b26c-107">スクロール ホイールのあるマウスをコンピュータにインストールします。</span><span class="sxs-lookup"><span data-stu-id="7b26c-107">Install a mouse with a scroll wheel on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b26c-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b26c-108">See Also</span></span>  
 [<span data-ttu-id="7b26c-109">My.Computer.Mouse.WheelScrollLines プロパティ</span><span class="sxs-lookup"><span data-stu-id="7b26c-109">My.Computer.Mouse.WheelScrollLines Property</span></span>](http://msdn.microsoft.com/en-us/67600f96-25d7-4dd9-946a-b46e1fc6a57f)  
 [<span data-ttu-id="7b26c-110">My.Computer.Mouse.WheelExists プロパティ</span><span class="sxs-lookup"><span data-stu-id="7b26c-110">My.Computer.Mouse.WheelExists Property</span></span>](http://msdn.microsoft.com/en-us/332d44f7-0b66-4eaa-b4ce-d7f161bfbd07)  
 [<span data-ttu-id="7b26c-111">例外と Visual Basic でのエラー処理</span><span class="sxs-lookup"><span data-stu-id="7b26c-111">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)
