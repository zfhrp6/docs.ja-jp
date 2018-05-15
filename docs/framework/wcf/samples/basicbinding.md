---
title: BasicBinding
ms.date: 03/30/2017
ms.assetid: 86fbeb87-4d89-4b61-9577-867e0ac12945
ms.openlocfilehash: 91ebef7ec985d3da6dc563ddbaa277d25f3172cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="basicbinding"></a><span data-ttu-id="1a0f0-102">BasicBinding</span><span class="sxs-lookup"><span data-stu-id="1a0f0-102">BasicBinding</span></span>
<span data-ttu-id="1a0f0-103">このサンプルでは、第 1 世代と第 2 世代の Web サービスで HTTP 通信と最大限の相互運用性を実現する、`basicHttpBinding` の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-103">This sample demonstrates the use of `basicHttpBinding` that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a0f0-104">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-104">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1a0f0-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1a0f0-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1a0f0-107">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a0f0-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\Http`  
  
## <a name="sample-details"></a><span data-ttu-id="1a0f0-109">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="1a0f0-109">Sample Details</span></span>  
 <span data-ttu-id="1a0f0-110">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-110">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
 <span data-ttu-id="1a0f0-111">既定の動作で基本的なバインディングを使用する場合、必要なものはバインディング セクション名だけです。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-111">To use the basic binding with default behavior, only the binding section name is required.</span></span> <span data-ttu-id="1a0f0-112">基本的なバインディングを構成してその設定の一部を変更する場合は、バインディング構成を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-112">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="1a0f0-113">エンドポイントを使用して名前でバインド構成を参照する必要があります、`bindingConfiguration`の属性、<`endpoint`> 要素を次のサンプル コードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-113">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the <`endpoint`> element, as shown in the following sample code.</span></span>  
  
```xml  
<services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
</services>  
```  
  
 <span data-ttu-id="1a0f0-114">このサンプルでは、バインディング構成の名前は `"Binding1"` です。これは次のコード例のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-114">In this sample, the binding configuration is named `"Binding1"` and is defined as shown in the following code example.</span></span>  
  
```xml  
<bindings>  
   <basicHttpBinding>  
      <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
         <security mode="None" />  
      </binding>  
   </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="1a0f0-115">バインド要素には、ホスト名比較モード、最大メッセージ サイズ、プロキシ オプション、タイムアウト、メッセージ エンコーディングなど、さまざまなオプションを設定するための属性が用意されています。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-115">The binding element provides attributes for setting the host name comparison mode, maximum message size, proxy options, timeouts, message encoding, and other options.</span></span>  
  
 <span data-ttu-id="1a0f0-116">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1a0f0-117">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1a0f0-118">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="1a0f0-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1a0f0-119">次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-119">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="1a0f0-120">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="1a0f0-121">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="1a0f0-122">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0f0-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a0f0-123">See Also</span></span>
