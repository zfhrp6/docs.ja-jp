---
title: "OperationContext へのアクセス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ca0290f658dfc5e34ec7e1e1be228213c521ce0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="117b0-102">OperationContext へのアクセス</span><span class="sxs-lookup"><span data-stu-id="117b0-102">Accessing OperationContext</span></span>
<span data-ttu-id="117b0-103">このサンプルで示す方法、メッセージング アクティビティ (<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.Send>) にアクセスする、カスタムのスコープ アクティビティと共に使用できます<xref:System.ServiceModel.OperationContext.Current%2A>アタッチしたり、送信または受信メッセージ内のカスタム メッセージ ヘッダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="117b0-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="117b0-104">使用例</span><span class="sxs-lookup"><span data-stu-id="117b0-104">Demonstrates</span></span>  
 <span data-ttu-id="117b0-105">メッセージング アクティビティ、<xref:System.ServiceModel.Activities.ISendMessageCallback>、<xref:System.ServiceModel.Activities.IReceiveMessageCallback>。</span><span class="sxs-lookup"><span data-stu-id="117b0-105">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="117b0-106">説明</span><span class="sxs-lookup"><span data-stu-id="117b0-106">Discussion</span></span>  
 <span data-ttu-id="117b0-107">このサンプルでは、メッセージング アクティビティで拡張ポイント (<xref:System.ServiceModel.Activities.ISendMessageCallback> および <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) を使用して <xref:System.ServiceModel.OperationContext.Current%2A> にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="117b0-107">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="117b0-108">これらのコールバックは、実行時にメッセージング アクティビティによって取得される <xref:System.Activities.IExecutionProperty> の実装としてワークフロー ランタイム内に登録されます。</span><span class="sxs-lookup"><span data-stu-id="117b0-108">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="117b0-109">その <xref:System.Activities.IExecutionProperty> 実装と同じスコープ内のメッセージング アクティビティはすべて影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="117b0-109">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="117b0-110">具体的には、このサンプルでは、カスタムのスコープ アクティビティを使用してコールバック動作を適用します。</span><span class="sxs-lookup"><span data-stu-id="117b0-110">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="117b0-111"><xref:System.ServiceModel.Activities.ISendMessageCallback> は、ワークフローの <xref:System.Activities.WorkflowApplication.Id%2A> を送信 <xref:System.ServiceModel.Channels.MessageHeader> として含めるためにクライアント ワークフローで使用されます。</span><span class="sxs-lookup"><span data-stu-id="117b0-111">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="117b0-112">このヘッダーはサービスで <xref:System.ServiceModel.Activities.IReceiveMessageCallback> を使用して取得され、ヘッダーの値がコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="117b0-112">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="117b0-113">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="117b0-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="117b0-114">このサンプルでは、HTTP エンドポイントを使用してワークフロー サービスを公開します。</span><span class="sxs-lookup"><span data-stu-id="117b0-114">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="117b0-115">このサンプルを適切な URL Acl を実行するを追加する必要があります (を参照してください[を構成する HTTP および HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)詳細については)、管理者として Visual Studio を実行しているか、適切な Acl を追加する管理者特権のプロンプトで次のコマンドを実行することによってです。</span><span class="sxs-lookup"><span data-stu-id="117b0-115">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="117b0-116">ドメインとユーザー名は置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="117b0-116">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="117b0-117">URL ACL を追加したら、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="117b0-117">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="117b0-118">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="117b0-118">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="117b0-119">複数のスタートアップ プロジェクトを設定するには、ソリューションを右クリックしを選択すると**スタートアップ プロジェクトの**します。</span><span class="sxs-lookup"><span data-stu-id="117b0-119">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3.  <span data-ttu-id="117b0-120">追加**サービス**と**クライアント**(その順序で) 複数のスタートアップ プロジェクトとして。</span><span class="sxs-lookup"><span data-stu-id="117b0-120">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4.  <span data-ttu-id="117b0-121">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="117b0-121">Run the application.</span></span> <span data-ttu-id="117b0-122">クライアント コンソールに実行中のワークフローが 2 回示され、[サービス] ウィンドウにこれらのワークフローのインスタンス ID が示されます。</span><span class="sxs-lookup"><span data-stu-id="117b0-122">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="117b0-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="117b0-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="117b0-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="117b0-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="117b0-125">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="117b0-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="117b0-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="117b0-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
