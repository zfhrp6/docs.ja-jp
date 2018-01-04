---
title: "インスタンス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ed0c4a6f13ddcafdb3a9a773be9cd3f017474ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="instances"></a><span data-ttu-id="b2a81-102">インスタンス</span><span class="sxs-lookup"><span data-stu-id="b2a81-102">Instances</span></span>
<span data-ttu-id="b2a81-103">カウンター名 : インスタンス</span><span class="sxs-lookup"><span data-stu-id="b2a81-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b2a81-104">説明</span><span class="sxs-lookup"><span data-stu-id="b2a81-104">Description</span></span>  
 <span data-ttu-id="b2a81-105">現在サービスに含まれているインスタンス コンテキストの数。</span><span class="sxs-lookup"><span data-stu-id="b2a81-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="b2a81-106">多くの場合、インスタンス コンテキストの数とインスタンスの数は同じです。</span><span class="sxs-lookup"><span data-stu-id="b2a81-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="b2a81-107">ただし、次のシナリオではこの規則は当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="b2a81-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="b2a81-108">サービス メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを明示的に呼び出している場合。</span><span class="sxs-lookup"><span data-stu-id="b2a81-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="b2a81-109"><xref:System.ServiceModel.ReleaseInstanceMode> が <xref:System.ServiceModel.OperationBehaviorAttribute> インスタンスに適用されている場合。</span><span class="sxs-lookup"><span data-stu-id="b2a81-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a81-110">参照</span><span class="sxs-lookup"><span data-stu-id="b2a81-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
