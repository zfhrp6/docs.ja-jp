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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23182f18f28cfb843c1c3a70996590a92d9cdea8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="instances"></a><span data-ttu-id="69b5b-102">インスタンス</span><span class="sxs-lookup"><span data-stu-id="69b5b-102">Instances</span></span>
<span data-ttu-id="69b5b-103">カウンター名 : インスタンス</span><span class="sxs-lookup"><span data-stu-id="69b5b-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="69b5b-104">説明</span><span class="sxs-lookup"><span data-stu-id="69b5b-104">Description</span></span>  
 <span data-ttu-id="69b5b-105">現在サービスに含まれているインスタンス コンテキストの数。</span><span class="sxs-lookup"><span data-stu-id="69b5b-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="69b5b-106">多くの場合、インスタンス コンテキストの数とインスタンスの数は同じです。</span><span class="sxs-lookup"><span data-stu-id="69b5b-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="69b5b-107">ただし、次のシナリオではこの規則は当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="69b5b-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="69b5b-108">サービス メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを明示的に呼び出している場合。</span><span class="sxs-lookup"><span data-stu-id="69b5b-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="69b5b-109"><xref:System.ServiceModel.ReleaseInstanceMode> が <xref:System.ServiceModel.OperationBehaviorAttribute> インスタンスに適用されている場合。</span><span class="sxs-lookup"><span data-stu-id="69b5b-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b5b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="69b5b-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
