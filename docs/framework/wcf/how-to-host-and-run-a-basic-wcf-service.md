---
title: '方法 : 基本的な Windows Communication Foundation サービスをホストおよび実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: f1c56ed83fa214cf781a833e05642635ac24b0c5
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753501"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="dccf0-102">方法 : 基本的な Windows Communication Foundation サービスをホストおよび実行する</span><span class="sxs-lookup"><span data-stu-id="dccf0-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>
<span data-ttu-id="dccf0-103">Windows Communication Foundation (WCF) アプリケーションの作成に必要な 6 つのタスクのうちの 3 番目がこれです。</span><span class="sxs-lookup"><span data-stu-id="dccf0-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="dccf0-104">6 つのすべてのタスクの概要については、「[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="dccf0-105">このトピックでは、コンソール アプリケーションで Windows Communication Foundation (WCF) サービスをホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="dccf0-106">この操作は、次の手順から構成されます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-106">This procedure consists of the following steps:</span></span>  
  
-   <span data-ttu-id="dccf0-107">コンソール アプリケーション プロジェクトを作成し、サービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-107">Create a console application project to host the service.</span></span>  
  
-   <span data-ttu-id="dccf0-108">サービスのサービス ホストを作成します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-108">Create a service host for the service.</span></span>  
  
-   <span data-ttu-id="dccf0-109">メタデータ交換を有効にします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-109">Enable metadata exchange.</span></span>  
  
-   <span data-ttu-id="dccf0-110">サービス ホストを開きます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-110">Open the service host.</span></span>  
  
 <span data-ttu-id="dccf0-111">このタスクで書かれるコードの全容は手順に続いて提供されている例で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="dccf0-112">新しいコンソール アプリケーションを作成し、サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="dccf0-112">To create a new console application to host the service</span></span>  
  
1.  <span data-ttu-id="dccf0-113">入門ソリューションを右クリックし、**[追加]**、**[新しいプロジェクト]** の順にクリックして新しいコンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-113">Create a new Console Application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="dccf0-114">**[新しいプロジェクトの追加]** ダイアログ ボックスの左側で、**[C#]** または **[VB]** の下にある **[Windows]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-114">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="dccf0-115">ダイアログ ボックスの中央のセクションで、**[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-115">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="dccf0-116">プロジェクトに GettingStartedHost という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-116">Name the project GettingStartedHost.</span></span>  
  
2.  <span data-ttu-id="dccf0-117">ソリューション エクスプローラーで **[GettingStartedHost]** を右クリックし、**[プロパティ]** を選択することで、GettingStartedHost プロジェクトのターゲット フレームワークを .NET Framework 4.5 に設定します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-117">Set the target framework of the GettingStartedHost project to .NET Framework 4.5 by right clicking on **GettingStartedHost** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="dccf0-118">**[ターゲット フレームワーク]** ボックスの一覧で、**[.NET Framework 4.5]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-118">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="dccf0-119">VB プロジェクトのターゲット フレームワークを設定する方法は多少異なり、GettingStartedHost プロジェクトの [プロパティ] ダイアログ ボックスで、画面左側の **[コンパイル]** タブをクリックし、ダイアログ ボックスの左下隅にある **[詳細コンパイル オプション]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-119">Setting the target framework for a VB project is a little different, in the GettingStartedHost project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="dccf0-120">次に、**[ターゲット フレームワーク]** ボックスの一覧の **[.NET Framework 4.5]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-120">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="dccf0-121">ターゲット フレームワークを設定すると、[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] はソリューションを再読み込みします。ダイアログが表示されたら、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-121">Setting the target framework will cause [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="dccf0-122">GettingStartedLib プロジェクトへの参照を GettingStartedHost プロジェクトに追加します。ソリューション エクスプローラーで GettingStartedHost プロジェクトの **[参照]** フォルダーを右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-122">Add a reference to the GettingStartedLib project to the GettingStartedHost project by right clicking on the **References** folder under the GettingStartedHost project in the solution explorer and select **Add Reference**.</span></span> <span data-ttu-id="dccf0-123">**[参照の追加]** ダイアログで、ダイアログの左側の **[ソリューション]** を選択します。ダイアログの中央セクションで [GettingStartedLib] を選択し、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-123">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog and select GettingStartedLib in the center section of the dialog and click **Add**.</span></span> <span data-ttu-id="dccf0-124">これにより、GettingStartedLib に定義されている型を GettingStartedHost プロジェクトで利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="dccf0-124">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>  
  
4.  <span data-ttu-id="dccf0-125">ソリューション エクスプローラーで GettingStartedHost プロジェクトの **[参照]** フォルダーを右クリックし、**[参照の追加]** を選択することで、System.ServiceModel の参照を GettingStartedHost プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-125">Add a reference to System.ServiceModel to the GettingStartedHost project by right-clicking the **Reference** folder under the GettingStartedHost project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="dccf0-126">**[参照の追加]** ダイアログ ボックスの左側で、**[フレームワーク]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="dccf0-127">[アセンブリの検索] ボックスに「`System.ServiceModel`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="dccf0-128">ダイアログ ボックスの中央のセクションで、**[System.ServiceModel]** を選択し、**[追加]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="dccf0-129">メイン メニューの [すべて保存] をクリックして、ソリューションを保存します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-129">Save the solution by clicking the Save All button below the main menu.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="dccf0-130">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="dccf0-130">To host the service</span></span>  
  
-   <span data-ttu-id="dccf0-131">Program.cs ファイルまたは Module.vb ファイルを開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-131">Open the Program.cs or Module.vb file and enter the following code:</span></span>  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
    namespace GettingStartedHost  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                // Step 1 Create a URI to serve as the base address.  
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");  
  
                // Step 2 Create a ServiceHost instance  
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
                try  
                {  
                    // Step 3 Add a service endpoint.  
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                    // Step 4 Enable metadata exchange.  
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                    smb.HttpGetEnabled = true;  
                    selfHost.Description.Behaviors.Add(smb);  
  
                    // Step 5 Start the service.  
                    selfHost.Open();  
                    Console.WriteLine("The service is ready.");  
                    Console.WriteLine("Press <ENTER> to terminate service.");  
                    Console.WriteLine();  
                    Console.ReadLine();  
  
                    // Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close();  
                }  
                catch (CommunicationException ce)  
                {  
                    Console.WriteLine("An exception occurred: {0}", ce.Message);  
                    selfHost.Abort();  
                }  
            }  
        }  
    }  
    ```  
  
    ```vb
    'Module1.vb  
    Imports System  
    Imports System.ServiceModel  
    Imports System.ServiceModel.Description  
    Imports GettingStartedLibVB.GettingStartedLib  
  
    Module Service  
  
        Class Program  
            Shared Sub Main()  
                ' Step 1 Create a URI to serve as the base address  
                Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
                ' Step 2 Create a ServiceHost instance  
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
                Try  
  
                    ' Step 3 Add a service endpoint  
                    ' Add a service endpoint  
                    selfHost.AddServiceEndpoint( _  
                        GetType(ICalculator), _  
                        New WSHttpBinding(), _  
                        "CalculatorService")  
  
                    ' Step 4 Enable metadata exchange.  
                    Dim smb As New ServiceMetadataBehavior()  
                    smb.HttpGetEnabled = True  
                    selfHost.Description.Behaviors.Add(smb)  
  
                    ' Step 5 Start the service  
                    selfHost.Open()  
                    Console.WriteLine("The service is ready.")  
                    Console.WriteLine("Press <ENTER> to terminate service.")  
                    Console.WriteLine()  
                    Console.ReadLine()  
  
                    ' Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close()  
                Catch ce As CommunicationException  
                    Console.WriteLine("An exception occurred: {0}", ce.Message)  
                    selfHost.Abort()  
                End Try  
            End Sub  
        End Class  
  
    End Module  
    ```  
  
    1.  <span data-ttu-id="dccf0-132">手順 1 - サービスのベース アドレスを保持する Uri クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-132">Step 1 - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="dccf0-133">サービスは、ベース アドレスとオプションの URI を含む URL によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-133">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="dccf0-134">ベース アドレスの書式は、[トランスポート]://[コンピューター名またはドメイン][:省略可能なポート番号]/[省略可能な URI セグメント] です。電卓サービスのベース アドレスは、電卓サービスのベース アドレスを使用して HTTP トランスポート、localhost、ポート 8000、および URI セグメント "GettingStarted" を使用します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-134">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>  
  
    2.  <span data-ttu-id="dccf0-135">手順 2 - サービスをホストする <xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-135">Step 2 – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="dccf0-136">コンストラクターは、サービス コントラクトを実装するクラスの型と、サービスのベース アドレスの、2 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="dccf0-136">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>  
  
    3.  <span data-ttu-id="dccf0-137">手順 3 - <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-137">Step 3 – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="dccf0-138">サービス エンドポイントは、アドレス、バインディング、およびサービス コントラクトから構成されます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-138">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="dccf0-139"><xref:System.ServiceModel.Description.ServiceEndpoint> コンストラクターは、サービス コントラクト インターフェイスの型、バインディング、およびアドレスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="dccf0-139">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="dccf0-140">サービス コントラクトは、サービス型に定義および実装した `ICalculator` です。</span><span class="sxs-lookup"><span data-stu-id="dccf0-140">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="dccf0-141">このサンプルで使用するバインディングは、WS-\* 仕様に準拠するエンドポイントへの接続に使用される組み込みのバインディングである <xref:System.ServiceModel.WSHttpBinding> です。</span><span class="sxs-lookup"><span data-stu-id="dccf0-141">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="dccf0-142">WCF バインディングの詳細については、[WCF バインディングの概要](../../../docs/framework/wcf/bindings-overview.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-142">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="dccf0-143">エンドポイントを識別するために、ベース アドレスにアドレスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-143">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="dccf0-144">このコードに指定されているアドレスは "CalculatorService" です。そのため、エンドポイントの完全修飾アドレスは `"http://localhost:8000/GettingStarted/CalculatorService"` になります。 .NET Framework 4.0 以降を使用するとき、サービス エンドポイントの追加は任意です。</span><span class="sxs-lookup"><span data-stu-id="dccf0-144">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"` Adding a service endpoint is optional when using .NET Framework 4.0 or later.</span></span> <span data-ttu-id="dccf0-145">これらのバージョンでは、エンドポイントがコードまたは構成で指定されていない場合、WCF は、サービスで実装されたベース アドレスとコントラクトの組み合わせごとに、1 つの既定のエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-145">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="dccf0-146">既定のエンドポイントの詳細については、「[Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md)」 (エンドポイント アドレスの指定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-146">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="dccf0-147">既定のエンドポイントについては、「[Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md)」 (簡易構成) と「[Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」 (WCF サービスの簡易構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-147">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="dccf0-148">サービス エンドポイントの追加は、.NET Framework 4 以降を使用する場合は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="dccf0-148">Adding a service endpoint is optional when using .NET Framework 4 or later.</span></span> <span data-ttu-id="dccf0-149">これらのバージョンでは、エンドポイントがコードまたは構成で指定されていない場合、WCF は、サービスで実装されたベース アドレスとコントラクトの組み合わせごとに、1 つの既定のエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-149">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="dccf0-150">既定のエンドポイントの詳細については、「[Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md)」 (エンドポイント アドレスの指定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-150">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="dccf0-151">既定のエンドポイントについては、「[Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md)」 (簡易構成) と「[Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」 (WCF サービスの簡易構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-151">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
    4.  <span data-ttu-id="dccf0-152">手順 4 - メタデータ交換を有効にします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-152">Step 4 – Enable metadata exchange.</span></span> <span data-ttu-id="dccf0-153">クライアントは、サービス操作を呼び出すために使用されるプロキシの生成にメタデータ交換を使用します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-153">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="dccf0-154">メタデータ交換を有効化するには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスを作成してその <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true` に設定し、動作を <xref:System.ServiceModel.ServiceHost> インスタンスの <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-154">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>  
  
    5.  <span data-ttu-id="dccf0-155">手順 5 - 受信メッセージをリッスンするために <xref:System.ServiceModel.ServiceHost> を開きます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-155">Step 5 – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="dccf0-156">コードでは、ユーザーによる Enter キーの押下を待機しています。</span><span class="sxs-lookup"><span data-stu-id="dccf0-156">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="dccf0-157">この動作を行わない場合、アプリは直ちに終了し、サービスはシャットダウンします。また、try/catch ブロックが使用されている点にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-157">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="dccf0-158"><xref:System.ServiceModel.ServiceHost> がインスタンス化された後、他のコードはすべて try/catch ブロックに配置されます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-158">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="dccf0-159"><xref:System.ServiceModel.ServiceHost> によってスローされた例外を安全にキャッチする方法の詳細については、「[Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)」 (using ステートメントで問題を回避する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-159">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>  
  
### <a name="to-verify-the-service-is-working"></a><span data-ttu-id="dccf0-160">サービスが正常に機能していることを確認するには</span><span class="sxs-lookup"><span data-stu-id="dccf0-160">To verify the service is working</span></span>  
  
1.  <span data-ttu-id="dccf0-161">[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 内から GettingStartedHost コンソール アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-161">Run the GettingStartedHost console application from inside [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="dccf0-162">[!INCLUDE[wv](../../../includes/wv-md.md)] 以降のオペレーティング システムでは、サービスを管理者権限で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dccf0-162">When running on [!INCLUDE[wv](../../../includes/wv-md.md)] and later operating systems, the service must be run with administrator privileges.</span></span> <span data-ttu-id="dccf0-163">Visual Studio が管理者権限で実行されるため、GettingStartedHost も管理者権限で実行されます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-163">Because Visual Studio was run with Administrator privileges, GettingStartedHost is also run with Administrator privileges.</span></span> <span data-ttu-id="dccf0-164">新しいコマンド プロンプトを管理者権限で開いて、service.exe をその中で実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="dccf0-164">You can also start a new command prompt running it with Administrator privileges and run service.exe within it.</span></span>  
  
2.  <span data-ttu-id="dccf0-165">Internet Explorer を開き、サービスのデバッグ ページ (`http://localhost:8000/GettingStarted/CalculatorService`) に移動します。</span><span class="sxs-lookup"><span data-stu-id="dccf0-165">Open Internet Explorer and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dccf0-166">例</span><span class="sxs-lookup"><span data-stu-id="dccf0-166">Example</span></span>  
 <span data-ttu-id="dccf0-167">次の例では、チュートリアルの前の手順で作成したサービス コントラクトと実装を含め、コンソール アプリケーションでサービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-167">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>  
  
 <span data-ttu-id="dccf0-168">コマンド ライン コンパイラでこれをコンパイルするには、`System.ServiceModel.dll` を参照するクラス ライブラリに IService1.cs と Service1.cs をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-168">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library referencing `System.ServiceModel.dll`.</span></span> <span data-ttu-id="dccf0-169">さらに、Program.cs をコンソール アプリケーションにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="dccf0-169">And compile Program.cs to a console application.</span></span>  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
        public interface ICalculator  
        {  
            [OperationContract]  
            double Add(double n1, double n2);  
            [OperationContract]  
            double Subtract(double n1, double n2);  
            [OperationContract]  
            double Multiply(double n1, double n2);  
            [OperationContract]  
            double Divide(double n1, double n2);  
        }  
}  
```  
  
```csharp
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            // Code added to write output to the console window.  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
    }  
}  
```  
  
```csharp
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
namespace GettingStartedHost  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");  
  
            // Step 2 of the hosting procedure: Create ServiceHost  
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
            try  
            {  
                // Step 3 of the hosting procedure: Add a service endpoint.  
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                // Step 4 of the hosting procedure: Enable metadata exchange.  
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                smb.HttpGetEnabled = true;  
                selfHost.Description.Behaviors.Add(smb);  
  
                // Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open();  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                selfHost.Close();  
            }  
            catch (CommunicationException ce)  
            {  
                Console.WriteLine("An exception occurred: {0}", ce.Message);  
                selfHost.Abort();  
            }  
        }  
    }  
}  
```  
  
```vb
'IService1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
    Public Interface ICalculator  
  
        <OperationContract()> _  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
End Namespace  
```  
  
```vb
'Service1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    Public Class CalculatorService  
        Implements ICalculator  
  
        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
            Dim result As Double = n1 + n2  
            ' Code added to write output to the console window.  
            Console.WriteLine("Received Add({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
        End Function  
  
        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
            Dim result As Double = n1 - n2  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
            Dim result As Double = n1 * n2  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
            Dim result As Double = n1 / n2  
            Console.WriteLine("Received Divide({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
    End Class  
End Namespace  
```  
  
```vb
'Module1.vb  
Imports System  
Imports System.ServiceModel  
Imports System.ServiceModel.Description  
Imports GettingStartedLibVB.GettingStartedLib  
  
Module Service  
  
    Class Program  
        Shared Sub Main()  
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
            ' Step 2 of the hosting procedure: Create ServiceHost  
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
            Try  
  
                ' Step 3 of the hosting procedure: Add a service endpoint.  
                ' Add a service endpoint  
                selfHost.AddServiceEndpoint( _  
                    GetType(ICalculator), _  
                    New WSHttpBinding(), _  
                    "CalculatorService")  
  
                ' Step 4 of the hosting procedure: Enable metadata exchange.  
                ' Enable metadata exchange  
                Dim smb As New ServiceMetadataBehavior()  
                smb.HttpGetEnabled = True  
                selfHost.Description.Behaviors.Add(smb)  
  
                ' Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open()  
                Console.WriteLine("The service is ready.")  
                Console.WriteLine("Press <ENTER> to terminate service.")  
                Console.WriteLine()  
                Console.ReadLine()  
  
                ' Close the ServiceHostBase to shutdown the service.  
                selfHost.Close()  
            Catch ce As CommunicationException  
                Console.WriteLine("An exception occurred: {0}", ce.Message)  
                selfHost.Abort()  
            End Try  
        End Sub  
    End Class  
  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="dccf0-170">このようなサービスには、リッスンを行うコンピューター上で HTTP アドレスを登録するためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="dccf0-170">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="dccf0-171">管理者アカウントにはこのアクセス許可がありますが、管理者以外のアカウントの場合は、HTTP 名前空間へのアクセス許可を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dccf0-171">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="dccf0-172">名前空間の予約を構成する方法については、「[Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)」 (HTTP と HTTPS を構成する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-172">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="dccf0-173">Visual Studio で service.exe を実行するには、管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="dccf0-173">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>  
  
 <span data-ttu-id="dccf0-174">これでサービスが実行されていることが確認できました。</span><span class="sxs-lookup"><span data-stu-id="dccf0-174">Now the service is running.</span></span> <span data-ttu-id="dccf0-175">[クライアントの作成方法](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)に関するページにお進みください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-175">Proceed to [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="dccf0-176">トラブルシューティングについては、「[Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)」 (チュートリアル入門のトラブルシューティング) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccf0-176">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dccf0-177">参照</span><span class="sxs-lookup"><span data-stu-id="dccf0-177">See Also</span></span>  
 [<span data-ttu-id="dccf0-178">はじめに</span><span class="sxs-lookup"><span data-stu-id="dccf0-178">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="dccf0-179">自己ホスト</span><span class="sxs-lookup"><span data-stu-id="dccf0-179">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
