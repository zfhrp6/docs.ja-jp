---
title: OperationScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d1e2738e8cdb546a1dcbb00689e5b4c360ddd04
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="operationscope"></a><span data-ttu-id="2bbd2-102">OperationScope</span><span class="sxs-lookup"><span data-stu-id="2bbd2-102">OperationScope</span></span>
<span data-ttu-id="2bbd2-103">このサンプルでは、メッセージング アクティビティの <xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply> を使用して、既存のカスタム アクティビティをワークフロー サービス内の操作として公開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-103">This sample demonstrates how the messaging activities, <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> can be used to expose an existing custom activity as an operation in a workflow service.</span></span> <span data-ttu-id="2bbd2-104">このサンプルには、`OperationScope` という新しいカスタム アクティビティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-104">This sample includes a new custom activity called an `OperationScope`.</span></span> <span data-ttu-id="2bbd2-105">このアクティビティは、ユーザーが操作の本文をカスタム アクティビティとして個別に作成できるようにし、それを `OperationScope` アクティビティを使用してサービス操作として簡単に公開できるようにすることで、ワークフロー サービスの開発を容易にするためのものです。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-105">It is intended to ease the development of a workflow service by allowing users to author the body of their operations separately as custom activities and then easily exposing them as service operations using the `OperationScope` activity.</span></span> <span data-ttu-id="2bbd2-106">たとえば、2 つの `Add` 引数を受け取って 1 つの `in` 引数を返すカスタム `out` アクティビティは、`Add` にドロップすることでワークフロー サービスの `OperationScope` 操作として公開できます。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-106">For example, a custom `Add` activity that takes two `in` arguments and returns one `out` argument could be exposed as an `Add` operation on the workflow service by dropping it into an `OperationScope`.</span></span>  
  
 <span data-ttu-id="2bbd2-107">スコープは、本文として提供されたアクティビティを調べることによって機能します。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-107">The scope works by inspecting the activity provided as its body.</span></span> <span data-ttu-id="2bbd2-108">バインドされていない `in` 引数は、受信メッセージからの入力であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-108">Any unbound `in` arguments are assumed to be inputs from the incoming message.</span></span> <span data-ttu-id="2bbd2-109">`out` 引数はすべて、バインドされているかどうかに関係なく、後続の応答メッセージの出力であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-109">All `out` arguments, regardless of whether they are bound, are assumed to be outputs in the subsequent reply message.</span></span> <span data-ttu-id="2bbd2-110">公開される操作の名前は、`OperationScope` アクティビティの表示名から取得されます。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-110">The exposed operation’s name is taken from the display name of the `OperationScope` activity.</span></span> <span data-ttu-id="2bbd2-111">最後に、本文アクティビティは、アクティビティの引数にバインドされたメッセージからのパラメーターを使用して、<xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply> にラップされます。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-111">The end result is that the body activity is wrapped in a <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> with the parameters from the messages bound to the arguments of the activity.</span></span>  
  
 <span data-ttu-id="2bbd2-112">このサンプルでは、HTTP エンドポイントを使用してワークフロー サービスを公開します。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="2bbd2-113">サンプルを実行するには、適切な URL ACL を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-113">To run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="2bbd2-114">[HTTP および HTTPS の構成](http://go.microsoft.com/fwlink/?LinkId=70353)です。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-114"> [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="2bbd2-115">管理者特権のプロンプトで次のコマンドを実行する適切な Acl を追加します (% ドメインのドメインとユーザー名に置き換えられることを確認してください。\\%username%)。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-115">Executing the following command at an elevated prompt adds the appropriate ACLs (ensure that your Domain and Username are substituted for %DOMAIN%\\%UserName%).</span></span>  
  
 <span data-ttu-id="2bbd2-116">**netsh http 追加 urlacl url = http://+: 8000/ユーザー ドメイン % =\\%username%**</span><span class="sxs-lookup"><span data-stu-id="2bbd2-116">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="2bbd2-117">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="2bbd2-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="2bbd2-118">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で OperationScope.sln ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-118">Open the OperationScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="2bbd2-119">複数のスタートアップ プロジェクトを設定するには、ソリューション エクスプ ローラーでソリューションを右クリックしを選択すると**スタートアップ プロジェクトの**します。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-119">Set multiple start-up projects by right-clicking the solution in Solution Explorer and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="2bbd2-120">複数のスタートアップ プロジェクトとして Scenario および Scenario_Client を (この順序で) 追加します。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-120">Add Scenario and Scenario_Client (in that order) as multiple start-up projects.</span></span>  
  
3.  <span data-ttu-id="2bbd2-121">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-121">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="2bbd2-122">カスタム アクティビティ `OperationScope` が原因で、BankService.xaml ワークフローを表示するためにこの手順が必要になります。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-122">This step is required to view the BankService.xaml workflow due to the custom activity `OperationScope`.</span></span>  
  
4.  <span data-ttu-id="2bbd2-123">Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-123">Press CTRL+F5 to run the application.</span></span> <span data-ttu-id="2bbd2-124">Scenario_Client コンソールで入力が求められ、対応する出力が Scenario コンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-124">The Scenario_Client console prompts you for inputs and the corresponding output is seen in the Scenario console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2bbd2-125">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2bbd2-126">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2bbd2-127">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2bbd2-128">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2bbd2-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`  
  
## <a name="see-also"></a><span data-ttu-id="2bbd2-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bbd2-129">See Also</span></span>
