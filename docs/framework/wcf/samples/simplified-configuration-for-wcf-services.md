---
title: "WCF サービスの簡略化された構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02611dc44b98c1b8b5ef5ae74559f9f370483792
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="8e4d0-102">WCF サービスの簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="8e4d0-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="8e4d0-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、一般的なサービスおよびクライアントを実装して構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-103">This sample demonstrates how to implement and configure a typical service and client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="8e4d0-104">このサンプルは、他のすべての基本的な技術サンプルの基礎になります。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="8e4d0-105">このサービスは、サービスとの通信に使用する単一エンドポイントを公開しており、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] の簡略化された構成を使用しています。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="8e4d0-106">[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 以前は、次の構成コード例に示すように、エンドポイントは通常、構成ファイル (Web.config) で定義されています。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="8e4d0-107">[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] では、`<service>` 要素は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="8e4d0-108">サービスでエンドポイントが定義されていない場合、各ベース アドレスのエンドポイントと実装されたコントラクトがサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="8e4d0-109">このベース アドレスがコントラクト名に追加されてエンドポイントが決定され、バインドがアドレス スキームで決定されます。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="8e4d0-110">次のコード例は、簡略化された構成ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="8e4d0-111">前の構成では、サービスと同じコンピューター上にあるクライアントは、http://localhost/servicemodelsamples/service.svc でサービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-111">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="8e4d0-112">リモート コンピューター上のクライアントがサービスにアクセスするには、localhost の代わりに完全修飾ドメイン名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="8e4d0-113">既定では、サービスはメタデータを公開しません。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="8e4d0-114">そのため、サービスは <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 動作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="8e4d0-115">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="8e4d0-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="8e4d0-116">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8e4d0-117">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8e4d0-118">次の手順に従ってサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-118">Run the sample by following these steps:</span></span>  
  
    1.  <span data-ttu-id="8e4d0-119">右クリックして、**サービス**プロジェクトし、選択**スタートアップ プロジェクトとして設定**、キーを押します**ctrl キーを押しながら f5 キー**です。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2.  <span data-ttu-id="8e4d0-120">コンソール出力でサービスが動作していることが確認されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3.  <span data-ttu-id="8e4d0-121">右クリックして、**クライアント**プロジェクトし、選択**スタートアップ プロジェクトとして設定**、キーを押します**ctrl キーを押しながら f5 キー**です。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e4d0-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8e4d0-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8e4d0-124">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8e4d0-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8e4d0-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="8e4d0-126">参照</span><span class="sxs-lookup"><span data-stu-id="8e4d0-126">See Also</span></span>  
 [<span data-ttu-id="8e4d0-127">AppFabric 管理のサンプル</span><span class="sxs-lookup"><span data-stu-id="8e4d0-127">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [<span data-ttu-id="8e4d0-128">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="8e4d0-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
