---
title: '方法 : IIS で WCF サービスをホストする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: a1759434d259cdffe1dac6b19a6582bfb83784bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="c1fac-102">方法 : IIS で WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="c1fac-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="c1fac-103">このトピックでは、インターネット インフォメーション サービス (IIS) でホストされている Windows Communication Foundation (WCF) サービスを作成するために必要な基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="c1fac-104">このトピックは、IIS に関する知識があり、IIS 管理ツールを使用して IIS アプリケーションを作成および管理する方法を理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="c1fac-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="c1fac-105">IIS の詳細については、次を参照してください。[インターネット インフォメーション サービス](http://go.microsoft.com/fwlink/?LinkId=132449)です。</span><span class="sxs-lookup"><span data-stu-id="c1fac-105">For more information about IIS see [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449).</span></span> <span data-ttu-id="c1fac-106">IIS 環境で実行されますが、プロセスのリサイクルなどの IIS 機能を最大限に活用する WCF サービスのアイドル シャット ダウン、処理状況の監視、およびメッセージに基づくアクティベーション。</span><span class="sxs-lookup"><span data-stu-id="c1fac-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="c1fac-107">このホスト オプションでは、IIS が正しく構成されている必要がありますが、アプリケーションの一部としてホスト コードを書く必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c1fac-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="c1fac-108">IIS ホストは、HTTP トランスポートでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1fac-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="c1fac-109">方法の詳細についての WCF と[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]対話は、「 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1fac-109">For more information about how WCF and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="c1fac-110">セキュリティの構成の詳細については、次を参照してください。[セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1fac-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="c1fac-111">この例の元のコピーを次を参照してください。 [IIS ホストを使用してインライン コード](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1fac-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="c1fac-112">IIS でホストされるサービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="c1fac-112">To create a service hosted by IIS</span></span>  
  
1.  <span data-ttu-id="c1fac-113">コンピューターに IIS がインストールされ、実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="c1fac-114">インストールして、IIS の構成の詳細については、次を参照してください[のインストールと IIS 7.0 の構成。](http://go.microsoft.com/fwlink/?LinkID=132128)</span><span class="sxs-lookup"><span data-stu-id="c1fac-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)</span></span>  
  
2.  <span data-ttu-id="c1fac-115">アプリケーション ファイル用に "IISHostedCalcService" という新しいフォルダーを作成し、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] がそのフォルダーの内容にアクセスできることを確認します。次に、IIS 管理ツールを使用して、このアプリケーション ディレクトリに物理的に配置する新しい IIS アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-115">Create a new folder for your application files called "IISHostedCalcService", ensure that [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="c1fac-116">アプリケーション ディレクトリのエイリアスを作成する場合は、"IISHostedCalc" を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3.  <span data-ttu-id="c1fac-117">"service.svc" という新しいファイルをアプリケーション ディレクトリに作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="c1fac-118">次を追加することでこのファイルを編集@ServiceHost要素。</span><span class="sxs-lookup"><span data-stu-id="c1fac-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  <span data-ttu-id="c1fac-119">アプリケーション ディレクトリ内に App_Code サブディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5.  <span data-ttu-id="c1fac-120">App_Code サブディレクトリに Service.cs というコード ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6.  <span data-ttu-id="c1fac-121">Service.cs ファイルの先頭に次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  <span data-ttu-id="c1fac-122">using ステートメントの後に、次の名前空間宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  <span data-ttu-id="c1fac-123">次のコードに示すように、名前空間宣言内にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="c1fac-124">次のコードに示すように、サービス コントラクト定義の後に、サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="c1fac-125">アプリケーション ディレクトリ内に "Web.config" というファイルを作成し、次の構成コードをファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="c1fac-126">実行時に、WCF インフラストラクチャは、クライアント アプリケーションと通信できるエンドポイントを構築するために情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     <span data-ttu-id="c1fac-127">この例では、構成ファイルにエンドポイントを明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="c1fac-128">エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="c1fac-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="c1fac-129">詳細については、既定のエンドポイント、バインディング、および動作を参照してください[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1fac-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="c1fac-130">サービスが正確にホストされるようにするには、Internet Explorer のインスタンスを開き、サービスの URL: `http://localhost/IISHostedCalc/Service.svc` を参照します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1fac-131">例</span><span class="sxs-lookup"><span data-stu-id="c1fac-131">Example</span></span>  
 <span data-ttu-id="c1fac-132">IIS がホストする電卓サービスのコードの完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c1fac-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="c1fac-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1fac-133">See Also</span></span>  
 [<span data-ttu-id="c1fac-134">インターネット インフォメーション サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="c1fac-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="c1fac-135">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="c1fac-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="c1fac-136">WCF サービスと ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c1fac-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [<span data-ttu-id="c1fac-137">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c1fac-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 [<span data-ttu-id="c1fac-138">Windows Server App Fabric のホスティング機能</span><span class="sxs-lookup"><span data-stu-id="c1fac-138">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
