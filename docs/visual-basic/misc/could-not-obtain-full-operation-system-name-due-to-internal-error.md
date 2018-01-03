---
title: "内部エラーのために完全な運用システム名を取得できませんでした"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c67d47126718c3d90d853add61b7d06aaf84fc70
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="6118c-102">内部エラーのために完全な運用システム名を取得できませんでした</span><span class="sxs-lookup"><span data-stu-id="6118c-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="6118c-103">内部エラーのために完全な運用システム名を取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="6118c-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="6118c-104">これは、現在のコンピューターに WMI が存在しないことが原因である場合があります。</span><span class="sxs-lookup"><span data-stu-id="6118c-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="6118c-105">`My.Computer.Info.OSFullName` プロパティの呼び出しに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="6118c-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="6118c-106">このエラーの考えられる原因は、Windows Management Instrumentation (WMI) が、現在のコンピューターにインストールされていないことです。</span><span class="sxs-lookup"><span data-stu-id="6118c-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6118c-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6118c-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="6118c-108">`Try...Catch` プロパティの呼び出しの周囲に `My.Computer.Info.OSFullName` ブロックを追加します。</span><span class="sxs-lookup"><span data-stu-id="6118c-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="6118c-109">WMI およびそのインストール方法の詳細については、「Windows Management Instrumentation Core」を検索してに移動します。</span><span class="sxs-lookup"><span data-stu-id="6118c-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6118c-110">参照</span><span class="sxs-lookup"><span data-stu-id="6118c-110">See Also</span></span>  
 [<span data-ttu-id="6118c-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="6118c-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="6118c-112">例外と Visual Basic でのエラー処理</span><span class="sxs-lookup"><span data-stu-id="6118c-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="6118c-113">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="6118c-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
