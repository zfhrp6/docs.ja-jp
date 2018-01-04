---
title: "永続的な二重"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1298f150709b48f18de654be2ab17adfdcbf42a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="durable-duplex"></a><span data-ttu-id="1e4c3-102">永続的な二重</span><span class="sxs-lookup"><span data-stu-id="1e4c3-102">Durable Duplex</span></span>
<span data-ttu-id="1e4c3-103">このサンプルでは、[!INCLUDE[wf](../../../../includes/wf-md.md)] のメッセージング アクティビティを使用して、永続的な双方向メッセージ交換を設定および構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-103">This sample demonstrates how to set up and configure durable duplex message exchange using the messaging activities in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span> <span data-ttu-id="1e4c3-104">永続的な双方向メッセージ交換は、長期間行われる双方向メッセージ交換です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-104">A durable duplex message exchange is a two-way message exchange that takes place over a long period of time.</span></span> <span data-ttu-id="1e4c3-105">メッセージ交換の有効期間は、通信チャネルの有効期間およびサービス インスタンスのメモリ内有効期間よりも長い場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-105">The lifetime of the message exchange may be longer than the lifetime of the communication channel and the in-memory lifetime of the service instances.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="1e4c3-106">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="1e4c3-106">Sample Details</span></span>  
 <span data-ttu-id="1e4c3-107">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して実装された 2 つの [!INCLUDE[wf2](../../../../includes/wf2-md.md)] サービスで、永続的な双方向メッセージ交換を構成します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-107">In this sample, two [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services implemented using [!INCLUDE[wf2](../../../../includes/wf2-md.md)] are configured to have a durable duplex message exchange.</span></span> <span data-ttu-id="1e4c3-108">永続的な双方向メッセージ交換が MSMQ 経由で送信され、関連するを使用して 2 つの一方向のメッセージから構成される[.NET コンテキスト交換](http://go.microsoft.com/fwlink/?LinkID=166059)です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-108">The durable duplex message exchange is composed from two one-way messages sent over MSMQ and correlated using [.NET Context Exchange](http://go.microsoft.com/fwlink/?LinkID=166059).</span></span> <span data-ttu-id="1e4c3-109">これらのメッセージは、<xref:System.ServiceModel.Activities.Send> メッセージング アクティビティと <xref:System.ServiceModel.Activities.Receive> メッセージング アクティビティを使用して送信されます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-109">The messages are sent using the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.Receive> messaging activities.</span></span> <span data-ttu-id="1e4c3-110">.NET コンテキスト交換は、送信メッセージに対してコールバック アドレスを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-110">.NET Context Exchange is use to specify the callback address on the sent messages.</span></span> <span data-ttu-id="1e4c3-111">どちらのサービスも Windows プロセス アクティブ化サービス (WAS) を使用してホストされ、サービス インスタンスの永続化を有効にするように構成されます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-111">Both services are hosted using Windows Process Activation Services (WAS) and are configured to enable persistence of the services instances.</span></span>  
  
 <span data-ttu-id="1e4c3-112">1 つ目のサービス (Service1.xamlx) は、処理を実行する送信サービス (Service2.xamlx) に要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-112">The first service (Service1.xamlx) sends a request to the send service (Service2.xamlx) to do some work.</span></span> <span data-ttu-id="1e4c3-113">処理が完了したら、Service2.xamlx は、処理が完了したことを示す通知を Service1.xamlx に送り返します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-113">Once the work is completed, Service2.xamlx sends a notification back to Service1.xamlx to indicate that the work has been completed.</span></span> <span data-ttu-id="1e4c3-114">ワークフロー コンソール アプリケーションによって、サービスがリッスンするキューが設定され、Service1.xamlx をアクティブ化するために最初の開始メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-114">A workflow console application sets up the queues that the services are listening on and sends the initial Start message to activate Service1.xamlx.</span></span> <span data-ttu-id="1e4c3-115">Service1.xamlx は、要求した処理が完了したことを示す通知を Service2.xamlx から受け取ったら、結果を XML ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-115">Once Service1.xamlx receives the notification from Service2.xamlx that the requested work has been completed, Service1.xamlx saves the result to an XML file.</span></span> <span data-ttu-id="1e4c3-116">コールバック メッセージを待機している間、Service1.xamlx は既定の <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> を使用してインスタンスの状態を永続化します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-116">While waiting for the callback message, Service1.xamlx persists its instance state using the default <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span></span> <span data-ttu-id="1e4c3-117">Service2.xamlx は、Service1.xamlx によって要求された処理を完了する一環としてインスタンスの状態を永続化します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-117">Service2.xamlx persists its instance state as part of completing the work requested by Service1.xamlx.</span></span>  
  
 <span data-ttu-id="1e4c3-118">MSMQ を介して .NET コンテキスト交換を使用するようにサービスを構成するために、<xref:System.ServiceModel.Channels.ContextBindingElement> と <xref:System.ServiceModel.Channels.MsmqTransportBindingElement> から成るカスタム バインディングを使用するように両方のサービスが構成されます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-118">To configure the services to use .NET Context Exchange over MSMQ, both services are configured to use a custom binding that consists of the <xref:System.ServiceModel.Channels.ContextBindingElement> and the <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span></span> <span data-ttu-id="1e4c3-119"><xref:System.ServiceModel.Channels.ContextBindingElement> ではコールバック アドレスが指定され、カスタム バインディングを使用して送信されるすべてのメッセージのコールバック コンテキスト ヘッダーに含まれます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-119">A callback address is specified with the <xref:System.ServiceModel.Channels.ContextBindingElement> and is included in a callback context header with all messages sent using a custom binding.</span></span> <span data-ttu-id="1e4c3-120">カスタム バインディングを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-120">The following code example defines the custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="1e4c3-121">このサンプルで使用するバインディングはセキュリティで保護されていません。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-121">The binding used by this sample is not secure.</span></span> <span data-ttu-id="1e4c3-122">アプリケーションを配置するときに、アプリケーションのセキュリティ要件に基づいてバインディングを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-122">When deploying your application you should configure your binding based on the security requirements of your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e4c3-123">このサンプルで使用するキューはトランザクション キューではありません。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-123">The queues used in this sample are not transactional.</span></span> <span data-ttu-id="1e4c3-124">セットアップする方法を示すサンプルについて[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]トランザクション キューを使用して交換のメッセージを参照してください、 [MSMQ アクティブ化](../../../../docs/framework/wcf/samples/msmq-activation.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-124">For a sample that shows how to set up [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message exchanges using transaction queues, see the [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md) sample.</span></span>  
  
 <span data-ttu-id="1e4c3-125">Service1.xamlx によって Service2.xamlx に送信されるメッセージは、Service2.xamlx のアドレスと前に定義したカスタム バインドを使用して構成されるクライアント エンドポイントを使用して送信されます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-125">The message sent by Service1.xamlx to Service2.xamlx is sent using a client endpoint configured with the address of Service2.xamlx and the custom binding defined previously.</span></span> <span data-ttu-id="1e4c3-126">Service2.xamlx から Service1.xamlx へのコールバックは、アドレスが明示的に構成されていないクライアント エンドポイントを使用して送信されます。アドレスは、Service1.xamlx によって送信されるコールバック コンテキストから取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-126">The callback from Service2.xamlx to Service1.xamlx is sent using a client endpoint with no explicitly configured address because the address is taken from the callback context sent by Service1.xamlx.</span></span> <span data-ttu-id="1e4c3-127">クライアント エンドポイントを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-127">The following code example defines the client endpoints.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1e4c3-128">このカスタム バインディングを使用するように net.msmq ベース アドレスの既定のプロトコル マッピングを変更することで、このカスタム バインディングを使用するエンドポイントを公開するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-128">The following code example exposes endpoints using this custom binding by changing the default protocol mapping for net.msmq base addresses to use this custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1e4c3-129"><xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> の動作を両方のサービスに追加して永続性データベースの接続文字列を指定することで、両方のサービスの永続化を有効にするコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-129">The following code example enables persistence for both services by adding the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior to both services and specifying the connection string for the persistence database.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a><span data-ttu-id="1e4c3-130">システム要件</span><span class="sxs-lookup"><span data-stu-id="1e4c3-130">System Requirements</span></span>  
 <span data-ttu-id="1e4c3-131">このサンプルには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-131">This sample requires the following components.</span></span>  
  
1.  <span data-ttu-id="1e4c3-132">インターネット インフォメーション サービス。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-132">Internet Information Services.</span></span>  
  
2.  <span data-ttu-id="1e4c3-133">[Internet Information Services] -> [IIS 6 と互換性のある管理] -> [IIS メタベースおよび IIS 6 構成との互換性]。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-133">Internet Information Services -> IIS 6.0 Management Compatibility -> IIS Metabase and IIS 6.0 configuration compatibility.</span></span>  
  
3.  <span data-ttu-id="1e4c3-134">[World Wide Web サービス] -> [アプリケーション開発機能] -> [ASP.NET]。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-134">World Wide Web Services -> Application Development Features -> ASP.NET.</span></span>  
  
4.  <span data-ttu-id="1e4c3-135">Microsoft メッセージ キュー (MSMQ) サーバー。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-135">Microsoft Message Queues (MSMQ) Server.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1e4c3-136">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="1e4c3-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="1e4c3-137">永続性データベースと結果ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-137">Set up the persistence database and the results directory.</span></span>  
  
    1.  <span data-ttu-id="1e4c3-138">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-138">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="1e4c3-139">このサンプルのフォルダーに移動して Setup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-139">Navigate to the folder for this sample and run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="1e4c3-140">仮想アプリケーションを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-140">Set up the virtual application.</span></span>  
  
    1.  <span data-ttu-id="1e4c3-141">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトから次のコマンドを実行し、ASP.NET を登録します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-141">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by running the following command.</span></span>  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  <span data-ttu-id="1e4c3-142">実行[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックして、管理者権限を持つ[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を選択して**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-142">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator permissions by right-clicking [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and selecting **Run as administrator**.</span></span>  
  
    3.  <span data-ttu-id="1e4c3-143">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、DurableDuplex.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-143">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DurableDuplex.sln file.</span></span>  
  
3.  <span data-ttu-id="1e4c3-144">サービス キューを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-144">Set up the service queues.</span></span>  
  
    1.  <span data-ttu-id="1e4c3-145">DurableDuplex クライアントを実行するために、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-145">To run the DurableDuplex client, press F5.</span></span>  
  
    2.  <span data-ttu-id="1e4c3-146">開く、**コンピューターの管理**コンソールを実行して`Compmgmt.msc`コマンド プロンプトからです。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-146">Open the **Computer Management** console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    3.  <span data-ttu-id="1e4c3-147">展開**サービスとアプリケーション**、**メッセージ キュー**です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-147">Expand **Service and Applications**, **Message Queuing**.</span></span> <span data-ttu-id="1e4c3-148">**専用キュー**です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-148">**Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="1e4c3-149">Durableduplex/service1.xamlx キューと durableduplex/service2.xamlx キューを右クリックし **プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-149">Right-click the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues and select **Properties**.</span></span>  
  
    5.  <span data-ttu-id="1e4c3-150">選択、**セキュリティ**でき、タブ**Everyone メッセージの受信**、**メッセージのピーク**と**メッセージの送信**両方のキューのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-150">Select the **Security** tab and allow **Everyone Receive Message**, **Peek Message** and **Send Message** permissions for both queues.</span></span>  
  
    6.  <span data-ttu-id="1e4c3-151">インターネット インフォメーション サービス (IIS) マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-151">Open Internet Information Services (IIS) Manager.</span></span>  
  
    7.  <span data-ttu-id="1e4c3-152">参照**サーバー**、**サイト**、**既定の Web サイト**、**プライベート**、**永続的な二重**を選択**Advanced Options**です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-152">Browse to **Server**, **Sites**, **Default Web site**, **private**, **Durable Duplex** and select **Advanced Options**.</span></span>  
  
    8.  <span data-ttu-id="1e4c3-153">変更、**有効なプロトコル**に**http, net.msmq**です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-153">Change the **Enabled Protocols** to **http,net.msmq**.</span></span>  
  
4.  <span data-ttu-id="1e4c3-154">サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-154">Run the sample.</span></span>  
  
    1.  <span data-ttu-id="1e4c3-155">http://localhost/private/durableduplex/service1.xamlx および http://localhost/private/durableduplex/service2.xamlx を参照し、両方のサービスが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-155">Browse to http://localhost/private/durableduplex/service1.xamlx and http://localhost/private/durableduplex/service2.xamlx to ensure that both services are running.</span></span>  
  
    2.  <span data-ttu-id="1e4c3-156">F5 キーを押して DurableDuplexClient を実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-156">Press F5 to run DurableDuplexClient.</span></span>  
  
         <span data-ttu-id="1e4c3-157">永続的な双方向メッセージ交換が完了したら、メッセージ交換の結果を示す result.xml ファイルが C:\Inbox フォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-157">When the durable duplex message exchange completes a result.xml file is saved to the C:\Inbox folder and contains the result of the message exchange.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="1e4c3-158">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="1e4c3-158">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="1e4c3-159">Cleanup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-159">Run Cleanup.cmd.</span></span>  
  
    1.  <span data-ttu-id="1e4c3-160">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-160">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="1e4c3-161">このサンプルのフォルダーに移動して Cleanup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-161">Navigate to the folder for this sample and run Cleanup.cmd.</span></span>  
  
2.  <span data-ttu-id="1e4c3-162">サービスの仮想アプリケーションを削除します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-162">Remove the virtual application for the services.</span></span>  
  
    1.  <span data-ttu-id="1e4c3-163">実行して、インターネット インフォメーション サービス (IIS) マネージャーを開く`Inetmgr.exe`コマンド プロンプトからです。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-163">Open the Internet Information Services (IIS) Manager by running `Inetmgr.exe` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="1e4c3-164">既定の Web サイトを参照し、削除、**プライベート**仮想ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-164">Browse to the default Web site and remove the **private** virtual directory.</span></span>  
  
3.  <span data-ttu-id="1e4c3-165">このサンプルに対して設定されているキューを削除します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-165">Remove the queues set up for this sample.</span></span>  
  
    1.  <span data-ttu-id="1e4c3-166">実行して、コンピューターの管理コンソールを開きます`Compmgmt.msc`コマンド プロンプトからです。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-166">Open the Computer Management console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="1e4c3-167">展開**サービスとアプリケーション**、**メッセージ キュー**、**専用キュー**です。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-167">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    3.  <span data-ttu-id="1e4c3-168">durableduplex/service1.xamlx キューと durableduplex/service2.xamlx キューを削除します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-168">Delete the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues.</span></span>  
  
4.  <span data-ttu-id="1e4c3-169">C:\Inbox ディレクトリを削除します。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-169">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e4c3-170">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-170">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1e4c3-171">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1e4c3-172">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1e4c3-173">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1e4c3-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`