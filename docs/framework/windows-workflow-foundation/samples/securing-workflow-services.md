---
title: ワークフロー サービスのセキュリティ保護
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 5dbd724f3a2f8febfc74719584f4d69cbf75b567
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="securing-workflow-services"></a><span data-ttu-id="7af37-102">ワークフロー サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="7af37-102">Securing Workflow Services</span></span>
<span data-ttu-id="7af37-103">セキュリティで保護されたワークフロー サービス サンプルでは、次の手順を示します。</span><span class="sxs-lookup"><span data-stu-id="7af37-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="7af37-104"><xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティを使用して基本ワークフロー サービスを作成する。</span><span class="sxs-lookup"><span data-stu-id="7af37-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="7af37-105">Windows Communication Foundation (WCF) 構成を使用して、ワークフロー サービスで使用するためのセキュリティで保護されたエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="7af37-105">Using Windows Communication Foundation (WCF) configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="7af37-106">カスタム ポリシー内にクレームを作成し、<xref:System.ServiceModel.ServiceAuthorizationManager> を使用してクレームを検証する。</span><span class="sxs-lookup"><span data-stu-id="7af37-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7af37-107">使用例</span><span class="sxs-lookup"><span data-stu-id="7af37-107">Demonstrates</span></span>  
 <span data-ttu-id="7af37-108">WCF セキュリティを使用して、クライアントとワークフロー サービス間の通信、クレーム ベースの承認を保護します。</span><span class="sxs-lookup"><span data-stu-id="7af37-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7af37-109">説明</span><span class="sxs-lookup"><span data-stu-id="7af37-109">Discussion</span></span>  
 <span data-ttu-id="7af37-110">このサンプルでは、通常の WCF サービスの場合と同様に、ワークフロー サービスをセキュリティで保護する WCF のセキュリティ インフラストラクチャの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="7af37-110">This sample demonstrates the use of WCF security infrastructure to secure a workflow service just like you would with a normal WCF service.</span></span> <span data-ttu-id="7af37-111">具体的には、承認にカスタム クレームを使用します。</span><span class="sxs-lookup"><span data-stu-id="7af37-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="7af37-112">この例では、<xref:System.ServiceModel.WSHttpBinding> とメッセージ モード セキュリティを Windows 資格情報と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="7af37-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="7af37-113">カスタムの <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) は、クライアントの Windows ユーザー名をチェックし、特定の文字がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="7af37-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="7af37-114">該当する文字がある場合は、クレームを作成して <xref:System.IdentityModel.Policy.EvaluationContext> に追加します。</span><span class="sxs-lookup"><span data-stu-id="7af37-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="7af37-115">このようにすることで、カスタム ポリシーは、クライアントのユーザー名にこの文字が含まれていることを示すステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7af37-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="7af37-116">このクレームは、呼び出しの有効期間においてクエリできます。</span><span class="sxs-lookup"><span data-stu-id="7af37-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="7af37-117">該当の文字は `Constants.cs` で検索できます。</span><span class="sxs-lookup"><span data-stu-id="7af37-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="7af37-118">承認ポリシーは、`SecureWorkFlowAuthZManager` 内のクレームを探します。</span><span class="sxs-lookup"><span data-stu-id="7af37-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="7af37-119">クレームが見つかると、`true` を返し、ワークフローを続行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7af37-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="7af37-120">クレームが見つからない場合は、`false` を返し、クライアントには "アクセスは拒否されました" メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="7af37-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="7af37-121">他のクレームもコンテキスト内にあり、`SecureWorkFlowAuthZManager` 内で調べることができます。</span><span class="sxs-lookup"><span data-stu-id="7af37-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="7af37-122">このサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="7af37-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="7af37-123">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を管理者権限で実行します。</span><span class="sxs-lookup"><span data-stu-id="7af37-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="7af37-124">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] に SecuringWorkflowServices.sln を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7af37-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="7af37-125">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="7af37-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="7af37-126">Service プロジェクトをソリューションのスタートアップ プロジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="7af37-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="7af37-127">Ctrl キーを押しながら F5 キーを押して、デバッグを行わずにサービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="7af37-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="7af37-128">Client プロジェクトをソリューションのスタートアップ プロジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="7af37-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="7af37-129">Ctrl キーを押しながら F5 キーを押して、デバッグを行わずにクライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="7af37-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7af37-130">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7af37-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7af37-131">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7af37-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7af37-132">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="7af37-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7af37-133">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7af37-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
