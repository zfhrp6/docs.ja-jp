---
title: "エンドポイント : 1 秒あたりの失敗した呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f52a0f0b44a788bd5c2d34c125e31884c2a9afb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="82544-102">エンドポイント : 1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="82544-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="82544-103">カウンター名 : 1 秒あたりの失敗した呼び出し。</span><span class="sxs-lookup"><span data-stu-id="82544-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="82544-104">説明</span><span class="sxs-lookup"><span data-stu-id="82544-104">Description</span></span>  
 <span data-ttu-id="82544-105">このエンドポイントの呼び出しのうち、エラーを返したものの 1 秒あたりの回数です。</span><span class="sxs-lookup"><span data-stu-id="82544-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="82544-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="82544-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="82544-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="82544-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="82544-108">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションでは、サービス メソッドは SOAP エラー メッセージを使用して操作エラー情報を通知します。</span><span class="sxs-lookup"><span data-stu-id="82544-108">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="82544-109">SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="82544-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="82544-110">SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。</span><span class="sxs-lookup"><span data-stu-id="82544-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82544-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="82544-111">See Also</span></span>  
 [<span data-ttu-id="82544-112">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="82544-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
