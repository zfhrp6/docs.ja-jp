---
title: "エンドポイント : 失敗した呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271e6284-9c4b-465f-b619-069e1555a5e4
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62eb1ad10c7112696d8fa2a358db4c88ee86cb3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-faulted"></a><span data-ttu-id="aad3a-102">エンドポイント : 失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="aad3a-102">Endpoint: Calls Faulted</span></span>
<span data-ttu-id="aad3a-103">カウンター名 : 失敗した呼び出し。</span><span class="sxs-lookup"><span data-stu-id="aad3a-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="aad3a-104">説明</span><span class="sxs-lookup"><span data-stu-id="aad3a-104">Description</span></span>  
 <span data-ttu-id="aad3a-105">このエンドポイントの呼び出しのうち、エラーとなったものの回数です。</span><span class="sxs-lookup"><span data-stu-id="aad3a-105">Number of calls to this endpoint that have returned faults.</span></span> <span data-ttu-id="aad3a-106">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションでは、サービス メソッドは SOAP エラー メッセージを使用して操作エラー情報を通知します。</span><span class="sxs-lookup"><span data-stu-id="aad3a-106">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="aad3a-107">SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="aad3a-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="aad3a-108">SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。</span><span class="sxs-lookup"><span data-stu-id="aad3a-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad3a-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="aad3a-109">See Also</span></span>  
 [<span data-ttu-id="aad3a-110">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="aad3a-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
