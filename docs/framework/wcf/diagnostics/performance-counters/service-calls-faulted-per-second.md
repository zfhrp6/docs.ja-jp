---
title: "サービス : 1 秒あたりの失敗した呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5cf587102814c5bbd2a9c22d88db90f48fbf4da1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="0cce8-102">サービス : 1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="0cce8-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="0cce8-103">カウンター名 : 1 秒あたりの失敗した呼び出し。</span><span class="sxs-lookup"><span data-stu-id="0cce8-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0cce8-104">説明</span><span class="sxs-lookup"><span data-stu-id="0cce8-104">Description</span></span>  
 <span data-ttu-id="0cce8-105">このサービスの呼び出しのうち、エラーを返したものの 1 秒あたりの回数です。</span><span class="sxs-lookup"><span data-stu-id="0cce8-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="0cce8-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="0cce8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0cce8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="0cce8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="0cce8-108">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションでは、サービス メソッドは SOAP エラー メッセージを使用して操作エラー情報を通知します。</span><span class="sxs-lookup"><span data-stu-id="0cce8-108">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="0cce8-109">SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0cce8-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="0cce8-110">SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。</span><span class="sxs-lookup"><span data-stu-id="0cce8-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cce8-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cce8-111">See Also</span></span>  
 [<span data-ttu-id="0cce8-112">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="0cce8-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
