---
title: "トランザクション バッチ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dbd11f3dad60463a5650d7aa6e53f9e8f3f5021e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-batching"></a><span data-ttu-id="71527-102">トランザクション バッチ</span><span class="sxs-lookup"><span data-stu-id="71527-102">Transacted Batching</span></span>
<span data-ttu-id="71527-103">このサンプルでは、メッセージ キュー (MSMQ) を使用して、トランザクション読み取りをバッチ処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="71527-103">This sample demonstrates how to batch transacted reads by using Message Queuing (MSMQ).</span></span> <span data-ttu-id="71527-104">トランザクション バッチは、キューを使用する通信でトランザクション読み取りのパフォーマンスを最適化するための機能です。</span><span class="sxs-lookup"><span data-stu-id="71527-104">Transacted Batching is a performance optimization feature for transacted reads in queued communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71527-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71527-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="71527-106">キュー通信では、クライアントはサービスとの通信にキューを使用します。</span><span class="sxs-lookup"><span data-stu-id="71527-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="71527-107">厳密には、クライアントはメッセージをキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="71527-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="71527-108">サービスは、メッセージをキューから受信します。</span><span class="sxs-lookup"><span data-stu-id="71527-108">The service receives messages from the queue.</span></span> <span data-ttu-id="71527-109">したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="71527-109">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="71527-110">このサンプルでは、トランザクション バッチを示します。</span><span class="sxs-lookup"><span data-stu-id="71527-110">This sample demonstrates transacted batching.</span></span> <span data-ttu-id="71527-111">トランザクション バッチの動作では、キューに置かれた多数のメッセージを読み取ってそれを処理するために使用するトランザクションが 1 つで済みます。</span><span class="sxs-lookup"><span data-stu-id="71527-111">Transacted batching is a behavior that enables the use of a single transaction when reading many messages in the queue and processing them.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="71527-112">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="71527-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="71527-113">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="71527-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="71527-114">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="71527-114">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="71527-115">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="71527-115">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="71527-116">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="71527-116">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="71527-117">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="71527-117">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="71527-118">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="71527-118">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="71527-119">展開して、**機能**タブです。</span><span class="sxs-lookup"><span data-stu-id="71527-119">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="71527-120">右クリック**プライベート メッセージ キュー**を選択して**新規**、**プライベート キュー**です。</span><span class="sxs-lookup"><span data-stu-id="71527-120">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="71527-121">チェック、**トランザクション**ボックス。</span><span class="sxs-lookup"><span data-stu-id="71527-121">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="71527-122">入力`ServiceModelSamplesTransacted`として、新しいキューの名前。</span><span class="sxs-lookup"><span data-stu-id="71527-122">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71527-123">このサンプルでは、クライアントは多数のメッセージをバッチの一部として送信します。</span><span class="sxs-lookup"><span data-stu-id="71527-123">In this sample the client sends hundreds of messages as part of the batch.</span></span> <span data-ttu-id="71527-124">通常、サービス アプリケーションがこれらを処理するのに多少の時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="71527-124">It is normal for the service application to take some time to process these.</span></span>  
  
3.  <span data-ttu-id="71527-125">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="71527-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="71527-126">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="71527-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="71527-127">ワークグループに属しているコンピューターまたは Active Directory 統合のないコンピューターでこのサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="71527-127">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="71527-128"><xref:System.ServiceModel.NetMsmqBinding> を使用する場合の既定では、トランスポート セキュリティが有効です。</span><span class="sxs-lookup"><span data-stu-id="71527-128">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="71527-129">MSMQ トランスポート セキュリティでは、2 つの関連するプロパティがある<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>と<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`既定では、認証モードに設定`Windows`保護レベルに設定されていると`Sign`です。</span><span class="sxs-lookup"><span data-stu-id="71527-129">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="71527-130">MSMQ の認証機能と署名機能を利用するには、ドメインに MSMQ があることと、MSMQ に関する Active Directory の統合オプションがインストールされていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="71527-130">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="71527-131">この条件を満たしていないコンピューターでこのサンプルを実行すると、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="71527-131">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
2.  <span data-ttu-id="71527-132">ドメインに属していないコンピュータ、または Active Directory 統合がインストールされていないコンピュータを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードと保護レベルを `None` にします。この構成の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="71527-132">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
    </system.serviceModel>  
    ```  
  
3.  <span data-ttu-id="71527-133">サーバーとクライアントの両方の構成を変更したことを確認してから、サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="71527-133">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71527-134">`security``mode` を `None` に設定することは、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>、および `Message` のセキュリティを `None` に設定することに相当します。</span><span class="sxs-lookup"><span data-stu-id="71527-134">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
4.  <span data-ttu-id="71527-135">データベースをリモート コンピューターで実行するには、接続文字列をデータベースが存在するコンピューターを指すように変更します。</span><span class="sxs-lookup"><span data-stu-id="71527-135">To run the database on a remote computer, change the connection string to point to the computer on which the database resides.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71527-136">要件</span><span class="sxs-lookup"><span data-stu-id="71527-136">Requirements</span></span>  
 <span data-ttu-id="71527-137">このサンプルを実行するには、MSMQ をインストールする必要があります。さらに、SQL または SQL Express が必要です。</span><span class="sxs-lookup"><span data-stu-id="71527-137">To run this sample, MSMQ must be installed and SQL or SQL Express is required.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="71527-138">使用例</span><span class="sxs-lookup"><span data-stu-id="71527-138">Demonstrates</span></span>  
 <span data-ttu-id="71527-139">このサンプルはトランザクション バッチ動作を示します。</span><span class="sxs-lookup"><span data-stu-id="71527-139">The sample demonstrates transacted batching behavior.</span></span> <span data-ttu-id="71527-140">トランザクション バッチは、MSMQ キューを使用したトランスポートで提供されるパフォーマンス最適化機能です。</span><span class="sxs-lookup"><span data-stu-id="71527-140">Transacted batching is a performance optimization feature provided with MSMQ queued transport.</span></span>  
  
 <span data-ttu-id="71527-141">メッセージの送受信にトランザクションが使用されている場合、実際には 2 つの別個のトランザクションが存在しています。</span><span class="sxs-lookup"><span data-stu-id="71527-141">When transactions are used to send and receive messages there are actually 2 separate transactions.</span></span> <span data-ttu-id="71527-142">クライアントがトランザクションのスコープ内でメッセージを送信する場合、トランザクションはクライアントおよびクライアント キュー マネージャにとってローカルとなります。</span><span class="sxs-lookup"><span data-stu-id="71527-142">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="71527-143">サービスがトランザクションのスコープ内でメッセージを受信する場合、トランザクションはサービスおよび受信キュー マネージャにとってローカルとなります。</span><span class="sxs-lookup"><span data-stu-id="71527-143">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="71527-144">クライアントとサービスは同じトランザクションに参加していません。むしろ、キューに対して操作 (送信や受信など) を実行する場合は異なるトランザクションを使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="71527-144">It is very important to remember that the client and the service are not participating in the same transaction; rather they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="71527-145">このサンプルでは、複数のサービス操作を実行する際に単一のトランザクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="71527-145">In the sample we use a single transaction for the execution of multiple service operations.</span></span> <span data-ttu-id="71527-146">これはパフォーマンス最適化機能としてのみ使用されるもので、アプリケーションのセマンティクスには影響しません。</span><span class="sxs-lookup"><span data-stu-id="71527-146">This is used only as a performance optimization feature and does not impact the semantics of the application.</span></span> <span data-ttu-id="71527-147">サンプルがに基づいて[トランザクション MSMQ バインディング](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)です。</span><span class="sxs-lookup"><span data-stu-id="71527-147">The sample is based on [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="71527-148">コメント</span><span class="sxs-lookup"><span data-stu-id="71527-148">Comments</span></span>  
 <span data-ttu-id="71527-149">このサンプルでは、クライアントはトランザクションのスコープ内からメッセージのバッチをサービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="71527-149">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="71527-150">パフォーマンスの最適化を示すために、この例では最大 2,500 という多数のメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="71527-150">To show the performance optimization, we send a large number of messages; in this case, up to 2500 messages.</span></span>  
  
 <span data-ttu-id="71527-151">キューに送信されたメッセージは、サービスによって定義されたトランザクション スコープ内のサービスによって受信されます。</span><span class="sxs-lookup"><span data-stu-id="71527-151">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span> <span data-ttu-id="71527-152">バッチ処理が行われない場合、2,500 のトランザクションが実行され、そのたびにサービス操作が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="71527-152">Without batching, this results in 2500 transactions for each invocation of the service operation.</span></span> <span data-ttu-id="71527-153">これはシステムのパフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="71527-153">This impacts performance of the system.</span></span> <span data-ttu-id="71527-154">MSMQ キューと `Orders` データベースという 2 つのリソース マネージャが含まれているので、このようなトランザクションはそれぞれ DTC トランザクションです。</span><span class="sxs-lookup"><span data-stu-id="71527-154">Because two resource managers are involved -the MSMQ queue and the `Orders` database- each such transaction is a DTC transaction.</span></span> <span data-ttu-id="71527-155">これを最適化するには、単一のトランザクション内でメッセージとサービス操作の呼び出しのバッチを発生させることによって、使用するトランザクション数を大幅に減らします。</span><span class="sxs-lookup"><span data-stu-id="71527-155">We optimize this by using a much smaller number of transactions by ensuring that a batch of messages and service operation invocations happen in a single transaction.</span></span>  
  
 <span data-ttu-id="71527-156">次の手順により、バッチ機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="71527-156">We use the batching feature by:</span></span>  
  
-   <span data-ttu-id="71527-157">トランザクション バッチ動作を構成で指定します。</span><span class="sxs-lookup"><span data-stu-id="71527-157">Specifying transacted batching behavior in configuration.</span></span>  
  
-   <span data-ttu-id="71527-158">単一のトランザクションを使用していくつのメッセージを読み取るかという観点から、バッチ サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="71527-158">Specifying a batch size in terms of number of messages to be read using a single transaction.</span></span>  
  
-   <span data-ttu-id="71527-159">同時に実行するバッチの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="71527-159">Specifying the maximum number of concurrent batches to run.</span></span>  
  
 <span data-ttu-id="71527-160">この例では、100 のサービス操作を単一のトランザクションで呼び出してからトランザクションをコミットするという方法でトランザクションの数を減らすことにより、パフォーマンスの向上を示します。</span><span class="sxs-lookup"><span data-stu-id="71527-160">In this example, we show performance gains by reducing the number of transactions by ensuring that 100 service operations are invoked in a single transaction before committing the transaction.</span></span>  
  
 <span data-ttu-id="71527-161">サービス動作は、`TransactionScopeRequired` が `true` に設定された操作動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="71527-161">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="71527-162">これにより、キューからのメッセージの取得に使用されるものと同じトランザクション スコープが、このメソッドによってアクセスされる任意のリソース マネージャにより使用されます。</span><span class="sxs-lookup"><span data-stu-id="71527-162">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="71527-163">この例では、基本的なデータベースを使用してメッセージに含まれる発注書情報を保存します。</span><span class="sxs-lookup"><span data-stu-id="71527-163">In this example, we use a basic database to store the purchase order information contained in the message.</span></span> <span data-ttu-id="71527-164">さらにトランザクション スコープでは、メソッドから例外がスローされた場合にメッセージがキューに返されることも保証されます。</span><span class="sxs-lookup"><span data-stu-id="71527-164">The transaction scope also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="71527-165">このサービス動作を設定しない場合、キューに置かれたチャネルはトランザクションを作成して、キューからのメッセージを読み取り、操作が失敗した場合には、ディスパッチによってメッセージが失われる前に、自動的にそのメッセージをコミットします。</span><span class="sxs-lookup"><span data-stu-id="71527-165">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before it is dispatched so that if the operation fails, the message is lost.</span></span> <span data-ttu-id="71527-166">最もよく見られるシナリオは、キューからのメッセージの読み込みに使用するトランザクションにサービス操作を登録することです。次のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="71527-166">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue as demonstrated in the following code.</span></span>  
  
 <span data-ttu-id="71527-167">`ReleaseServiceInstanceOnTransactionComplete` が `false` に設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="71527-167">Note that `ReleaseServiceInstanceOnTransactionComplete` is set to `false`.</span></span> <span data-ttu-id="71527-168">これはバッチ処理の重要な要件です。</span><span class="sxs-lookup"><span data-stu-id="71527-168">This is an important requirement for batching.</span></span> <span data-ttu-id="71527-169">`ReleaseServiceInstanceOnTransactionComplete` のプロパティ `ServiceBehaviorAttribute` は、トランザクションが完了した後のサービス インスタンスの処理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="71527-169">The property `ReleaseServiceInstanceOnTransactionComplete` on `ServiceBehaviorAttribute` indicates what to do with the service instance once the transaction is completed.</span></span> <span data-ttu-id="71527-170">既定では、トランザクションが完了するとサービス インスタンスは解放されます。</span><span class="sxs-lookup"><span data-stu-id="71527-170">By default, the service instance is released upon completing the transaction.</span></span> <span data-ttu-id="71527-171">バッチ処理の主な特徴は、キューに置かれた多数のメッセージを読み取ってディスパッチするために単一のトランザクションを使用する点です。</span><span class="sxs-lookup"><span data-stu-id="71527-171">The core aspect to batching is the use of a single transaction for reading and dispatching many messages in the queue.</span></span> <span data-ttu-id="71527-172">そのため、サービス インスタンスが解放されると、実際にバッチ処理が行われる前にトランザクションが完了することになります。</span><span class="sxs-lookup"><span data-stu-id="71527-172">Therefore releasing the service instance ends up completing the transaction prematurely negating the very use of batching.</span></span> <span data-ttu-id="71527-173">このプロパティが `true` に設定され、トランザクション バッチ動作がエンドポイントに追加された場合、このバッチ処理の検証動作は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="71527-173">If this property is set to `true` and transacted batching behavior is added to the endpoint, the batching validation behavior throws an exception.</span></span>  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```  
  
 <span data-ttu-id="71527-174">`Orders` クラスは、注文処理機能をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="71527-174">The `Orders` class encapsulates the processing of the order.</span></span> <span data-ttu-id="71527-175">サンプルでは、このクラスは発注書情報を使用してデータベースを更新します。</span><span class="sxs-lookup"><span data-stu-id="71527-175">In the sample, it updates the database with purchase order information.</span></span>  
  
```  
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```  
  
 <span data-ttu-id="71527-176">バッチ動作とその構成は、サービス アプリケーションの構成で指定されます。</span><span class="sxs-lookup"><span data-stu-id="71527-176">The batching behavior and its configuration are specified in the service application configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="71527-177">バッチ サイズにより、システムの動作が決まります。</span><span class="sxs-lookup"><span data-stu-id="71527-177">The batch size is a hint to the system.</span></span> <span data-ttu-id="71527-178">たとえば、バッチ サイズを 20 に指定した場合、20 のメッセージが単一トランザクションを使用して読み取られてディスパッチされ、その後トランザクションがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="71527-178">For example, if you specify a batch size of 20, then 20 messages would be read and dispatched using a single transaction and then the transaction is committed.</span></span> <span data-ttu-id="71527-179">しかし、そのバッチ サイズに達する前にトランザクションがバッチをコミットする場合もあります。</span><span class="sxs-lookup"><span data-stu-id="71527-179">But there are cases where the transaction may commit the batch before the batch size is reached.</span></span>  
>   
>  <span data-ttu-id="71527-180">各トランザクションにはタイムアウトが関連付けられています。これはトランザクションが作成された後に時間刻みを開始します。</span><span class="sxs-lookup"><span data-stu-id="71527-180">Associated with every transaction is a timeout that starts ticking once the transaction is created.</span></span> <span data-ttu-id="71527-181">このタイムアウト時間が経過すると、トランザクションは中止されます。</span><span class="sxs-lookup"><span data-stu-id="71527-181">When this timeout expires the transaction is aborted.</span></span> <span data-ttu-id="71527-182">バッチ サイズに達していなくてもタイムアウト時間が経過する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="71527-182">It is possible for this timeout to expire even before the batch size is reached.</span></span> <span data-ttu-id="71527-183">中止された後でバッチを再動作させないようにするため、`TransactedBatchingBehavior` はトランザクションの残り時間を確認します。</span><span class="sxs-lookup"><span data-stu-id="71527-183">To avoid re-working the batch because of the abort, the `TransactedBatchingBehavior` checks to see how much time is left on the transaction.</span></span> <span data-ttu-id="71527-184">トランザクションのタイムアウトが 80% 経過すると、トランザクションはコミットされます。</span><span class="sxs-lookup"><span data-stu-id="71527-184">If 80% of the transaction timeout is used up, then the transaction is committed.</span></span>  
>   
>  <span data-ttu-id="71527-185">キューのメッセージがなくなると、<xref:System.ServiceModel.Description.TransactedBatchingBehavior> はバッチ サイズに達するまで待機する代わりに、トランザクションをコミットします。</span><span class="sxs-lookup"><span data-stu-id="71527-185">If there are no more messages in the queue then instead of waiting for the fulfillment of the batch size the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> commits the transaction.</span></span>  
>   
>  <span data-ttu-id="71527-186">バッチ サイズの選択は、アプリケーションに依存します。</span><span class="sxs-lookup"><span data-stu-id="71527-186">The choice of the batch size is dependent on your application.</span></span> <span data-ttu-id="71527-187">バッチ サイズが小さすぎると、必要なパフォーマンスを実現できません。</span><span class="sxs-lookup"><span data-stu-id="71527-187">If the batch size is too small, you may not get the desired performance.</span></span> <span data-ttu-id="71527-188">逆にバッチ サイズが大きすぎると、パフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="71527-188">On the other hand if the batch size is too big, it may deteriorate performance.</span></span> <span data-ttu-id="71527-189">たとえば、トランザクションが長期間有効でデータベースのロックを保持したり、またはトランザクションがデッドロック状態になる場合があります。この場合、バッチはロール バックされて作業がやり直しになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="71527-189">For example, your transaction could live longer and hold locks on your database or your transaction could become dead locked, which could cause the batch to get rolled back and to redo the work.</span></span>  
  
 <span data-ttu-id="71527-190">クライアントはトランザクション スコープを作成します。</span><span class="sxs-lookup"><span data-stu-id="71527-190">The client creates a transaction scope.</span></span> <span data-ttu-id="71527-191">キューとの通信はトランザクションのスコープ内で実行されるため、すべてのメッセージがキューに送信されるか、またはメッセージがキューにまったく送信されないかを示す、アトミック単位として扱われます。</span><span class="sxs-lookup"><span data-stu-id="71527-191">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="71527-192">トランザクションは、トランザクション スコープで <xref:System.Transactions.TransactionScope.Complete%2A> を呼び出すことでコミットされます。</span><span class="sxs-lookup"><span data-stu-id="71527-192">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  
  
```  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="71527-193">サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="71527-193">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="71527-194">サービスがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="71527-194">You can see the service receive messages from the client.</span></span> <span data-ttu-id="71527-195">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="71527-195">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="71527-196">キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="71527-196">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="71527-197">クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="71527-197">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="71527-198">メッセージがバッチ内で読み取られて処理された際には、ロール出力を表示できます。</span><span class="sxs-lookup"><span data-stu-id="71527-198">You can see a rolling output as messages are read in a batch and processed.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="71527-199">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="71527-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="71527-200">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="71527-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="71527-201">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="71527-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="71527-202">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="71527-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a><span data-ttu-id="71527-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="71527-203">See Also</span></span>
