---
title: "サービス : 失敗した呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f82558bdacbc36569329764aa1639c81146d9127
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-faulted"></a><span data-ttu-id="f0284-102">サービス : 失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="f0284-102">Service: Calls Faulted</span></span>
<span data-ttu-id="f0284-103">カウンター名 : 失敗した呼び出し。</span><span class="sxs-lookup"><span data-stu-id="f0284-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f0284-104">説明</span><span class="sxs-lookup"><span data-stu-id="f0284-104">Description</span></span>  
 <span data-ttu-id="f0284-105">このサービスの呼び出しのうち、エラーとなったものの回数です。</span><span class="sxs-lookup"><span data-stu-id="f0284-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="f0284-106">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションでは、サービス メソッドは SOAP エラー メッセージを使用して操作エラー情報を通知します。</span><span class="sxs-lookup"><span data-stu-id="f0284-106">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="f0284-107">SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f0284-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="f0284-108">SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。</span><span class="sxs-lookup"><span data-stu-id="f0284-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0284-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0284-109">See Also</span></span>  
 [<span data-ttu-id="f0284-110">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="f0284-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
