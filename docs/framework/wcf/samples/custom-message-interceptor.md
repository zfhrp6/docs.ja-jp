---
title: "カスタム メッセージ インターセプター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f7774af6c1531e48be29351299555a650548687f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="12c3a-102">カスタム メッセージ インターセプター</span><span class="sxs-lookup"><span data-stu-id="12c3a-102">Custom Message Interceptor</span></span>
<span data-ttu-id="12c3a-103">このサンプルでは、チャネル拡張モデルの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="12c3a-104">特に、チャネル ファクトリとチャネル リスナーを作成するカスタム バインディング要素を実装して、ランタイム スタックの特定のポイントですべての送受信メッセージを中断する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="12c3a-105">また、このサンプルには、こうしたカスタム ファクトリの使用方法を示すクライアントとサーバーも含まれます。</span><span class="sxs-lookup"><span data-stu-id="12c3a-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="12c3a-106">このサンプルでは、クライアントとサービスは両方ともコンソール プログラム (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="12c3a-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="12c3a-107">そして、これらのクライアントとサービスの両方で、カスタム バインディング要素およびこれに関連付けられたランタイム オブジェクトを含む共通ライブラリ (.dll) を使用します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12c3a-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12c3a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="12c3a-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="12c3a-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="12c3a-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="12c3a-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="12c3a-111">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="12c3a-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="12c3a-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="12c3a-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="12c3a-113">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でカスタム階層チャネルを作成するための推奨手順について説明します。作成時には、チャネル フレームワークと次に示す [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のベスト プラクティスを使用します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-113">The sample describes the recommended procedure for creating a custom layered channel in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], by using the channel framework and following [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] best practices.</span></span> <span data-ttu-id="12c3a-114">カスタム階層チャネルを作成する手順は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12c3a-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1.  <span data-ttu-id="12c3a-115">どのチャネル形状をチャネル ファクトリおよびチャネル リスナがサポートするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2.  <span data-ttu-id="12c3a-116">チャネル形状をサポートするチャネル ファクトリおよびチャネル リスナを作成します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3.  <span data-ttu-id="12c3a-117">チャネル スタックにカスタム階層チャネルを追加するバインディング要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4.  <span data-ttu-id="12c3a-118">バインド要素拡張セクションを追加して、新しいバインド要素を構成システムに公開します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="12c3a-119">チャネル形状</span><span class="sxs-lookup"><span data-stu-id="12c3a-119">Channel Shapes</span></span>  
 <span data-ttu-id="12c3a-120">カスタム階層チャネルを記述する最初の手順として、どの形状がチャネルに必要かを判断します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="12c3a-121">メッセージ インスペクタの場合、下のレイヤでサポートされる任意の形状をサポートします (たとえば、下のレイヤで <xref:System.ServiceModel.Channels.IOutputChannel> と <xref:System.ServiceModel.Channels.IDuplexSessionChannel> が作成できる場合は、<xref:System.ServiceModel.Channels.IOutputChannel> と <xref:System.ServiceModel.Channels.IDuplexSessionChannel> を公開します)。</span><span class="sxs-lookup"><span data-stu-id="12c3a-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="12c3a-122">チャネル ファクトリとリスナ ファクトリ</span><span class="sxs-lookup"><span data-stu-id="12c3a-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="12c3a-123">カスタム階層チャネルを記述する次の手順では、クライアント チャネルでの <xref:System.ServiceModel.Channels.IChannelFactory> の実装とサービス チャネルでの <xref:System.ServiceModel.Channels.IChannelListener> の実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="12c3a-124">これらのクラスでは、内部ファクトリとリスナが取得され、この内部ファクトリとリスナが `OnCreateChannel` と `OnAcceptChannel` 以外のすべての呼び出しを代行します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="12c3a-125">バインディング要素の追加</span><span class="sxs-lookup"><span data-stu-id="12c3a-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="12c3a-126">このサンプルでは、`InterceptingBindingElement` というカスタム バインディング要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="12c3a-127">`InterceptingBindingElement``ChannelMessageInterceptor`は入力としてこれを使用して`ChannelMessageInterceptor`通過するメッセージを操作します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="12c3a-128">公開する必要があるクラスはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="12c3a-128">This is the only class that must be public.</span></span> <span data-ttu-id="12c3a-129">ファクトリ、リスナ、およびチャネルはすべて、ランタイム パブリック インターフェイスの内部実装として設定できます。</span><span class="sxs-lookup"><span data-stu-id="12c3a-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="12c3a-130">構成サポートの追加</span><span class="sxs-lookup"><span data-stu-id="12c3a-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="12c3a-131">バインディング構成と統合するには、ライブラリで、構成セクション ハンドラをバインディング要素拡張セクションとして定義します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="12c3a-132">クライアントとサーバーの構成ファイルでは、バインディング要素拡張を構成システムに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12c3a-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="12c3a-133">バインディング要素を構成システムに公開する実装は、このクラスから派生できます。</span><span class="sxs-lookup"><span data-stu-id="12c3a-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a><span data-ttu-id="12c3a-134">ポリシーの追加</span><span class="sxs-lookup"><span data-stu-id="12c3a-134">Adding Policy</span></span>  
 <span data-ttu-id="12c3a-135">ポリシー システムと統合するには、`InterceptingBindingElement` に IPolicyExportExtension を実装し、ポリシーの生成に参加する必要があることを通知します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="12c3a-136">生成されたクライアント上でポリシーのインポートをサポートするには、`InterceptingBindingElementImporter` の派生クラスを登録し、`CreateMessageInterceptor`() をオーバーライドして、ポリシーが有効なそれらの `ChannelMessageInterceptor` クラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="12c3a-137">例 : 破棄可能なメッセージ インスペクタ</span><span class="sxs-lookup"><span data-stu-id="12c3a-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="12c3a-138">このサンプルには、メッセージを破棄する `ChannelMessageInspector` の実装例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="12c3a-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="12c3a-139">この例には、次のように構成からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="12c3a-139">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="12c3a-140">クライアントとサーバーでは、両方ともこの新しく作成された構成セクションを使用して、カスタム ファクトリをランタイム チャネル スタックの最低レベル (トランスポート レベルの上) に挿入します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="12c3a-141">クライアントでは `MessageInterceptor` ライブラリを使用して、カスタム ヘッダーを偶数番号付きメッセージに追加します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="12c3a-142">一方、サービスでは `MessageInterceptor` ライブラリを使用して、この特殊なヘッダーを持たないメッセージを削除します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="12c3a-143">サービスを実行し、次にクライアントを実行すると、次のクライアント出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="12c3a-143">You should see the following client output after running the service and then the client.</span></span>  
  
```  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="12c3a-144">クライアントからは 10 種類の異なる風速がサービスに報告されますが、特殊なヘッダーがあるのはそれらのタグの半分だけです。</span><span class="sxs-lookup"><span data-stu-id="12c3a-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="12c3a-145">サービスには、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="12c3a-145">On the service, you should see the following output:</span></span>  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="12c3a-146">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="12c3a-146">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="12c3a-147">次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="12c3a-147">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="12c3a-148">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="12c3a-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="12c3a-149">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="12c3a-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="12c3a-150">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="12c3a-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="12c3a-151">最初に Service.exe を実行して次に Client.exe を実行し、両方のコンソール ウィンドウで出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="12c3a-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c3a-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="12c3a-152">See Also</span></span>
