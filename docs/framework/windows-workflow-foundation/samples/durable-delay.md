---
title: 永続的な遅延
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 5307b8144e17f91cd3ba8c2e385492f86c167820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516023"
---
# <a name="durable-delay"></a><span data-ttu-id="5bf35-102">永続的な遅延</span><span class="sxs-lookup"><span data-stu-id="5bf35-102">Durable Delay</span></span>
<span data-ttu-id="5bf35-103">このサンプルでは、永続的な遅延を使用する方法を示します。これは、遅延の間、ワークフローを永続的なデバイスに永続化する遅延のことです。</span><span class="sxs-lookup"><span data-stu-id="5bf35-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="5bf35-104">このサンプル ワークフローには、遅延によって分割された 2 つのコンソールへのメッセージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5bf35-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="5bf35-105">遅延が発生すると、ワークフローがアンロードされ、ワークフローはメモリに再読み込みされるまでワークフロー インスタンス ストアで 5 秒間待機します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="5bf35-106">ワークフローの詳細</span><span class="sxs-lookup"><span data-stu-id="5bf35-106">Workflow Details</span></span>  
 <span data-ttu-id="5bf35-107">ワークフロー サービス ホストは、ワークフローをホストし、読み込みとアンロードを行うことによってワークフロー インスタンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="5bf35-108">ワークフロー定義のインスタンスを開始するために、このサンプルでは、ワークフローの <xref:System.ServiceModel.Activities.Receive> アクティビティにメッセージを送信するプロキシを設定します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="5bf35-109"><xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> プロパティを `true` に設定し、このプロパティがメッセージを受信したらワークフローの新しいインスタンスを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5bf35-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="5bf35-110">初期化時のワークフロー サービス ホストによる設定の詳細を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="5bf35-111">アドレスを持つサービス ホストを作成 (http://localhost:8080/Client)です。</span><span class="sxs-lookup"><span data-stu-id="5bf35-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="5bf35-112">ワークフロー内で <xref:System.ServiceModel.Activities.Receive> アクティビティとの通信を可能にする、サービス ホストのエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="5bf35-113">SQL インスタンス ストアを設定します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="5bf35-114">ワークフロー サービス ホストがワークフロー インスタンスを SQL 永続化ストアにアンロードする条件を指定する、インスタンスのアンロード動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="5bf35-115">このサンプルでは、(遅延が発生して) ワークフローがアイドル状態になった直後にインスタンスがアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="5bf35-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="5bf35-116">ワークフローの <xref:System.ServiceModel.Activities.Receive> アクティビティにメッセージを送信するプロキシを作成します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5bf35-117">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="5bf35-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="5bf35-118">永続性データベースを設定します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="5bf35-119">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5bf35-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="5bf35-120">移動し、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ディレクトリ (C:\Windows\Microsoft.NET\Framework\v4 です。X\\)。</span><span class="sxs-lookup"><span data-stu-id="5bf35-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="5bf35-121">WorkflowManagementService.exe.config ファイルを編集し、<`database`> 要素内に次の接続文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="5bf35-122">DurableDelay\CS ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="5bf35-123">Setup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="5bf35-124">実行[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックして、管理者特権を使用して、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]アイコンを選択して**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="5bf35-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="5bf35-125">Delay.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="5bf35-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="5bf35-126">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="5bf35-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="5bf35-127">Ctrl キーを押しながら F5 キーを押してソリューションを実行します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="5bf35-128">このサンプルをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="5bf35-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="5bf35-129">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5bf35-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="5bf35-130">DurableDelay\CS ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="5bf35-131">Cleanup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="5bf35-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5bf35-132">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5bf35-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5bf35-133">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5bf35-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5bf35-134">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="5bf35-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5bf35-135">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5bf35-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`