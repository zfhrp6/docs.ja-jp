---
title: NamedPipe アクティベーション
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 46b59dab0f67c66ca364d9e880ef519386d0df94
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806384"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="bb2e0-102">NamedPipe アクティベーション</span><span class="sxs-lookup"><span data-stu-id="bb2e0-102">NamedPipe Activation</span></span>
<span data-ttu-id="bb2e0-103">このサンプルでは、名前付きパイプを介して通信するサービスをアクティブ化するために、Windows プロセス アクティブ化サービス (WAS: Windows Process Activation Service) を使用してサービスをホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="bb2e0-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)する必要があります[!INCLUDE[wv](../../../../includes/wv-md.md)]を実行します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and requires [!INCLUDE[wv](../../../../includes/wv-md.md)] to run.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb2e0-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bb2e0-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bb2e0-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bb2e0-108">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bb2e0-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="bb2e0-110">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="bb2e0-110">Sample Details</span></span>  
 <span data-ttu-id="bb2e0-111">このサンプルは、クライアント コンソール プログラム (.exe) と、Windows プロセス アクティブ化サービス (WAS) によってアクティブ化されるワーカー プロセス内でホストされるサービス ライブラリ (.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="bb2e0-112">クライアント アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-112">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="bb2e0-113">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="bb2e0-114">コントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (Add、Subtract、Multiply、および Divide) を公開しています。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
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
```  
  
 <span data-ttu-id="bb2e0-115">クライアントは指定された算術演算を同期要求し、サービスの実装は計算を行って結果を返します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>  
  
```  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="bb2e0-116">このサンプルでは、セキュリティ保護を行わないように変更された `netNamedPipeBinding` バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="bb2e0-117">バインディングは、クライアントとサービスの構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="bb2e0-118">サービスのバインディングの種類は、エンドポイント要素の `binding` 属性に指定されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
 <span data-ttu-id="bb2e0-119">セキュリティ保護された名前付きパイプ バインディングを使用する場合は、サーバーのセキュリティ モードを必要なセキュリティ設定に変更し、クライアントで svcutil.exe を再実行して更新されたクライアントの構成ファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
  
        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->  
        <endpoint address=""   
                  binding="netNamedPipeBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexNamedPipeBinding"  
                  contract="IMetadataExchange" />  
      </service>  
        </services>      
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="Binding1" >  
                    <security mode = "None">  
                    </security>  
                </binding >  
            </netNamedPipeBinding>  
        </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="bb2e0-120">クライアントのエンドポイント情報が構成されます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <endpoint name=""  
                          address="net.pipe://localhost/servicemodelsamples/service.svc"   
                          binding="netNamedPipeBinding"   
                          bindingConfiguration="Binding1"   
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
    <bindings>  
  
      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.  
            Each property is configured with the default value.   -->  
  
      <netNamedPipeBinding>  
        <binding name="Binding1"   
                         maxBufferSize="65536"  
                         maxConnections="10">  
          <security mode = "None">  
          </security>  
        </binding >  
  
      </netNamedPipeBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="bb2e0-121">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bb2e0-122">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bb2e0-123">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="bb2e0-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bb2e0-124">[!INCLUDE[iisver](../../../../includes/iisver-md.md)] がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-124">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)]<span data-ttu-id="bb2e0-125"> は WAS のアクティブ化に必要です。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-125"> is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="bb2e0-126">確実に実行する、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
     <span data-ttu-id="bb2e0-127">さらに、WCF 非 HTTP アクティブ化コンポーネントをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-127">In addition, you must install the WCF non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="bb2e0-128">**開始** メニューの 選択**コントロール パネルの **です。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-128">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="bb2e0-129">選択**プログラムと機能**します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-129">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="bb2e0-130">をクリックして**Windows コンポーネントをオンまたはオフ**です。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-130">Click **Turn Windows Components on or Off**.</span></span>  
  
    4.  <span data-ttu-id="bb2e0-131">展開して、 **Microsoft .NET Framework 3.0**ノードとチェック、 **Windows Communication Foundation NON-HTTP Activation**機能します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="bb2e0-132">名前付きパイプのアクティブ化をサポートするように Windows プロセス アクティブ化サービス (WAS) を構成します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>  
  
     <span data-ttu-id="bb2e0-133">便宜上、次の 2 つの手順が、サンプル ディレクトリにある AddNetPipeSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="bb2e0-134">net.pipe のアクティブ化をサポートするには、既定の Web サイトをあらかじめ net.pipe プロトコルにバインドしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="bb2e0-135">これは、IIS7.0 管理ツール セットと共にインストールされる appcmd.exe を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="bb2e0-136">権限のレベルが高い (管理者の) コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-136">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="bb2e0-137">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-137">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="bb2e0-138">このコマンドによって、既定の Web サイトに net.pipe サイト バインディングを追加します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-138">This command adds a net.pipe site binding to the default Web site.</span></span>  
  
    2.  <span data-ttu-id="bb2e0-139">サイト内のすべてのアプリケーションが同じ net.pipe バインディングを共有しますが、net.pipe サポートの有効化はアプリケーションごとに指定できます。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="bb2e0-140">/servicemodelsamples アプリケーションで net.pipe を有効にするには、権限のレベルが高いコマンド プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="bb2e0-141">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-141">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="bb2e0-142">このコマンドにより、/servicemodelsamples アプリケーションに両方を使用してアクセスして http://localhost/servicemodelsamples と net.tcp://localhost/servicemodelsamples です。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-142">This command enables the /servicemodelsamples application to be accessed using both http://localhost/servicemodelsamples and net.tcp://localhost/servicemodelsamples.</span></span>  
  
4.  <span data-ttu-id="bb2e0-143">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="bb2e0-144">このサンプル用に追加した net.pipe サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-144">Remove the net.pipe site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="bb2e0-145">便宜上、次の 2 つの手順が、サンプル ディレクトリにある RemoveNetPipeSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>  
  
    1.  <span data-ttu-id="bb2e0-146">権限のレベルが高いコマンド プロンプトから次のコマンドを実行して、有効なプロトコルの一覧から net.tcp を削除します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="bb2e0-147">このコマンドは、全体で 1 行のテキストになるように入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-147">This command must be entered as a single line of text.</span></span>  
  
    2.  <span data-ttu-id="bb2e0-148">権限のレベルが高いコマンド プロンプトから次のコマンドを実行して、net.tcp サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="bb2e0-149">このコマンドは、全体で 1 行のテキストになるように入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb2e0-149">This command must be typed in as a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2e0-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb2e0-150">See Also</span></span>  
 [<span data-ttu-id="bb2e0-151">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="bb2e0-151">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
