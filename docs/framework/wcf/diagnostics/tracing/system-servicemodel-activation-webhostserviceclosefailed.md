---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc2b0dc75e8e8748e25c1faf28150e0c156a20ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="edbc8-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="edbc8-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="edbc8-103">サービスが正常に閉じられず、中止された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="edbc8-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="edbc8-104">説明</span><span class="sxs-lookup"><span data-stu-id="edbc8-104">Description</span></span>  
 <span data-ttu-id="edbc8-105">このエラー コードはログ ファイルにのみ記録されます。</span><span class="sxs-lookup"><span data-stu-id="edbc8-105">This error code only appears in the log file.</span></span> <span data-ttu-id="edbc8-106">通常は、Abort を既に呼び出した後でサービスを閉じようとした場合などの、プログラミング エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="edbc8-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="edbc8-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="edbc8-107">Troubleshooting</span></span>  
 <span data-ttu-id="edbc8-108">アプリケーションのソース コードをチェックしてください。</span><span class="sxs-lookup"><span data-stu-id="edbc8-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbc8-109">参照</span><span class="sxs-lookup"><span data-stu-id="edbc8-109">See Also</span></span>  
 [<span data-ttu-id="edbc8-110">トレース</span><span class="sxs-lookup"><span data-stu-id="edbc8-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="edbc8-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="edbc8-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="edbc8-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="edbc8-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
