---
title: インスタンス
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: a95acf8e775e0802dc0ed781c562fa6373995a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473043"
---
# <a name="instances"></a><span data-ttu-id="0afd7-102">インスタンス</span><span class="sxs-lookup"><span data-stu-id="0afd7-102">Instances</span></span>
<span data-ttu-id="0afd7-103">カウンター名 : インスタンス</span><span class="sxs-lookup"><span data-stu-id="0afd7-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0afd7-104">説明</span><span class="sxs-lookup"><span data-stu-id="0afd7-104">Description</span></span>  
 <span data-ttu-id="0afd7-105">現在サービスに含まれているインスタンス コンテキストの数。</span><span class="sxs-lookup"><span data-stu-id="0afd7-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="0afd7-106">多くの場合、インスタンス コンテキストの数とインスタンスの数は同じです。</span><span class="sxs-lookup"><span data-stu-id="0afd7-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="0afd7-107">ただし、次のシナリオではこの規則は当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="0afd7-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="0afd7-108">サービス メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを明示的に呼び出している場合。</span><span class="sxs-lookup"><span data-stu-id="0afd7-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="0afd7-109"><xref:System.ServiceModel.ReleaseInstanceMode> が <xref:System.ServiceModel.OperationBehaviorAttribute> インスタンスに適用されている場合。</span><span class="sxs-lookup"><span data-stu-id="0afd7-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0afd7-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="0afd7-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
