---
title: 内部エラーのために完全な運用システム名を取得できませんでした
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: f85ca5f7f325cb0dd2b8fc55d3f90f6abdfd4a7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="c41ef-102">内部エラーのために完全な運用システム名を取得できませんでした</span><span class="sxs-lookup"><span data-stu-id="c41ef-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="c41ef-103">内部エラーのために完全な運用システム名を取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="c41ef-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="c41ef-104">これは、現在のコンピューターに WMI が存在しないことが原因である場合があります。</span><span class="sxs-lookup"><span data-stu-id="c41ef-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="c41ef-105">`My.Computer.Info.OSFullName` プロパティの呼び出しに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="c41ef-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="c41ef-106">このエラーの考えられる原因は、Windows Management Instrumentation (WMI) が、現在のコンピューターにインストールされていないことです。</span><span class="sxs-lookup"><span data-stu-id="c41ef-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c41ef-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c41ef-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="c41ef-108">`Try...Catch` プロパティの呼び出しの周囲に `My.Computer.Info.OSFullName` ブロックを追加します。</span><span class="sxs-lookup"><span data-stu-id="c41ef-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="c41ef-109">WMI およびそのインストール方法の詳細については、「Windows Management Instrumentation Core」を検索してに移動します。</span><span class="sxs-lookup"><span data-stu-id="c41ef-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c41ef-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c41ef-110">See Also</span></span>  
 [<span data-ttu-id="c41ef-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="c41ef-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="c41ef-112">例外と Visual Basic でのエラー処理</span><span class="sxs-lookup"><span data-stu-id="c41ef-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="c41ef-113">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="c41ef-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
