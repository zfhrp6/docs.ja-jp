---
title: "セキュリティで保護されていないイントラネットのクライアントとサービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
caps.latest.revision: "20"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 0cfd98d401921c47bd85f8d4089e3efb437ca6b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="ca40d-102">セキュリティで保護されていないイントラネットのクライアントとサービス</span><span class="sxs-lookup"><span data-stu-id="ca40d-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="ca40d-103">次の図は、セキュリティで保護されたプライベート ネットワーク上で [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションに情報を提供するために開発された単純な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを示しています。</span><span class="sxs-lookup"><span data-stu-id="ca40d-103">The following illustration depicts a simple [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service developed to provide information on a secure private network to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="ca40d-104">データの重要性が低いか、ネットワークが本質的に安全であることが期待されるか、または [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャよりも下位層でセキュリティが提供されているため、セキュリティは必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="ca40d-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure.</span></span>  
  
 <span data-ttu-id="ca40d-105">![イントラネットのセキュリティ保護されていないクライアントとサービスのシナリオ](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="ca40d-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="ca40d-106">特徴</span><span class="sxs-lookup"><span data-stu-id="ca40d-106">Characteristic</span></span>|<span data-ttu-id="ca40d-107">説明</span><span class="sxs-lookup"><span data-stu-id="ca40d-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ca40d-108">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="ca40d-108">Security Mode</span></span>|<span data-ttu-id="ca40d-109">なし</span><span class="sxs-lookup"><span data-stu-id="ca40d-109">None</span></span>|  
|<span data-ttu-id="ca40d-110">Transport</span><span class="sxs-lookup"><span data-stu-id="ca40d-110">Transport</span></span>|<span data-ttu-id="ca40d-111">TCP</span><span class="sxs-lookup"><span data-stu-id="ca40d-111">TCP</span></span>|  
|<span data-ttu-id="ca40d-112">バインディング</span><span class="sxs-lookup"><span data-stu-id="ca40d-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="ca40d-113">相互運用性</span><span class="sxs-lookup"><span data-stu-id="ca40d-113">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ca40d-114"> のみ</span><span class="sxs-lookup"><span data-stu-id="ca40d-114"> only</span></span>|  
|<span data-ttu-id="ca40d-115">認証</span><span class="sxs-lookup"><span data-stu-id="ca40d-115">Authentication</span></span>|<span data-ttu-id="ca40d-116">なし</span><span class="sxs-lookup"><span data-stu-id="ca40d-116">None</span></span>|  
|<span data-ttu-id="ca40d-117">整合性</span><span class="sxs-lookup"><span data-stu-id="ca40d-117">Integrity</span></span>|<span data-ttu-id="ca40d-118">なし</span><span class="sxs-lookup"><span data-stu-id="ca40d-118">None</span></span>|  
|<span data-ttu-id="ca40d-119">機密性</span><span class="sxs-lookup"><span data-stu-id="ca40d-119">Confidentiality</span></span>|<span data-ttu-id="ca40d-120">なし</span><span class="sxs-lookup"><span data-stu-id="ca40d-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="ca40d-121">サービス</span><span class="sxs-lookup"><span data-stu-id="ca40d-121">Service</span></span>  
 <span data-ttu-id="ca40d-122">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="ca40d-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ca40d-123">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ca40d-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="ca40d-124">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca40d-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="ca40d-125">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="ca40d-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ca40d-126">コード</span><span class="sxs-lookup"><span data-stu-id="ca40d-126">Code</span></span>  
 <span data-ttu-id="ca40d-127">次のコードは、セキュリティで保護されないエンドポイントを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ca40d-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="ca40d-128">構成</span><span class="sxs-lookup"><span data-stu-id="ca40d-128">Configuration</span></span>  
 <span data-ttu-id="ca40d-129">次のコードは、次に示す構成を使用して同一のエンドポイントをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="ca40d-129">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""   
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"   
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="ca40d-130">Client</span><span class="sxs-lookup"><span data-stu-id="ca40d-130">Client</span></span>  
 <span data-ttu-id="ca40d-131">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="ca40d-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ca40d-132">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ca40d-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="ca40d-133">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca40d-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="ca40d-134">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca40d-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ca40d-135">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="ca40d-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ca40d-136">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ca40d-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="ca40d-137">コード</span><span class="sxs-lookup"><span data-stu-id="ca40d-137">Code</span></span>  
 <span data-ttu-id="ca40d-138">次のコードは、TCP プロトコルを使用してセキュリティで保護されていないエンドポイントにアクセスする基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ca40d-138">The following code shows a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="ca40d-139">構成</span><span class="sxs-lookup"><span data-stu-id="ca40d-139">Configuration</span></span>  
 <span data-ttu-id="ca40d-140">次の構成コードは、クライアントに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ca40d-140">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"   
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"   
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca40d-141">参照</span><span class="sxs-lookup"><span data-stu-id="ca40d-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="ca40d-142">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="ca40d-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="ca40d-143">Windows Server App Fabric のセキュリティ モデル</span><span class="sxs-lookup"><span data-stu-id="ca40d-143">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
