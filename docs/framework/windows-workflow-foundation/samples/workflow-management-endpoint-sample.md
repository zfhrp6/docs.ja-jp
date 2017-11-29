---
title: "ワークフロー管理エンドポイントのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d13d1d2af449631f93dd4df29ff41113ffbbfec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="617fa-102">ワークフロー管理エンドポイントのサンプル</span><span class="sxs-lookup"><span data-stu-id="617fa-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="617fa-103">このサンプルでは、ワークフロー コントロール エンドポイントを使用して、ローカルとリモートの両方でワークフローを作成および実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="617fa-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="617fa-104">このサンプルでは、コントロール エンドポイントをホストし、そのコントロール エンドポイントを呼び出すクライアントを記述して、ワークフローのインスタンスを作成および実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="617fa-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="617fa-105">このワークフローはサービスではありません。</span><span class="sxs-lookup"><span data-stu-id="617fa-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="617fa-106">サンプルのサービス側では、ワークフローが WorkflowServiceHost を使用してホストされており、クライアントが管理操作 (保留、開始など) を実行できるように WorkflowControlEndpoint が追加されています。</span><span class="sxs-lookup"><span data-stu-id="617fa-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="617fa-107">ワークフローを作成できるように、ユーザー定義 CreationEndpoint も追加されています。</span><span class="sxs-lookup"><span data-stu-id="617fa-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="617fa-108">次に、サービスは、中断状態のワークフローを開始するこれらのエンドポイントを使用して、ワークフローを再開します。</span><span class="sxs-lookup"><span data-stu-id="617fa-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="617fa-109">クライアントはクライアント コードから同じ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="617fa-109">The client performs the same operations but from the client code.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="617fa-110">これらのインターフェイスを参照してください、[ワークフロー コントロール エンドポイント](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)と[する方法: IIS でサービス以外のワークフローのホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="617fa-110"> these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) and [How to: Host a non-service workflow in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="617fa-111">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="617fa-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="617fa-112">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を管理者権限で実行します。</span><span class="sxs-lookup"><span data-stu-id="617fa-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="617fa-113">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ManagementEndpoint.sln ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="617fa-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="617fa-114">ソリューションをビルドするには、ctrl キーと shift キーを押しながら B キーを押してまたは選択**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="617fa-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="617fa-115">ManagementEndpoint.exe アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="617fa-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="617fa-116">Client.exe アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="617fa-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="617fa-117">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="617fa-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="617fa-118">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="617fa-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="617fa-119">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="617fa-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="617fa-120">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="617fa-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`  
  
## <a name="see-also"></a><span data-ttu-id="617fa-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="617fa-121">See Also</span></span>
