---
title: "ワークフローの永続性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e65f07fc01d0d364d7271c4f1378b968b687881
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-persistence"></a><span data-ttu-id="36384-102">ワークフローの永続性</span><span class="sxs-lookup"><span data-stu-id="36384-102">Workflow Persistence</span></span>
<span data-ttu-id="36384-103">ワークフローの永続化は、ワークフロー インスタンスの状態を、プロセスやコンピューターの情報に依存せず永続的にキャプチャしたものです。</span><span class="sxs-lookup"><span data-stu-id="36384-103">Workflow persistence is the durable capture of a workflow instance's state, independent of process or computer information.</span></span> <span data-ttu-id="36384-104">永続化の目的は、システム生涯時にワークフロー インスタンスの既知の回復ポイントを提供するため、アクティブに作業を実行していないワークフロー インスタンスをアンロードしてメモリを節約するため、またはワークフロー インスタンスの状態をサーバー ファーム内のあるノードから別のノードに移行するためです。</span><span class="sxs-lookup"><span data-stu-id="36384-104">This is done to provide a well-known point of recovery for the workflow instance in the event of system failure, or to preserve memory by unloading workflow instances that are not actively doing work, or to move the state of the workflow instance from one node to another node in a server farm.</span></span>  
  
 <span data-ttu-id="36384-105">永続化によって、プロセスの迅速性、拡張性、エラー時の回復、およびメモリをより効率的に管理できる機能を実現できます。</span><span class="sxs-lookup"><span data-stu-id="36384-105">Persistence enables process agility, scalability, recovery in the face of failure, and the ability to manage memory more efficiently.</span></span> <span data-ttu-id="36384-106">永続化プロセスには永続化ポイントの指定や保存するデータの収集が含まれ、最終的にはデータの実際のストレージが永続化プロバイダーにデリゲートされます。</span><span class="sxs-lookup"><span data-stu-id="36384-106">The persistence process includes the identification of a persistence point, the gathering of the data to be saved, and finally the delegation of the actual storage of the data to a persistence provider.</span></span>  
  
 <span data-ttu-id="36384-107">ワークフローの永続化を有効にするには、インスタンス ストアに関連付ける必要があります、 **WorkflowApplication**または**WorkflowServiceHost**で示した[する方法: 永続化を有効にします。ワークフローとワークフロー サービス](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="36384-107">To enable persistence for a workflow, you need to associate an instance store with the **WorkflowApplication** or **WorkflowServiceHost** as mentioned in [How to: Enable Persistence for Workflows and Workflow Services](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="36384-108">**WorkflowApplication**と**WorkflowServiceHost**それらに関連付けられたインスタンス ストアを使用して、永続化ストアおよびにワークフロー インスタンスの読み込みに永続化ワークフロー インスタンスを有効にするには永続化ストアに格納されているワークフロー インスタンスのデータに基づくメモリです。</span><span class="sxs-lookup"><span data-stu-id="36384-108">The **WorkflowApplication** and **WorkflowServiceHost** use the instance store associated with them to enable persisting workflow instances into a persistence store and loading workflow instances into memory based on the workflow instance data stored in the persistence store.</span></span>  
  
 <span data-ttu-id="36384-109">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]が付属しています、 **SqlWorkflowInstanceStore**クラスは、SQL Server 2005 または SQL Server 2008 データベースにワークフロー インスタンスに関するデータおよびメタデータの永続化できます。</span><span class="sxs-lookup"><span data-stu-id="36384-109">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with the **SqlWorkflowInstanceStore** class, which allows persistence of data and metadata about workflow instances into a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="36384-110">参照してください[SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="36384-110">See [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) for more details.</span></span>  
  
 <span data-ttu-id="36384-111">アプリケーション固有のデータをワークフロー インスタンス関連の情報と共に格納し、読み込むために、<xref:System.Activities.Persistence.PersistenceParticipant> クラスを拡張する永続参加要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="36384-111">To store and load your application-specific data along with the workflow instance-related information, you can create persistence participants that extend the <xref:System.Activities.Persistence.PersistenceParticipant> class.</span></span> <span data-ttu-id="36384-112">永続参加要素は永続化プロセスに参加して、カスタムのシリアル化可能なデータを永続化ストアに保存し、インスタンス ストアからメモリにデータを読み込み、永続化トランザクションで任意の追加ロジックを実行します。</span><span class="sxs-lookup"><span data-stu-id="36384-112">A persistence participant participates in the persistence process to save custom serializable data into the persistence store, to load the data from the instance store into memory, and to perform any additional logic under a persistence transaction.</span></span> <span data-ttu-id="36384-113">詳細については、次を参照してください。[永続参加要素](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)です。</span><span class="sxs-lookup"><span data-stu-id="36384-113">For more information, see [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).</span></span>  
  
 <span data-ttu-id="36384-114">Windows Server App Fabric を使用すると、永続化の構成のプロセスを簡潔化できます。</span><span class="sxs-lookup"><span data-stu-id="36384-114">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="36384-115">[Windows Server App Fabric で永続化の概念](http://go.microsoft.com/fwlink/?LinkId=201200)</span><span class="sxs-lookup"><span data-stu-id="36384-115"> [Persistence Concepts with Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201200)</span></span>  
  
## <a name="implicit-persistence-points"></a><span data-ttu-id="36384-116">暗黙的な永続化ポイント</span><span class="sxs-lookup"><span data-stu-id="36384-116">Implicit Persistence Points</span></span>  
 <span data-ttu-id="36384-117">次の一覧は、インスタンス ストアがワークフローに関連付けられている場合にワークフローが永続化される条件の例です。</span><span class="sxs-lookup"><span data-stu-id="36384-117">The following list contains examples of the conditions upon which a workflow is persisted when an instance store is associated with a workflow.</span></span>  
  
-   <span data-ttu-id="36384-118">ときに、 **TransactionScope**アクティビティの完了または**TransactedReceiveScope**アクティビティが完了します。</span><span class="sxs-lookup"><span data-stu-id="36384-118">When a **TransactionScope** activity completes or a **TransactedReceiveScope** activity completes.</span></span>  
  
-   <span data-ttu-id="36384-119">ワークフロー インスタンスがアイドル状態になったと**WorkflowIdleBehavior**ワークフロー ホストに設定します。</span><span class="sxs-lookup"><span data-stu-id="36384-119">When a workflow instance becomes idle and the **WorkflowIdleBehavior** is set on workflow host.</span></span> <span data-ttu-id="36384-120">これが発生した、たとえば、メッセージング アクティビティを使用する場合、または、**遅延**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="36384-120">This occurs, for example, when you use messaging activities or a **Delay** activity.</span></span>  
  
-   <span data-ttu-id="36384-121">WorkflowApplication がアイドル状態になったと**PersistableIdle**アプリケーションのプロパティに設定されて**PersistableIdleAction.Persist**です。</span><span class="sxs-lookup"><span data-stu-id="36384-121">When a WorkflowApplication becomes idle and the **PersistableIdle** property of the application is set to **PersistableIdleAction.Persist**.</span></span>  
  
-   <span data-ttu-id="36384-122">ホスト アプリケーションに対して、ワークフロー インスタンスの永続化またはアンロードが指示されたとき。</span><span class="sxs-lookup"><span data-stu-id="36384-122">When a host application is instructed to persist or unload a workflow instance.</span></span>  
  
-   <span data-ttu-id="36384-123">ワークフロー インスタンスが終了したとき。</span><span class="sxs-lookup"><span data-stu-id="36384-123">When a workflow instance is terminated or finishes.</span></span>  
  
-   <span data-ttu-id="36384-124">ときに、 **Persist**アクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="36384-124">When a **Persist** activity executes.</span></span>  
  
-   <span data-ttu-id="36384-125">以前のバージョンの Windows Workflow Foundation を使用して開発したワークフロー インスタンスが、相互運用可能な実行中に永続化ポイントに到達したとき。</span><span class="sxs-lookup"><span data-stu-id="36384-125">When an instance of a workflow developed using a previous version of Windows Workflow Foundation encounters a persistence point during interoperable execution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36384-126">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="36384-126">In This Section</span></span>  
  
-   [<span data-ttu-id="36384-127">SQL Workflow Instance Store</span><span class="sxs-lookup"><span data-stu-id="36384-127">SQL Workflow Instance Store</span></span>](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [<span data-ttu-id="36384-128">インスタンス ストア</span><span class="sxs-lookup"><span data-stu-id="36384-128">Instance Stores</span></span>](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [<span data-ttu-id="36384-129">永続参加要素</span><span class="sxs-lookup"><span data-stu-id="36384-129">Persistence Participants</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [<span data-ttu-id="36384-130">永続化のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="36384-130">Persistence Best Practices</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [<span data-ttu-id="36384-131">非永続化ワークフロー インスタンス</span><span class="sxs-lookup"><span data-stu-id="36384-131">Non-Persisted Workflow Instances</span></span>](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [<span data-ttu-id="36384-132">ワークフローの一時停止と再開</span><span class="sxs-lookup"><span data-stu-id="36384-132">Pausing and Resuming a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
