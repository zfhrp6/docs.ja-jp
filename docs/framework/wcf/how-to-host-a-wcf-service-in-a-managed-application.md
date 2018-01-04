---
title: "方法 : マネージ アプリケーションで WCF サービスをホストする"
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
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6491faa6134c1e80e07294d8f888200c04fa8704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a><span data-ttu-id="94c57-102">方法 : マネージ アプリケーションで WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="94c57-102">How to: Host a WCF Service in a Managed Application</span></span>
<span data-ttu-id="94c57-103">マネージ アプリケーションでサービスをホストするには、マネージ アプリケーション コード内にサービスのコードを埋め込み、サービスのエンドポイントをコードで強制的に定義するか、構成を使用して宣言により定義してから、または既定のエンドポイントを使用して、<xref:System.ServiceModel.ServiceHost> のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="94c57-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="94c57-104">メッセージの受信を開始するには、<xref:System.ServiceModel.ICommunicationObject.Open%2A> で <xref:System.ServiceModel.ServiceHost> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="94c57-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="94c57-105">これにより、サービスのリスナーが作成されて開きます。</span><span class="sxs-lookup"><span data-stu-id="94c57-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="94c57-106">この方法によるサービスのホストは、マネージ アプリケーション自体がホスト作業を行うため、"自己ホスト" と呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="94c57-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="94c57-107">サービスを閉じるには、<xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> で <xref:System.ServiceModel.ServiceHost> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="94c57-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="94c57-108">サービスは、マネージ Windows サービス、インターネット インフォメーション サービス (IIS)、または Windows プロセス アクティブ化サービス (WAS) でホストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="94c57-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="94c57-109">サービスのオプションをホストするを参照してください[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="94c57-109"> hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
 <span data-ttu-id="94c57-110">マネージ アプリケーションでのサービスのホスティングは、展開するインフラストラクチャが最小限で済むため、最も柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="94c57-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="94c57-111">マネージ アプリケーションでサービスをホストするを参照してください[マネージ アプリケーションのホスト](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="94c57-111"> hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="94c57-112">次の手順では、自己ホスト型サービスをコンソール アプリケーションに実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="94c57-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>  
  
### <a name="to-create-a-self-hosted-service"></a><span data-ttu-id="94c57-113">自己ホスト型サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="94c57-113">To create a self-hosted service</span></span>  
  
1.  <span data-ttu-id="94c57-114">開いている[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]選択**新規**、**プロジェクト.**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="94c57-114">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New**, **Project...** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="94c57-115">**インストールされたテンプレート**一覧で、 **Visual c#**、 **Windows**または**Visual Basic**、 **Windows**.</span><span class="sxs-lookup"><span data-stu-id="94c57-115">In the **Installed Templates** list, select **Visual C#**, **Windows** or **Visual Basic**, **Windows**.</span></span> <span data-ttu-id="94c57-116">によって、[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]設定、これらの両方またはいずれかの可能性があります、**他の言語**内のノード、**インストールされたテンプレート** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="94c57-116">Depending on your [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] settings, one or both of these may be under the **Other Languages** node in the **Installed Templates** list.</span></span>  
  
3.  <span data-ttu-id="94c57-117">選択**コンソール アプリケーション**から、 **Windows**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="94c57-117">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="94c57-118">型`SelfHost`で、**名前**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="94c57-118">Type `SelfHost` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="94c57-119">右クリック**SelfHost**で**ソリューション エクスプ ローラー**選択**参照の追加.**.選択**System.ServiceModel**から、 **.NET**  タブでをクリックし、 **OK**です。</span><span class="sxs-lookup"><span data-stu-id="94c57-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference...**. Select **System.ServiceModel** from the **.NET** tab and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="94c57-120">場合、**ソリューション エクスプ ローラー**ウィンドウが表示されている、select**ソリューション エクスプ ローラー**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="94c57-120">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="94c57-121">ダブルクリックして**Program.cs**または**Module1.vb**で**ソリューション エクスプ ローラー**がまだ開いていない場合、コード ウィンドウで開きます。</span><span class="sxs-lookup"><span data-stu-id="94c57-121">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window if it is not already open.</span></span> <span data-ttu-id="94c57-122">ファイルの先頭に次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="94c57-122">Add the following statements at the top of the file.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  <span data-ttu-id="94c57-123">サービス コントラクトを定義して実装します。</span><span class="sxs-lookup"><span data-stu-id="94c57-123">Define and implement a service contract.</span></span> <span data-ttu-id="94c57-124">この例では、サービスへの入力に基づいてメッセージを返す `HelloWorldService` を定義します。</span><span class="sxs-lookup"><span data-stu-id="94c57-124">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="94c57-125">方法を定義し、サービス インターフェイスを実装して参照してください[する方法: サービス コントラクトを定義する](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)と[する方法: サービス コントラクトを実装する](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="94c57-125"> how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>  
  
7.  <span data-ttu-id="94c57-126">`Main` メソッドの上部で、サービスのベース アドレスで <xref:System.Uri> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="94c57-126">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  <span data-ttu-id="94c57-127"><xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成して、サービス型を表す <xref:System.Type> とベース アドレス URI (Uniform Resource Identifier) を <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29> に渡します。</span><span class="sxs-lookup"><span data-stu-id="94c57-127">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="94c57-128">メタデータ公開を有効にして、<xref:System.ServiceModel.ICommunicationObject.Open%2A> で <xref:System.ServiceModel.ServiceHost> メソッドを呼び出し、サービスを初期化してメッセージを受信する準備をします。</span><span class="sxs-lookup"><span data-stu-id="94c57-128">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  <span data-ttu-id="94c57-129">この例では、既定のエンドポイントを使用するので、このサービスには構成ファイルは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="94c57-129">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="94c57-130">エンドポイントが構成されていない場合、ランタイムは、サービスによって実装されたサービス コントラクトごとに 1 つのエンドポイントを各ベース アドレスに作成します。</span><span class="sxs-lookup"><span data-stu-id="94c57-130">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="94c57-131">既定のエンドポイントを参照してください[簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="94c57-131"> default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="94c57-132">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="94c57-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="to-test-the-service"></a><span data-ttu-id="94c57-133">サービスをテストするには</span><span class="sxs-lookup"><span data-stu-id="94c57-133">To test the service</span></span>  
  
1.  <span data-ttu-id="94c57-134">Ctrl キーを押しながら F5 キーを押してサービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="94c57-134">Press Ctrl + F5 to run the service.</span></span>  
  
2.  <span data-ttu-id="94c57-135">開いている**WCF テスト クライアント**です。</span><span class="sxs-lookup"><span data-stu-id="94c57-135">Open **WCF Test Client**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="94c57-136">開くには**WCF テスト クライアント**を開き、[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]コマンド プロンプトを実行**WcfTestClient.exe**です。</span><span class="sxs-lookup"><span data-stu-id="94c57-136">To open **WCF Test Client**, open a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] command prompt and execute **WcfTestClient.exe**.</span></span>  
  
3.  <span data-ttu-id="94c57-137">選択**サービスを追加しています.**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="94c57-137">Select **Add Service...** from the **File** menu.</span></span>  
  
4.  <span data-ttu-id="94c57-138">型`http://localhost:8080/hello`クリックおよびアドレス ボックスに**OK**です。</span><span class="sxs-lookup"><span data-stu-id="94c57-138">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="94c57-139">サービスが実行していることを確認してください。サービスが実行していない場合、この手順は失敗します。</span><span class="sxs-lookup"><span data-stu-id="94c57-139">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="94c57-140">コードでベース アドレスを変更した場合は、この手順で、変更したアドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="94c57-140">If you have changed the base address in the code, then use the modified base address in this step.</span></span>  
  
5.  <span data-ttu-id="94c57-141">ダブルクリックして**SayHello**下にある、**マイ サービス プロジェクト**ノード。</span><span class="sxs-lookup"><span data-stu-id="94c57-141">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="94c57-142">名前を入力、**値**内の列、**要求**ボックスの一覧し、をクリックして**Invoke**です。</span><span class="sxs-lookup"><span data-stu-id="94c57-142">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span> <span data-ttu-id="94c57-143">応答メッセージに表示されます、**応答** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="94c57-143">A reply message appears in the **Response** list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94c57-144">例</span><span class="sxs-lookup"><span data-stu-id="94c57-144">Example</span></span>  
 <span data-ttu-id="94c57-145"><xref:System.ServiceModel.ServiceHost> 型のサービスをホストする `HelloWorldService` オブジェクトを作成し、<xref:System.ServiceModel.ICommunicationObject.Open%2A> で <xref:System.ServiceModel.ServiceHost> メソッドを呼び出す例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="94c57-145">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="94c57-146">ベース アドレスがコードで指定され、メタデータ公開が有効化されていて、既定のエンドポイントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="94c57-146">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="94c57-147">参照</span><span class="sxs-lookup"><span data-stu-id="94c57-147">See Also</span></span>  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [<span data-ttu-id="94c57-148">方法 : IIS で WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="94c57-148">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [<span data-ttu-id="94c57-149">自己ホスト</span><span class="sxs-lookup"><span data-stu-id="94c57-149">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="94c57-150">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="94c57-150">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="94c57-151">方法: サービス コントラクトを定義する</span><span class="sxs-lookup"><span data-stu-id="94c57-151">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="94c57-152">方法: サービス コントラクトを実装する</span><span class="sxs-lookup"><span data-stu-id="94c57-152">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="94c57-153">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="94c57-153">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="94c57-154">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="94c57-154">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="94c57-155">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="94c57-155">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
