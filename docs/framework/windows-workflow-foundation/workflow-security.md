---
title: "ワークフローのセキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbb1d1efc0758410f12f2c669cca85b9f0e38406
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-security"></a><span data-ttu-id="e161f-102">ワークフローのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="e161f-102">Workflow Security</span></span>
[!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="e161f-103"> は、Microsoft SQL Server や [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] などの複数のさまざまなテクノロジと統合されています。</span><span class="sxs-lookup"><span data-stu-id="e161f-103"> is integrated with several different technologies, such as Microsoft SQL Server and [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="e161f-104">これらのテクノロジと相互作用するうえで、不適切に実行された場合にワークフローでセキュリティの問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="e161f-104">Interacting with these technologies may introduce security issues into your workflow if done improperly.</span></span>  
  
## <a name="persistence-security-concerns"></a><span data-ttu-id="e161f-105">永続化のセキュリティに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="e161f-105">Persistence Security Concerns</span></span>  
  
1.  <span data-ttu-id="e161f-106"><xref:System.Activities.Statements.Delay> アクティビティと永続化を使用するワークフローは、サービスによって再アクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-106">Workflows that use a <xref:System.Activities.Statements.Delay> activity and persistence need to be reactivated by a service.</span></span> <span data-ttu-id="e161f-107">Windows AppFabric はワークフロー管理サービス (WMS) を使用して、タイマーが期限切れのワークフローを再アクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="e161f-107">Windows AppFabric uses the Workflow Management Service (WMS) to reactivate workflows with expired timers.</span></span> <span data-ttu-id="e161f-108">WMS は <xref:System.ServiceModel.WorkflowServiceHost> を作成して、再アクティブ化されたワークフローをホストします。</span><span class="sxs-lookup"><span data-stu-id="e161f-108">WMS creates a <xref:System.ServiceModel.WorkflowServiceHost> to host the reactivated workflow.</span></span> <span data-ttu-id="e161f-109">WMS サービスが停止した場合、永続化されたワークフローはタイマーが時間切れになっていると再アクティブ化されません。</span><span class="sxs-lookup"><span data-stu-id="e161f-109">If the WMS service is stopped, persisted workflows will not be reactivated when their timers expire.</span></span>  
  
2.  <span data-ttu-id="e161f-110">永続的なインスタンスへのアクセスは、アプリケーション ドメイン外の安全でないエンティティから保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-110">Access to durable instancing should be protected against malicious entities external to the application domain.</span></span> <span data-ttu-id="e161f-111">また、開発者は、悪意のあるコードが永続性インスタンス化コードと同じアプリケーション ドメインで実行できないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-111">In addition, developers should ensure that malicious code can't be executed in the same application domain as the durable instancing code.</span></span>  
  
3.  <span data-ttu-id="e161f-112">永続性インスタンス化は、高い (管理者の) アクセス許可で実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="e161f-112">Durable instancing should not be run with elevated (Administrator) permissions.</span></span>  
  
4.  <span data-ttu-id="e161f-113">アプリケーション ドメインの外部で処理されるデータは、保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-113">Data being processed outside the application domain should be protected.</span></span>  
  
5.  <span data-ttu-id="e161f-114">セキュリティの分離を必要とするアプリケーションは、スキーマ抽象化と同じインスタンスを共有しないようにします。</span><span class="sxs-lookup"><span data-stu-id="e161f-114">Applications that require security isolation should not share the same instance of the schema abstraction.</span></span> <span data-ttu-id="e161f-115">このようなアプリケーションは、異なるストア プロバイダーを使用するか、別のストアのインスタンス化を使用するように構成されたストア プロバイダーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-115">Such applications should use different store providers, or store providers configured to use different store instantiations.</span></span>  
  
## <a name="sql-server-security-concerns"></a><span data-ttu-id="e161f-116">SQL サーバーのセキュリティに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="e161f-116">SQL Server Security Concerns</span></span>  
  
-   <span data-ttu-id="e161f-117">子アクティビティ、場所、ブックマーク、ホストの拡張機能、またはスコープを多数使用する場合、またはペイロードが非常に大きいブックマークを使用する場合、メモリが不足したり、永続化の実行中に必要以上のディスク容量が割り当てられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-117">When large numbers of child activities, locations, bookmarks, host extensions, or scopes are used, or when bookmarks with very large payloads are used, memory can be exhausted, or undue amounts of database space can be allocated during persistence.</span></span> <span data-ttu-id="e161f-118">オブジェクト レベルおよびデータベース レベルのセキュリティを使用すると、このような状態を緩和できます。</span><span class="sxs-lookup"><span data-stu-id="e161f-118">This can be mitigated by using object-level and database-level security.</span></span>  
  
-   <span data-ttu-id="e161f-119"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用する場合、インスタンス ストアをセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-119">When using <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the instance store must be secured.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="e161f-120">[SQL Server のベスト プラクティス](http://go.microsoft.com/fwlink/?LinkId=164972)です。</span><span class="sxs-lookup"><span data-stu-id="e161f-120"> [SQL Server Best Practices](http://go.microsoft.com/fwlink/?LinkId=164972).</span></span>  
  
-   <span data-ttu-id="e161f-121">インスタンス ストアの機密情報は暗号化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-121">Sensitive data in the instance store should be encrypted.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="e161f-122">[SQL セキュリティ暗号化](http://go.microsoft.com/fwlink/?LinkId=164976)です。</span><span class="sxs-lookup"><span data-stu-id="e161f-122"> [SQL Security Encryption](http://go.microsoft.com/fwlink/?LinkId=164976).</span></span>  
  
-   <span data-ttu-id="e161f-123">多くの場合、データベース接続文字列は構成ファイルに含まれているので、Windows レベルのセキュリティ (ACL) を使用して、構成ファイル (通常は Web.Config) が安全であるように、またログインとパスワードの情報が接続文字列に含まれないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-123">Since the database connection string is often included in a configuration file, windows-level security (ACL) should be used to ensure that the configuration file (Web.Config usually) is secure, and that login and password information are not included in the connection string.</span></span> <span data-ttu-id="e161f-124">Windows 認証をデータベースと Web サーバー間で代わりに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-124">Windows authentication should be used between the database and the web server instead.</span></span>  
  
## <a name="considerations-for-workflowservicehost"></a><span data-ttu-id="e161f-125">WorkflowServiceHost に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="e161f-125">Considerations for WorkflowServiceHost</span></span>  
  
-   <span data-ttu-id="e161f-126">ワークフローで使用されている [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] のエンドポイントは、セキュリティで保護される必要があります。</span><span class="sxs-lookup"><span data-stu-id="e161f-126">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] endpoints used in workflows should be secured.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="e161f-127">[WCF セキュリティの概要](http://go.microsoft.com/fwlink/?LinkID=164975)です。</span><span class="sxs-lookup"><span data-stu-id="e161f-127"> [WCF Security Overview](http://go.microsoft.com/fwlink/?LinkID=164975).</span></span>  
  
-   <span data-ttu-id="e161f-128"><xref:System.ServiceModel.ServiceAuthorizationManager> を使用して、ホスト レベルの認証を実装できます。</span><span class="sxs-lookup"><span data-stu-id="e161f-128">Host-level authorization can be implemented by using <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span> <span data-ttu-id="e161f-129">参照してください[操作方法: サービスのカスタム承認マネージャーを作成する](http://go.microsoft.com/fwlink/?LinkId=192228)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="e161f-129">See [How To: Create a Custom Authorization Manager for a Service](http://go.microsoft.com/fwlink/?LinkId=192228) for details.</span></span> <span data-ttu-id="e161f-130">これは、次のサンプル」でも例示されて:[ワークフロー サービスのセキュリティ保護する](../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="e161f-130">This is also demonstrated in the following sample: [Securing Workflow Services](../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md).</span></span>  
  
-   <span data-ttu-id="e161f-131">受信メッセージの ServiceSecurityContext は、OperationContext へのアクセスによって、ワーク フロー内からも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e161f-131">The ServiceSecurityContext for the incoming message is also available from within workflow by accessing OperationContext.</span></span>  <span data-ttu-id="e161f-132">参照してください[からワークフロー サービスから OperationContext へのアクセス](../../../docs/framework/wcf/feature-details/accessing-operationcontext-from-a-workflow-service.md)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="e161f-132">See [Accessing OperationContext from a Workflow Service](../../../docs/framework/wcf/feature-details/accessing-operationcontext-from-a-workflow-service.md) for details.</span></span>  
  
## <a name="wf-security-pack-ctp"></a><span data-ttu-id="e161f-133">WF Security Pack CTP</span><span class="sxs-lookup"><span data-stu-id="e161f-133">WF Security Pack CTP</span></span>  
 <span data-ttu-id="e161f-134">Microsoft WF Security Pack CTP 1 は、一連のアクティビティとその実装がに基づいて最初の community technology preview (CTP) リリース[Windows Workflow Foundation](http://msdn.microsoft.com/netframework/aa663328.aspx)で[.NET Framework 4](http://msdn.microsoft.com/netframework/default.aspx) (WF4) で、 [Windows Identity Foundation (WIF)](http://msdn.microsoft.com/security/aa570351.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="e161f-134">The Microsoft WF Security Pack CTP 1 is the first community technology preview (CTP) release of a set of activities and their implementation based on [Windows Workflow Foundation](http://msdn.microsoft.com/netframework/aa663328.aspx)in [.NET Framework 4](http://msdn.microsoft.com/netframework/default.aspx) (WF 4) and the [Windows Identity Foundation (WIF)](http://msdn.microsoft.com/security/aa570351.aspx).</span></span>  <span data-ttu-id="e161f-135">Microsoft WF Security Pack CTP 1 には、アクティビティおよび、ワークフローを使用してさまざまなセキュリティ関連のシナリオを簡単に有効にする方法を示すそのデザイナーの両方が含まれています。これらには以下のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e161f-135">The Microsoft WF Security Pack CTP 1 contains both activities and their designers which illustrate how to easily enable various security-related scenarios using workflow, including:</span></span>  
  
1.  <span data-ttu-id="e161f-136">ワークフローのクライアント ID の偽装</span><span class="sxs-lookup"><span data-stu-id="e161f-136">Impersonating a client identity in the workflow</span></span>  
  
2.  <span data-ttu-id="e161f-137">PrincipalPermission やクレームの検証などの内部ワークフローの認証</span><span class="sxs-lookup"><span data-stu-id="e161f-137">In-workflow authorization, such as PrincipalPermission and validation of Claims</span></span>  
  
3.  <span data-ttu-id="e161f-138">ユーザー名/パスワードやセキュリティ トークン サービス (STS) から取得するトークンなど、ワークフローで指定される ClientCredentials を使用した認証されたメッセージ</span><span class="sxs-lookup"><span data-stu-id="e161f-138">Authenticated messaging using ClientCredentials specified in the workflow, such as username/password or a token retrieved from a Security Token Service (STS)</span></span>  
  
4.  <span data-ttu-id="e161f-139">WS-Trust ActAs を使用して、クライアント セキュリティ トークンをバックエンド サービス (クレーム ベースの委任) にフロー</span><span class="sxs-lookup"><span data-stu-id="e161f-139">Flowing a client security token to a back-end service (claims-based delegation) using WS-Trust ActAs</span></span>  
  
<span data-ttu-id="e161f-140">詳細についてと WF Security Pack CTP をダウンロードするを参照してください: [WF Security Pack CTP](http://wf.codeplex.com/releases/view/48114)</span><span class="sxs-lookup"><span data-stu-id="e161f-140">For more information and to download the WF Security Pack CTP, see: [WF Security Pack CTP](http://wf.codeplex.com/releases/view/48114)</span></span>