---
title: "トランスポート セキュリティと匿名クライアント"
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
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a4d4180a0a60e062ab6d8872b153d5bc8b416708
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="47db7-102">トランスポート セキュリティと匿名クライアント</span><span class="sxs-lookup"><span data-stu-id="47db7-102">Transport Security with an Anonymous Client</span></span>
<span data-ttu-id="47db7-103">この [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] シナリオでは、トランスポート セキュリティ (HTTPS) を使用して機密性と整合性を確保します。</span><span class="sxs-lookup"><span data-stu-id="47db7-103">This [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="47db7-104">サーバーは SSL (Secure Sockets Layer) 証明書で認証される必要があり、クライアントはサーバーの証明書を信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47db7-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="47db7-105">クライアントを認証する機構はないため、匿名となります。</span><span class="sxs-lookup"><span data-stu-id="47db7-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>  
  
 <span data-ttu-id="47db7-106">サンプル アプリケーションについては、次を参照してください。 [WS トランスポート セキュリティ](../../../../docs/framework/wcf/samples/ws-transport-security.md)です。</span><span class="sxs-lookup"><span data-stu-id="47db7-106">For a sample application, see [WS Transport Security](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="47db7-107">トランスポート セキュリティを参照してください[トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="47db7-107"> transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="47db7-108">サービスと証明書の使用を参照してください[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)と[する方法: SSL 証明書でポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)です。</span><span class="sxs-lookup"><span data-stu-id="47db7-108"> using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 <span data-ttu-id="47db7-109">![トランスポート セキュリティを使用すると匿名クライアント](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span><span class="sxs-lookup"><span data-stu-id="47db7-109">![Using transport security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span></span>  
  
|<span data-ttu-id="47db7-110">特徴</span><span class="sxs-lookup"><span data-stu-id="47db7-110">Characteristic</span></span>|<span data-ttu-id="47db7-111">説明</span><span class="sxs-lookup"><span data-stu-id="47db7-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="47db7-112">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="47db7-112">Security Mode</span></span>|<span data-ttu-id="47db7-113">Transport</span><span class="sxs-lookup"><span data-stu-id="47db7-113">Transport</span></span>|  
|<span data-ttu-id="47db7-114">相互運用性</span><span class="sxs-lookup"><span data-stu-id="47db7-114">Interoperability</span></span>|<span data-ttu-id="47db7-115">既存の Web サービスとクライアントを使用する</span><span class="sxs-lookup"><span data-stu-id="47db7-115">With existing Web services and clients</span></span>|  
|<span data-ttu-id="47db7-116">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="47db7-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="47db7-117">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="47db7-117">Authentication (Client)</span></span>|<span data-ttu-id="47db7-118">はい</span><span class="sxs-lookup"><span data-stu-id="47db7-118">Yes</span></span><br /><br /> <span data-ttu-id="47db7-119">アプリケーション レベル ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサポートなし)</span><span class="sxs-lookup"><span data-stu-id="47db7-119">Application level (no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] support)</span></span>|  
|<span data-ttu-id="47db7-120">整合性</span><span class="sxs-lookup"><span data-stu-id="47db7-120">Integrity</span></span>|<span data-ttu-id="47db7-121">はい</span><span class="sxs-lookup"><span data-stu-id="47db7-121">Yes</span></span>|  
|<span data-ttu-id="47db7-122">機密性</span><span class="sxs-lookup"><span data-stu-id="47db7-122">Confidentiality</span></span>|<span data-ttu-id="47db7-123">はい</span><span class="sxs-lookup"><span data-stu-id="47db7-123">Yes</span></span>|  
|<span data-ttu-id="47db7-124">Transport</span><span class="sxs-lookup"><span data-stu-id="47db7-124">Transport</span></span>|<span data-ttu-id="47db7-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="47db7-125">HTTPS</span></span>|  
|<span data-ttu-id="47db7-126">バインド</span><span class="sxs-lookup"><span data-stu-id="47db7-126">Binding</span></span>|<span data-ttu-id="47db7-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="47db7-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>|  
  
## <a name="service"></a><span data-ttu-id="47db7-128">サービス</span><span class="sxs-lookup"><span data-stu-id="47db7-128">Service</span></span>  
 <span data-ttu-id="47db7-129">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="47db7-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="47db7-130">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="47db7-130">Do one of the following:</span></span>  
  
-   <span data-ttu-id="47db7-131">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="47db7-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="47db7-132">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="47db7-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="47db7-133">コード</span><span class="sxs-lookup"><span data-stu-id="47db7-133">Code</span></span>  
 <span data-ttu-id="47db7-134">次のコードは、トランスポート セキュリティを使用してエンドポイントを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="47db7-134">The following code shows how to create an endpoint using transport security:</span></span>  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a><span data-ttu-id="47db7-135">構成</span><span class="sxs-lookup"><span data-stu-id="47db7-135">Configuration</span></span>  
 <span data-ttu-id="47db7-136">次のコードは、構成を使用して同一のエンドポイントをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="47db7-136">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="47db7-137">クライアントを認証する機構はないため、匿名となります。</span><span class="sxs-lookup"><span data-stu-id="47db7-137">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="47db7-138">クライアント</span><span class="sxs-lookup"><span data-stu-id="47db7-138">Client</span></span>  
 <span data-ttu-id="47db7-139">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="47db7-139">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="47db7-140">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="47db7-140">Do one of the following:</span></span>  
  
-   <span data-ttu-id="47db7-141">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="47db7-141">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="47db7-142">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="47db7-142">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="47db7-143">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="47db7-143">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="47db7-144">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="47db7-144">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="47db7-145">コード</span><span class="sxs-lookup"><span data-stu-id="47db7-145">Code</span></span>  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a><span data-ttu-id="47db7-146">構成</span><span class="sxs-lookup"><span data-stu-id="47db7-146">Configuration</span></span>  
 <span data-ttu-id="47db7-147">コードの代わりに次の構成を使用して、サービスをセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="47db7-147">The following configuration can be used instead of the code to set up the service.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47db7-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="47db7-148">See Also</span></span>  
 [<span data-ttu-id="47db7-149">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="47db7-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="47db7-150">WS トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="47db7-150">WS Transport Security</span></span>](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [<span data-ttu-id="47db7-151">トランスポート セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="47db7-151">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [<span data-ttu-id="47db7-152">Windows Server App Fabric のセキュリティ モデル</span><span class="sxs-lookup"><span data-stu-id="47db7-152">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
