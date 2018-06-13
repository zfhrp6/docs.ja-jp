---
title: 要求/応答サービス
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 8fe1343a4b3590622becf71f1167f4b19dbc67af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490946"
---
# <a name="request-reply-services"></a><span data-ttu-id="a580c-102">要求/応答サービス</span><span class="sxs-lookup"><span data-stu-id="a580c-102">Request-Reply Services</span></span>
<span data-ttu-id="a580c-103">要求/応答サービスは、操作コントラクトでは、Windows Communication Foundation (WCF) の既定の種類です。</span><span class="sxs-lookup"><span data-stu-id="a580c-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a580c-104">クライアントはサービス操作を呼び出し、サービスからの応答を待機します。</span><span class="sxs-lookup"><span data-stu-id="a580c-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="a580c-105">サービス操作の呼び出しは、同期的または非同期的に実行できます。同期呼び出しでは、応答を受信するか、呼び出しがタイムアウトするまで、クライアントがブロックされます。非同期呼び出しでは、クライアントはサービス操作の呼び出し後、動作を続行し、別のスレッドのサービスからの応答を受信できます。</span><span class="sxs-lookup"><span data-stu-id="a580c-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="a580c-106">要求/応答サービス コントラクトを作成するには、サービス コントラクトを定義し、次のサンプル コードに示すように <xref:System.ServiceModel.OperationContractAttribute> クラスを各操作に適用します。</span><span class="sxs-lookup"><span data-stu-id="a580c-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="a580c-107">これは既定の動作であるため、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティを `false` に設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a580c-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a580c-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="a580c-108">See Also</span></span>  
 [<span data-ttu-id="a580c-109">一方向サービス</span><span class="sxs-lookup"><span data-stu-id="a580c-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [<span data-ttu-id="a580c-110">双方向サービス</span><span class="sxs-lookup"><span data-stu-id="a580c-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
