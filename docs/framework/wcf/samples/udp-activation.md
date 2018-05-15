---
title: UDP アクティベーション
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 9f7600bff17c015f28c3fb94ed5360561d45c65b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="udp-activation"></a><span data-ttu-id="65f1b-102">UDP アクティベーション</span><span class="sxs-lookup"><span data-stu-id="65f1b-102">UDP Activation</span></span>
<span data-ttu-id="65f1b-103">このサンプルがに基づいて、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="65f1b-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="65f1b-104">拡張されて、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Windows プロセス アクティブ化サービス (WAS) を使用するプロセス アクティブ化をサポートするサンプルです。</span><span class="sxs-lookup"><span data-stu-id="65f1b-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="65f1b-105">サンプルは、次の 3 つの主要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-105">The sample consists of three major pieces:</span></span>  
  
-   <span data-ttu-id="65f1b-106">UDP プロトコル アクティベータ。アクティベーション対象のアプリケーションの代わりに UDP メッセージを受信するスタンドアロンのプロセスです。</span><span class="sxs-lookup"><span data-stu-id="65f1b-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
-   <span data-ttu-id="65f1b-107">UDP カスタム トランスポートを使用してメッセージを送信するクライアント。</span><span class="sxs-lookup"><span data-stu-id="65f1b-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
-   <span data-ttu-id="65f1b-108">UDP カスタム トランスポート経由でメッセージを受信するサービス。WAS によってアクティブ化されるワーカー プロセス内でホストされています。</span><span class="sxs-lookup"><span data-stu-id="65f1b-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="65f1b-109">UDP プロトコル アクティベータ</span><span class="sxs-lookup"><span data-stu-id="65f1b-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="65f1b-110">UDP プロトコル アクティベータは、WCF クライアントと WCF サービス間のブリッジです。</span><span class="sxs-lookup"><span data-stu-id="65f1b-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="65f1b-111">トランスポート層で UDP プロトコルを介するデータ通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="65f1b-112">主な機能は、次の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="65f1b-112">It has two major functions:</span></span>  
  
-   <span data-ttu-id="65f1b-113">WAS リスナ アダプタ (LA)。WAS と連携し、受信メッセージに応答してプロセスをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
-   <span data-ttu-id="65f1b-114">UDP プロトコル リスナ。アクティベーション対象のアプリケーションの代わりに UDP メッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="65f1b-115">このアクティベータは、サーバー コンピュータ上でスタンドアロン プログラムとして実行される必要があります。</span><span class="sxs-lookup"><span data-stu-id="65f1b-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="65f1b-116">通常、WAS リスナ アダプタ (NetTcpActivator や NetPipeActivator など) は、長時間にわたって実行される Windows サービスに実装されます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="65f1b-117">ただしこのサンプルでは、単純化してわかりやすくするために、このプロトコル アクティベータをスタンドアロン アプリケーションとして実装しています。</span><span class="sxs-lookup"><span data-stu-id="65f1b-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="65f1b-118">WAS リスナ アダプタ</span><span class="sxs-lookup"><span data-stu-id="65f1b-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="65f1b-119">UDP の WAS リスナ アダプタは `UdpListenerAdapter` クラスに実装されています。</span><span class="sxs-lookup"><span data-stu-id="65f1b-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="65f1b-120">これは WAS とやり取りするモジュールで、UDP プロトコル用アプリケーションのアクティベーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="65f1b-121">これは、次の Webhost API を呼び出すことによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="65f1b-122">このリスナ アダプタは、`WebhostRegisterProtocol` を最初に呼び出した後、applicationHost.config (%windir%\system32\inetsrv 内にあります) に登録されているすべてのアプリケーションの WAS からコールバック `ApplicationCreated` を受信します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="65f1b-123">このサンプルで処理するのは、(プロトコル ID が "net.udp" の) UDP プロトコルが有効なアプリケーションだけです。</span><span class="sxs-lookup"><span data-stu-id="65f1b-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="65f1b-124">他の実装でこのアプリケーションへの動的な構成変更 (アプリケーションを無効から有効に移行する場合など) に応答する場合、そうした実装では異なる方法でアプリケーションを処理することがあります。</span><span class="sxs-lookup"><span data-stu-id="65f1b-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="65f1b-125">コールバック `ConfigManagerInitializationCompleted` が受信される場合、WAS により、プロトコルの初期化に関するすべての通知が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="65f1b-126">その時点で、リスナ アダプタはアクティベーション要求を処理する準備ができています。</span><span class="sxs-lookup"><span data-stu-id="65f1b-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="65f1b-127">アプリケーションに初めて新しい要求が届くと、このリスナ アダプタは `WebhostOpenListenerChannelInstance` を WAS に呼び出します。ワーカー プロセスがまだ開始されていない場合は、これにより開始されます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="65f1b-128">次に、プロトコル ハンドラが読み込まれ、リスナ アダプタと仮想アプリケーション間の通信を開始できるようになります。</span><span class="sxs-lookup"><span data-stu-id="65f1b-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="65f1b-129">%SystemRoot%\System32\inetsrv\ApplicationHost.config にリスナー アダプターが登録されている、<`listenerAdapters`> には次のセクションします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="65f1b-130">プロトコル リスナ</span><span class="sxs-lookup"><span data-stu-id="65f1b-130">Protocol Listener</span></span>  
 <span data-ttu-id="65f1b-131">UDP プロトコル リスナはプロトコル アクティベータ内部のモジュールで、仮想アプリケーションの代わりに UDP エンドポイントでリッスンします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="65f1b-132">これは `UdpSocketListener` クラスに実装されています。</span><span class="sxs-lookup"><span data-stu-id="65f1b-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="65f1b-133">エンドポイントは `IPEndpoint` として表され、このポート番号はサイトのプロトコルのバインディングから抽出されます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="65f1b-134">サービスの制御</span><span class="sxs-lookup"><span data-stu-id="65f1b-134">Control Service</span></span>  
 <span data-ttu-id="65f1b-135">このサンプルでは、WCF を使用してアクティベータと WAS ワーカー プロセスの間で通信するためにします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="65f1b-136">アクティベータに存在するサービスは、コントロール サービスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="65f1b-137">プロトコル ハンドラー</span><span class="sxs-lookup"><span data-stu-id="65f1b-137">Protocol Handlers</span></span>  
 <span data-ttu-id="65f1b-138">リスナ アダプタが `WebhostOpenListenerChannelInstance` を呼び出した後、ワーカー プロセスが開始されていない場合は WAS プロセス マネージャによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="65f1b-139">ワーカー プロセス内部のアプリケーション マネージャは、UDP プロセス プロトコル ハンドラ (PPH) を読み込み、`ListenerChannelId` を要求します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="65f1b-140">次に呼び出して、PPH`IAdphManager`です。`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="65f1b-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="65f1b-141">UDP AppDomain プロトコル ハンドラ (ADPH) を開始します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="65f1b-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="65f1b-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="65f1b-143">この情報は、Web.config で次のように登録されます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="65f1b-144">このサンプルの特殊なセットアップ</span><span class="sxs-lookup"><span data-stu-id="65f1b-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="65f1b-145">このサンプルは、Windows Vista、Windows Server 2008、または Windows 7 でのみビルドおよび実行可能です。</span><span class="sxs-lookup"><span data-stu-id="65f1b-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="65f1b-146">サンプルを実行するには、最初にすべてのコンポーネントを正しくセットアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="65f1b-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="65f1b-147">サンプルをインストールするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="65f1b-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="65f1b-148">このサンプルをセットアップするには</span><span class="sxs-lookup"><span data-stu-id="65f1b-148">To set up this sample</span></span>  
  
1.  <span data-ttu-id="65f1b-149">次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-149">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="65f1b-150">Windows Vista でプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="65f1b-151">コンパイル後、ビルド後のフェーズで次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    -   <span data-ttu-id="65f1b-152">UDP バインディングを [既定の Web サイト] のサイトにインストールします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    -   <span data-ttu-id="65f1b-153">物理パス "%SystemDrive%\inetpub\wwwroot\servicemodelsamples" をポイントする、仮想アプリケーション "ServiceModelSamples" を作成します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    -   <span data-ttu-id="65f1b-154">さらに、この仮想アプリケーションの "net.udp" プロトコルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3.  <span data-ttu-id="65f1b-155">ユーザー インターフェイス アプリケーション "WasNetActivator.exe" を起動します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="65f1b-156">クリックして、**セットアップ** タブで、次のチェック ボックスをオンにし、をクリックして**インストール**それらをインストールします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    -   <span data-ttu-id="65f1b-157">UDP リスナ アダプタ</span><span class="sxs-lookup"><span data-stu-id="65f1b-157">UDP Listener Adapter</span></span>  
  
    -   <span data-ttu-id="65f1b-158">UDP プロトコル ハンドラ</span><span class="sxs-lookup"><span data-stu-id="65f1b-158">UDP Protocol Handlers</span></span>  
  
4.  <span data-ttu-id="65f1b-159">をクリックして、**アクティベーション**のユーザー インターフェイス アプリケーション"WasNetActivator.exe"のタブです。</span><span class="sxs-lookup"><span data-stu-id="65f1b-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="65f1b-160">をクリックして、**開始**リスナー アダプターを開始するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="65f1b-161">これで、プログラムを実行する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="65f1b-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65f1b-162">このサンプルの実行後は、Cleanup.bat を実行して、[既定の Web サイト] から net.udp バインディングを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65f1b-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="65f1b-163">サンプルの使用方法</span><span class="sxs-lookup"><span data-stu-id="65f1b-163">Sample Usage</span></span>  
 <span data-ttu-id="65f1b-164">コンパイル後、次の 4 つの異なるバイナリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-164">After compilation, there are four different binaries generated:</span></span>  
  
-   <span data-ttu-id="65f1b-165">Client.exe: クライアント コード。</span><span class="sxs-lookup"><span data-stu-id="65f1b-165">Client.exe: The client code.</span></span> <span data-ttu-id="65f1b-166">App.config は、クライアント構成ファイルの Client.exe.config にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
-   <span data-ttu-id="65f1b-167">UDPActivation.dll: 主要なすべての UDP 実装を含むライブラリ。</span><span class="sxs-lookup"><span data-stu-id="65f1b-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
-   <span data-ttu-id="65f1b-168">Service.dll: サービス コード。</span><span class="sxs-lookup"><span data-stu-id="65f1b-168">Service.dll: The service code.</span></span> <span data-ttu-id="65f1b-169">これは、ServiceModelSamples 仮想アプリケーションの \bin ディレクトリにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="65f1b-170">このサービス ファイルは Service.svc で、構成ファイルは Web.config です。これらをコンパイルすると、%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
-   <span data-ttu-id="65f1b-171">WasNetActivator: UDP アクティベータ プログラム。</span><span class="sxs-lookup"><span data-stu-id="65f1b-171">WasNetActivator: The UDP activator program.</span></span>  
  
-   <span data-ttu-id="65f1b-172">必要なすべての要素が正しくインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="65f1b-173">サンプルを実行する方法を、次の手順に示します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-173">The following steps show how to run the sample:</span></span>  
  
1.  <span data-ttu-id="65f1b-174">次の Windows サービスが開始されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-174">Ensure that the following Windows services have been started:</span></span>  
  
    -   <span data-ttu-id="65f1b-175">Windows プロセス アクティブ化サービス (WAS)。</span><span class="sxs-lookup"><span data-stu-id="65f1b-175">Windows Process Activation Service (WAS).</span></span>  
  
    -   <span data-ttu-id="65f1b-176">インターネット インフォメーション サービス (IIS): W3SVC。</span><span class="sxs-lookup"><span data-stu-id="65f1b-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2.  <span data-ttu-id="65f1b-177">次に、アクティベータ WasNetActivator.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="65f1b-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="65f1b-178">下にある、**アクティブ化** タブ、唯一のプロトコル**UDP**、ドロップ ダウン リストで選択しました。</span><span class="sxs-lookup"><span data-stu-id="65f1b-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="65f1b-179">をクリックして、**開始**アクティベーターを起動するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="65f1b-179">Click the **Start** button to start the activator.</span></span>  
  
3.  <span data-ttu-id="65f1b-180">アクティベータが開始されると、コマンド ウィンドウで Client.exe を実行することにより、クライアント コードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="65f1b-181">このサンプルの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="65f1b-181">The following is the sample output:</span></span>  
  
    ```  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="65f1b-182">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="65f1b-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="65f1b-183">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="65f1b-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="65f1b-184">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="65f1b-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="65f1b-185">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="65f1b-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a><span data-ttu-id="65f1b-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="65f1b-186">See Also</span></span>
