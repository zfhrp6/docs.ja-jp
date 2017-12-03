---
title: "WorkflowHostingEndpoint のブックマーク リゾルバー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 99efa92de6e13243ac5ea4b6379ce99e8507ed94
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="3bac6-102">WorkflowHostingEndpoint のブックマーク リゾルバー</span><span class="sxs-lookup"><span data-stu-id="3bac6-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="3bac6-103">このサンプルでは、<xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> を <xref:System.ServiceModel.Activities.WorkflowServiceHost> と共に使用して、ワークフロー インスタンスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3bac6-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3bac6-104">使用例</span><span class="sxs-lookup"><span data-stu-id="3bac6-104">Demonstrates</span></span>  
 <span data-ttu-id="3bac6-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="3bac6-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="3bac6-106">説明</span><span class="sxs-lookup"><span data-stu-id="3bac6-106">Discussion</span></span>  
 <span data-ttu-id="3bac6-107">このサンプルでは、<xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> を使用して、<xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされるワークフロー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3bac6-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="3bac6-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> は、次のシナリオで使用できる <xref:System.ServiceModel.Activities.WorkflowServiceHost> の機能拡張ポイントです。</span><span class="sxs-lookup"><span data-stu-id="3bac6-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="3bac6-109">新しいワークフロー インスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="3bac6-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="3bac6-110"><xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされているワークフロー インスタンスでのブックマークの再開</span><span class="sxs-lookup"><span data-stu-id="3bac6-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="3bac6-111">含まれているサンプルのエンドポイントでは、ワークフローを作成してインスタンス ID を返したり、特定の ID を持つインスタンスを作成したりするための操作を提供するコントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="3bac6-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="3bac6-112">サンプルのコンソール アプリケーションでは、ワークフロー定義を含む <xref:System.ServiceModel.Activities.WorkflowServiceHost> インスタンスが作成されて、`CreationEndpoint` がホストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3bac6-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="3bac6-113">その後、エンドポイントで `Create` 操作が呼び出され、新しいワークフロー インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3bac6-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3bac6-114">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="3bac6-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3bac6-115">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="3bac6-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="3bac6-116">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3bac6-116">Run the application.</span></span> <span data-ttu-id="3bac6-117">`CreationEndpoint` コンソールには、ワークフロー インスタンスの作成時にインスタンス ID を含むメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3bac6-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="3bac6-118">"Hello World!"メッセージ</span><span class="sxs-lookup"><span data-stu-id="3bac6-118">The message "Hello World!"</span></span> <span data-ttu-id="3bac6-119">ワークフロー インスタンスによって印刷されます。</span><span class="sxs-lookup"><span data-stu-id="3bac6-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3bac6-120">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3bac6-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3bac6-121">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3bac6-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3bac6-122">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="3bac6-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3bac6-123">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3bac6-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
