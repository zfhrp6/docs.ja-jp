---
title: "方法 : WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する"
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
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b4bd1dce4128e6f25294525f10226d98f732cd4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a><span data-ttu-id="ad261-102">方法 : WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する</span><span class="sxs-lookup"><span data-stu-id="ad261-102">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>
<span data-ttu-id="ad261-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web サービス クライアントと相互運用できるように [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] サービス エンドポイントを構成するには、サービス エンドポイントのバインディングの種類として <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="ad261-103">To configure a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web service clients, use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
 <span data-ttu-id="ad261-104">必要に応じて、HTTPS およびトランスポート レベルのクライアント認証のサポートをバインディングで有効にできます。</span><span class="sxs-lookup"><span data-stu-id="ad261-104">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="ad261-105"> Web サービス クライアントでは MTOM メッセージ エンコーディングがサポートされていないため、<xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> プロパティは、既定値である <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="ad261-105"> Web service clients do not support MTOM message encoding, so the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property should be left as its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ad261-106">また、ASP.Net Web サービス クライアントでは WS-Security がサポートされていないため、<xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> を <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad261-106">ASP.Net Web Service clients do not support WS-Security, so the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> should be set to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span>  
  
 <span data-ttu-id="ad261-107">メタデータを行うために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]に利用できるサービス[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web サービス プロキシ生成ツール (つまり、 [Web サービス記述言語ツール (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833)、 [Web サービス検出ツール (Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)、および Visual Studio で Web 参照の追加機能)、HTTP GET メタデータ エンドポイントを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad261-107">To make the metadata for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service available to [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web service proxy generation tools (that is, [Web Services Description Language Tool (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833), [Web Services Discovery Tool (Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834), and the Add Web Reference feature in Visual Studio), you should expose an HTTP/GET metadata endpoint.</span></span>  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a><span data-ttu-id="ad261-108">コードを使用して ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加するには</span><span class="sxs-lookup"><span data-stu-id="ad261-108">To add a WCF endpoint that is compatible with ASP.NET Web service clients in code</span></span>  
  
1.  <span data-ttu-id="ad261-109">新しい <xref:System.ServiceModel.BasicHttpBinding> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ad261-109">Create a new <xref:System.ServiceModel.BasicHttpBinding> instance</span></span>  
  
2.  <span data-ttu-id="ad261-110">必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインディングのトランスポート セキュリティを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ad261-110">Optionally enable transport security for this service endpoint binding by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="ad261-111">詳細については、「[トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad261-111">For details, please see [Transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
3.  <span data-ttu-id="ad261-112">上で作成したバインディング インスタンスを使用して、サービス ホストに新しいアプリケーション エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="ad261-112">Add a new application endpoint to your service host using the binding instance that you just created.</span></span> <span data-ttu-id="ad261-113">コードでサービス エンドポイントを追加する方法の詳細については、次を参照してください。、[する方法: コードでサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad261-113">For details about how to add a service endpoint in code, see the [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
4.  <span data-ttu-id="ad261-114">サービス用に HTTP/GET メタデータのエンドポイントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ad261-114">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="ad261-115">詳細をご覧ください[する方法: サービスを使用してコードのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad261-115">For details see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span>  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a><span data-ttu-id="ad261-116">構成ファイルを使用して ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加するには</span><span class="sxs-lookup"><span data-stu-id="ad261-116">To add a WCF endpoint that is compatible with ASP.NET Web service clients in a configuration file</span></span>  
  
1.  <span data-ttu-id="ad261-117">新しい <xref:System.ServiceModel.BasicHttpBinding> バインディング構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="ad261-117">Create a new <xref:System.ServiceModel.BasicHttpBinding> binding configuration.</span></span> <span data-ttu-id="ad261-118">詳細については、次を参照してください。、[する方法: 構成では、サービス バインドを指定して](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad261-118">For details, see the [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
2.  <span data-ttu-id="ad261-119">必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインディング構成のトランスポート セキュリティを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ad261-119">Optionally enable transport security for this service endpoint binding configuration by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="ad261-120">詳細については、「[トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad261-120">For details, see [Transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
3.  <span data-ttu-id="ad261-121">上で作成したバインド構成を使用して、サービスに新しいアプリケーション エンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="ad261-121">Configure a new application endpoint for your service using the binding configuration that you just created.</span></span> <span data-ttu-id="ad261-122">構成ファイルでサービス エンドポイントを追加する方法の詳細については、次を参照してください。、[する方法: 構成でサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad261-122">For details about how to add a service endpoint in a configuration file, see the [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
4.  <span data-ttu-id="ad261-123">サービス用に HTTP/GET メタデータのエンドポイントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ad261-123">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="ad261-124">詳細を参照してください、[する方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad261-124">For details see the [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad261-125">例</span><span class="sxs-lookup"><span data-stu-id="ad261-125">Example</span></span>  
 <span data-ttu-id="ad261-126">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービス クライアントと互換性のある [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] エンドポイントをコードおよび構成ファイルで追加する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="ad261-126">The following example code demonstrates how to add a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint that is compatible with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web service clients in code and alternatively in configuration files.</span></span>  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a><span data-ttu-id="ad261-127">参照</span><span class="sxs-lookup"><span data-stu-id="ad261-127">See Also</span></span>  
 [<span data-ttu-id="ad261-128">方法 : コード内にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="ad261-128">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 [<span data-ttu-id="ad261-129">方法 : コードを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="ad261-129">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 [<span data-ttu-id="ad261-130">方法: 構成でサービス バインディングを指定する</span><span class="sxs-lookup"><span data-stu-id="ad261-130">How to: Specify a Service Binding in Configuration</span></span>](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [<span data-ttu-id="ad261-131">方法 : 構成にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="ad261-131">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [<span data-ttu-id="ad261-132">方法 : 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="ad261-132">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="ad261-133">トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ad261-133">Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="ad261-134">メタデータを使用する</span><span class="sxs-lookup"><span data-stu-id="ad261-134">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
