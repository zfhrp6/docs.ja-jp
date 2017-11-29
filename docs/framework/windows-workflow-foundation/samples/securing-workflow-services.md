---
title: "ワークフロー サービスのセキュリティ保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 601a7312bdf88ac4915478b6d8fb0626b645a0b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="securing-workflow-services"></a><span data-ttu-id="9d2a3-102">ワークフロー サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="9d2a3-102">Securing Workflow Services</span></span>
<span data-ttu-id="9d2a3-103">セキュリティで保護されたワークフロー サービス サンプルでは、次の手順を示します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="9d2a3-104"><xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティを使用して基本ワークフロー サービスを作成する。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="9d2a3-105">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 構成を使用して、ワークフロー サービスで使用するセキュリティで保護されたエンドポイントを定義する。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-105">Using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="9d2a3-106">カスタム ポリシー内にクレームを作成し、<xref:System.ServiceModel.ServiceAuthorizationManager> を使用してクレームを検証する。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9d2a3-107">使用例</span><span class="sxs-lookup"><span data-stu-id="9d2a3-107">Demonstrates</span></span>  
 <span data-ttu-id="9d2a3-108">WCF セキュリティを使用して、クライアントとワークフロー サービス間の通信、クレーム ベースの承認を保護します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9d2a3-109">説明</span><span class="sxs-lookup"><span data-stu-id="9d2a3-109">Discussion</span></span>  
 <span data-ttu-id="9d2a3-110">このサンプルでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティ インフラストラクチャを使用して、通常の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと同様にワークフロー サービスをセキュリティで保護する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-110">This sample demonstrates the use of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security infrastructure to secure a workflow service just like you would with a normal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="9d2a3-111">具体的には、承認にカスタム クレームを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="9d2a3-112">この例では、<xref:System.ServiceModel.WSHttpBinding> とメッセージ モード セキュリティを Windows 資格情報と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="9d2a3-113">カスタムの <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) は、クライアントの Windows ユーザー名をチェックし、特定の文字がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="9d2a3-114">該当する文字がある場合は、クレームを作成して <xref:System.IdentityModel.Policy.EvaluationContext> に追加します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="9d2a3-115">このようにすることで、カスタム ポリシーは、クライアントのユーザー名にこの文字が含まれていることを示すステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="9d2a3-116">このクレームは、呼び出しの有効期間においてクエリできます。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="9d2a3-117">該当の文字は `Constants.cs` で検索できます。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="9d2a3-118">承認ポリシーは、`SecureWorkFlowAuthZManager` 内のクレームを探します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="9d2a3-119">クレームが見つかると、`true` を返し、ワークフローを続行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="9d2a3-120">クレームが見つからない場合は、`false` を返し、クライアントには "アクセスは拒否されました" メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="9d2a3-121">他のクレームもコンテキスト内にあり、`SecureWorkFlowAuthZManager` 内で調べることができます。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="9d2a3-122">このサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="9d2a3-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="9d2a3-123">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を管理者権限で実行します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="9d2a3-124">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] に SecuringWorkflowServices.sln を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="9d2a3-125">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="9d2a3-126">Service プロジェクトをソリューションのスタートアップ プロジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="9d2a3-127">Ctrl キーを押しながら F5 キーを押して、デバッグを行わずにサービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="9d2a3-128">Client プロジェクトをソリューションのスタートアップ プロジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="9d2a3-129">Ctrl キーを押しながら F5 キーを押して、デバッグを行わずにクライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9d2a3-130">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9d2a3-131">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9d2a3-132">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d2a3-133">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9d2a3-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
