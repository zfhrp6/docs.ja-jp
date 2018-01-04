---
title: "階層的な構成モデル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf8e7b37b6430be1eed9bc037bfa06aeb825b866
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="a341d-102">階層的な構成モデル</span><span class="sxs-lookup"><span data-stu-id="a341d-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="a341d-103">このサンプルでは、サービスの構成ファイルの階層を実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a341d-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="a341d-104">また、バインド、サービス動作、およびエンドポイント動作を階層の上位レベルから継承する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="a341d-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a341d-105">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="a341d-105">Sample details</span></span>  
 <span data-ttu-id="a341d-106">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 用に開発された機能の 1 つとして、階層的な構成モデルの強化があります。</span><span class="sxs-lookup"><span data-stu-id="a341d-106">One of the features developed for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="a341d-107">階層的な構成モデルは、たとえば、Machine.config -> Rootweb.config -> Web.config のように定義されます。[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] では、構成階層の上位レベルで定義されるこれらのバインドおよび動作が、明示的な構成なしにサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a341d-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="a341d-108">このサンプルでは、コンピューター レベルまたはアプリケーション レベルで定義された構成要素に依存することによって簡単なサービス構成を実現する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a341d-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="a341d-109">このサンプルは、階層の 3 つのレベルで定義された 9 個のサービスから構成されます。</span><span class="sxs-lookup"><span data-stu-id="a341d-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="a341d-110">`Service1` はルートになります。</span><span class="sxs-lookup"><span data-stu-id="a341d-110">`Service1` is at the root.</span></span> <span data-ttu-id="a341d-111">`Service2` と `Service3` は `Service1` から既定の要素を継承します。</span><span class="sxs-lookup"><span data-stu-id="a341d-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="a341d-112">`Service4`、`Service5`、`Service6`、および `Service7` は、階層の第 3 レベルで定義され、`Service3` から既定の要素を継承します。</span><span class="sxs-lookup"><span data-stu-id="a341d-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="a341d-113">最後に、`Service10` および `Service11` は階層の第 4 レベルに置かれます。</span><span class="sxs-lookup"><span data-stu-id="a341d-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="a341d-114">すべてのサービスは `IDesc` コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="a341d-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="a341d-115">`IDesc` インターフェイスの定義を次に示します。この定義は、このインターフェイスで公開されるメソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="a341d-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="a341d-116">`IDesc` インターフェイスは Service1.cs で定義されます。</span><span class="sxs-lookup"><span data-stu-id="a341d-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 <span data-ttu-id="a341d-117">サービスによるこれらのメソッドの実装は単純です。</span><span class="sxs-lookup"><span data-stu-id="a341d-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="a341d-118">`ListEndpoints` は、すべてのサービス エンドポイントを反復処理し、サービスにあるすべてのエンドポイントのリストを返します。</span><span class="sxs-lookup"><span data-stu-id="a341d-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="a341d-119">`ListServiceBehaviors` は、サービスに追加されたすべての動作を反復処理し、サービスに関連付けられているすべてのサービス動作のリストを返します。</span><span class="sxs-lookup"><span data-stu-id="a341d-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="a341d-120">`ListEndpointBehaviors` は、`ListServiceBehaviors` と同様に動作しますが、サービス動作ではなくエンドポイント動作のリストを返します。</span><span class="sxs-lookup"><span data-stu-id="a341d-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="a341d-121">この実装により、クライアントは、サービスで公開されているエンドポイントの数、およびサービスに追加されたサービス動作とエンドポイント動作を認識できます。</span><span class="sxs-lookup"><span data-stu-id="a341d-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="a341d-122">サンプルの一部として実装されているクライアントは、ソリューションのすべてのサービスにサービス参照を追加し、サービスごとにこれらの要素を示します。</span><span class="sxs-lookup"><span data-stu-id="a341d-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="a341d-123">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="a341d-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="a341d-124">クライアントを実行するには</span><span class="sxs-lookup"><span data-stu-id="a341d-124">To run the client</span></span>  
  
1.  <span data-ttu-id="a341d-125">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、ConfigHierarchicalModel.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a341d-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="a341d-126">クライアント プロジェクトはまだスタートアップ プロジェクトに設定されていないので、次の手順で設定します。</span><span class="sxs-lookup"><span data-stu-id="a341d-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="a341d-127">**ソリューション エクスプ ローラー**ソリューションを右クリックし、**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="a341d-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="a341d-128">**共通プロパティ****スタートアップ プロジェクト**、順にクリック**シングル スタートアップ プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="a341d-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="a341d-129">**シングル スタートアップ プロジェクト**ドロップダウン リストで、**クライアント**です。</span><span class="sxs-lookup"><span data-stu-id="a341d-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="a341d-130">をクリックして**OK**ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a341d-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="a341d-131">サンプルをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a341d-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="a341d-132">クライアントを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a341d-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a341d-133">この手順が機能しない場合は、次の手順を使用して、環境設定が適切であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a341d-133">If these steps do not work, then make sure that your environment has been properly set up, using the following steps.</span></span>  
>   
>  1.  <span data-ttu-id="a341d-134">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a341d-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="a341d-135">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a341d-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="a341d-136">1 つまたは複数のコンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a341d-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a341d-137">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a341d-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a341d-138">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a341d-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a341d-139">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="a341d-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a341d-140">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a341d-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="a341d-141">参照</span><span class="sxs-lookup"><span data-stu-id="a341d-141">See Also</span></span>  
 [<span data-ttu-id="a341d-142">AppFabric 管理のサンプル</span><span class="sxs-lookup"><span data-stu-id="a341d-142">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)
