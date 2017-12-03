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
ms.openlocfilehash: 87423c3de551cb9fbf8c5a7756e2f0f999129a3b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="instances"></a><span data-ttu-id="6d857-102">インスタンス</span><span class="sxs-lookup"><span data-stu-id="6d857-102">Instances</span></span>
<span data-ttu-id="6d857-103">カウンター名 : インスタンス</span><span class="sxs-lookup"><span data-stu-id="6d857-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6d857-104">説明</span><span class="sxs-lookup"><span data-stu-id="6d857-104">Description</span></span>  
 <span data-ttu-id="6d857-105">現在サービスに含まれているインスタンス コンテキストの数。</span><span class="sxs-lookup"><span data-stu-id="6d857-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="6d857-106">多くの場合、インスタンス コンテキストの数とインスタンスの数は同じです。</span><span class="sxs-lookup"><span data-stu-id="6d857-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="6d857-107">ただし、次のシナリオではこの規則は当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="6d857-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="6d857-108">サービス メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを明示的に呼び出している場合。</span><span class="sxs-lookup"><span data-stu-id="6d857-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="6d857-109"><xref:System.ServiceModel.ReleaseInstanceMode> が <xref:System.ServiceModel.OperationBehaviorAttribute> インスタンスに適用されている場合。</span><span class="sxs-lookup"><span data-stu-id="6d857-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d857-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d857-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
