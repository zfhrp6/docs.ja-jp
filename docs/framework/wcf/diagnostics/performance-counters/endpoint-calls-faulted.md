---
title: 'エンドポイント : 失敗した呼び出し'
ms.date: 03/30/2017
ms.assetid: 271e6284-9c4b-465f-b619-069e1555a5e4
ms.openlocfilehash: 126ba1b4bd2cc16d62460f198a69194fe4652a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-calls-faulted"></a><span data-ttu-id="292ac-102">エンドポイント : 失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="292ac-102">Endpoint: Calls Faulted</span></span>
<span data-ttu-id="292ac-103">カウンター名 : 失敗した呼び出し。</span><span class="sxs-lookup"><span data-stu-id="292ac-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="292ac-104">説明</span><span class="sxs-lookup"><span data-stu-id="292ac-104">Description</span></span>  
 <span data-ttu-id="292ac-105">このエンドポイントの呼び出しのうち、エラーとなったものの回数です。</span><span class="sxs-lookup"><span data-stu-id="292ac-105">Number of calls to this endpoint that have returned faults.</span></span> <span data-ttu-id="292ac-106">Windows Communication Foundation (WCF) アプリケーションでは、サービス メソッドは、SOAP エラー メッセージを使用して、処理のエラー情報を通信します。</span><span class="sxs-lookup"><span data-stu-id="292ac-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="292ac-107">SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="292ac-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="292ac-108">SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。</span><span class="sxs-lookup"><span data-stu-id="292ac-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292ac-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="292ac-109">See Also</span></span>  
 [<span data-ttu-id="292ac-110">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="292ac-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
