---
title: TransactedReceiveScope の使用
ms.date: 03/30/2017
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
ms.openlocfilehash: 635235504a08a151053026cf25c68750dc335eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="use-of-transactedreceivescope"></a><span data-ttu-id="c480e-102">TransactedReceiveScope の使用</span><span class="sxs-lookup"><span data-stu-id="c480e-102">Use of TransactedReceiveScope</span></span>
<span data-ttu-id="c480e-103">このサンプルでは、クライアントからサーバーにトランザクションをフローする方法を示します。このために、<xref:System.Activities.Statements.TransactionScope> を使用してクライアント上に新しいトランザクションを作成し、<xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用してフローされたトランザクションを含むメッセージを受信し、サーバー上でトランザクションの有効期間のスコープを設定します。</span><span class="sxs-lookup"><span data-stu-id="c480e-103">This sample shows how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span> <span data-ttu-id="c480e-104">このサンプルは、クライアントとサーバーの役割を果たす 2 つのプロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c480e-104">The sample consists of two projects that fill the roles of client and server.</span></span>  
  
## <a name="client-application"></a><span data-ttu-id="c480e-105">クライアント アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c480e-105">Client Application</span></span>  
 <span data-ttu-id="c480e-106">クライアント アプリケーションは、分散トランザクション ID の出力、サーバーへのメッセージの送信、トランザクションのフロー、応答の受信、分散トランザクション ID の再出力、および完了処理を行うワークフローを実行します。</span><span class="sxs-lookup"><span data-stu-id="c480e-106">The client application runs a workflow that prints the distributed transaction ID, sends a message to the server, flows the transaction, receives the reply, prints the distributed transaction ID again and completes.</span></span> <span data-ttu-id="c480e-107">最初に出力される分散トランザクション ID は空の GUID です。これは、その時点ではトランザクションがまだローカルのみであるためです。</span><span class="sxs-lookup"><span data-stu-id="c480e-107">When the distributed transaction ID is initially prints, it is an empty GUID as the transaction is still only local.</span></span>  
  
## <a name="server-application"></a><span data-ttu-id="c480e-108">サーバー アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c480e-108">Server Application</span></span>  
 <span data-ttu-id="c480e-109">サーバー プロジェクトはクライアントに似ていますが、ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされます。これは、エンドポイントでクライアントからのメッセージをリッスンする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="c480e-109">The server project is similar, however, the workflow is hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> because it must listen on an endpoint for the message from the client.</span></span> <span data-ttu-id="c480e-110">ワークフローの中心は、クライアントからフローされたトランザクションの受信、送信されたメッセージの出力、分散トランザクション ID の出力、およびクライアントへの応答の送信を行う <xref:System.ServiceModel.Activities.TransactedReceiveScope> です。</span><span class="sxs-lookup"><span data-stu-id="c480e-110">The workflow is centered on the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, which receives the flowed transaction from the client, prints the message that was sent, prints the distributed transaction ID and sends the reply to the client.</span></span> <span data-ttu-id="c480e-111">分散トランザクション ID は空でない GUID になり、トランザクションに対応するアクティビティが <xref:System.ServiceModel.Activities.TransactedReceiveScope> の本体に追加された場合、そのアクティビティはフローされたランザクションで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c480e-111">The distributed transaction ID is now a non-empty GUID and if a transaction-aware activity was added to the body of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, it would execute under the flowed transaction.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="c480e-112">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="c480e-112">To run the sample</span></span>  
  
1.  <span data-ttu-id="c480e-113">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で TransactedReceiveScope.sln ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="c480e-113">Open the TransactedReceiveScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c480e-114">ソリューションをビルドするには、ctrl キーと shift キーを押しながら B キーを押してまたは選択**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="c480e-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="c480e-115">ビルドが成功した後、ソリューションを右クリックし  **スタートアップ プロジェクトの**します。</span><span class="sxs-lookup"><span data-stu-id="c480e-115">Once the build has succeeded, right-click the solution and select **Set Startup Projects**.</span></span> <span data-ttu-id="c480e-116">ダイアログ ボックスで、次のように選択します。**マルチ スタートアップ プロジェクト**両方のプロジェクトのアクションを確認してください**開始**です。</span><span class="sxs-lookup"><span data-stu-id="c480e-116">From the dialog, select **Multiple Startup Projects** and ensure the action for both projects is **Start**.</span></span>  
  
4.  <span data-ttu-id="c480e-117">F5 キーを押すか、選択**デバッグの開始**から、**デバッグ**メニュー。</span><span class="sxs-lookup"><span data-stu-id="c480e-117">Press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="c480e-118">または、ctrl キーを押しながら f5 キーを押してまたは選択**デバッグなしで開始**から、**デバッグ**] メニューの [デバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="c480e-118">Alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c480e-119">クライアントを起動する前に、サーバーを起動しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c480e-119">The server must be running prior to starting the client.</span></span> <span data-ttu-id="c480e-120">サービスをホストするコンソール ウィンドウの出力で、起動された時間が示されます。</span><span class="sxs-lookup"><span data-stu-id="c480e-120">The output from the console window hosting the service indicates when it has started.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c480e-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c480e-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c480e-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c480e-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c480e-123">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="c480e-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c480e-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c480e-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`