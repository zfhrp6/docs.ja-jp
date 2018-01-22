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
ms.openlocfilehash: 7caf2e24bcbd86ad2b6175d593bd218a9bb4689d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="no-mouse-wheel-is-present"></a><span data-ttu-id="fffb6-102">マウスのホイールが存在しません</span><span class="sxs-lookup"><span data-stu-id="fffb6-102">No mouse wheel is present</span></span>
<span data-ttu-id="fffb6-103">`My.Computer.Mouse.WheelScrollLines` プロパティが呼び出されましたが、マウスにスクロール ホイールがありません。</span><span class="sxs-lookup"><span data-stu-id="fffb6-103">The `My.Computer.Mouse.WheelScrollLines` property was called, but the mouse has no scroll wheel.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fffb6-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="fffb6-104">To correct this error</span></span>  
  
-   <span data-ttu-id="fffb6-105">`My.Computer.Mouse.WheelExists` プロパティを呼び出す前に `My.Computer.Mouse.WheelScrollLines` プロパティを調べて、マウスにスクロール ホイールがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fffb6-105">Check the `My.Computer.Mouse.WheelExists` property to see if the mouse has a scroll wheel before calling the `My.Computer.Mouse.WheelScrollLines` property.</span></span>  
  
     <span data-ttu-id="fffb6-106">- または -</span><span class="sxs-lookup"><span data-stu-id="fffb6-106">-or-</span></span>  
  
-   <span data-ttu-id="fffb6-107">スクロール ホイールのあるマウスをコンピュータにインストールします。</span><span class="sxs-lookup"><span data-stu-id="fffb6-107">Install a mouse with a scroll wheel on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffb6-108">参照</span><span class="sxs-lookup"><span data-stu-id="fffb6-108">See Also</span></span>  
 [<span data-ttu-id="fffb6-109">My.Computer.Mouse.WheelScrollLines</span><span class="sxs-lookup"><span data-stu-id="fffb6-109">My.Computer.Mouse.WheelScrollLines</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelScrollLines)  
 [<span data-ttu-id="fffb6-110">My.Computer.Mouse.WheelExists</span><span class="sxs-lookup"><span data-stu-id="fffb6-110">My.Computer.Mouse.WheelExists</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelExists)  
 [<span data-ttu-id="fffb6-111">例外と Visual Basic でのエラー処理</span><span class="sxs-lookup"><span data-stu-id="fffb6-111">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)
