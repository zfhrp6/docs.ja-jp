---
title: "方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18f575e9bae37b66526d7b61a641374266ba627b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="18e74-102">方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="18e74-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="18e74-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスに接続して通信するには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションに、サービス アドレス、バインディング構成、およびサービス コントラクトの詳細が必要です。</span><span class="sxs-lookup"><span data-stu-id="18e74-103">To connect to and communicate with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="18e74-104">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーは通常、必要な属性型の前の登録から必要なコントラクトを取得しますが、これが適切でない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="18e74-104">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="18e74-105">登録の代わりに、モニカーは、`wsdl` パラメーターまたは Metadata Exchange を使用し、`mexAddress` パラメーターを使用することによって、WSDL (Web Services Definition Language) ドキュメントの形でコントラクトの定義を取得できます。</span><span class="sxs-lookup"><span data-stu-id="18e74-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="18e74-106">これによって、セルの値の一部が Web サービスとの対話によって計算される Excel ワークシートの配布などのシナリオが可能になります。</span><span class="sxs-lookup"><span data-stu-id="18e74-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="18e74-107">このシナリオでは、ドキュメントを開く可能性があるすべてのクライアントにサービス コントラクト アセンブリを登録することが実現できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18e74-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="18e74-108">`wsdl` パラメーターまたは `mexAddress` パラメーターによって、自己完結型のソリューションが可能になります。</span><span class="sxs-lookup"><span data-stu-id="18e74-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18e74-109">要求と応答の改ざんまたはなりすましを防止するために、相互認証を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18e74-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="18e74-110">具体的には、応答している Metadata Exchange エンドポイントが目的の信頼されたパーティであることがクライアントに対して保証されることが重要です。</span><span class="sxs-lookup"><span data-stu-id="18e74-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18e74-111">例</span><span class="sxs-lookup"><span data-stu-id="18e74-111">Example</span></span>  
 <span data-ttu-id="18e74-112">MEX コントラクトと共にサービス モニカーを使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="18e74-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="18e74-113">次のコントラクトが設定されたサービスは、wsHttpBinding で公開されます。</span><span class="sxs-lookup"><span data-stu-id="18e74-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 <span data-ttu-id="18e74-114">リモート サービスに [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを作成するとき、次の例に示すモニカーの文字列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="18e74-114">To construct a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="18e74-115">クライアント アプリケーションの実行中に、クライアントは、指定された `WS-MetadataExchange` で `mexAddress` を実行します。</span><span class="sxs-lookup"><span data-stu-id="18e74-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="18e74-116">これによって、複数のサービスのアドレス、バインディング、およびコントラクトの詳細が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18e74-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="18e74-117">`address`、`contract`、`contractNamespace`、`binding`、および `bindingNamespace` の各パラメーターは、目的のサービスを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="18e74-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="18e74-118">このパラメーターが一致した場合、モニカーは、適切なコントラクト定義を使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを作成します。これによって、型指定されたコントラクトと同様、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを使用して呼び出しを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="18e74-118">Once those parameters have been matched, the moniker constructs a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client with the appropriate contract definition and calls can then be made using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, as with the typed contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18e74-119">モニカーの形式が正しくないか、サービスを使用できない場合は、`GetObject` を呼び出すと、"構文が無効です" というエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="18e74-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="18e74-120">このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="18e74-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e74-121">参照</span><span class="sxs-lookup"><span data-stu-id="18e74-121">See Also</span></span>  
 [<span data-ttu-id="18e74-122">方法 : サービス モニカーを登録および構成する</span><span class="sxs-lookup"><span data-stu-id="18e74-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
