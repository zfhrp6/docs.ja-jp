---
title: '&lt;sqlWorkflowInstanceStore&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 530d515c3913bb103fcc1b5f0c76670db03b71b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsqlworkflowinstancestoregt"></a><span data-ttu-id="32f56-102">&lt;sqlWorkflowInstanceStore&gt;</span><span class="sxs-lookup"><span data-stu-id="32f56-102">&lt;sqlWorkflowInstanceStore&gt;</span></span>
<span data-ttu-id="32f56-103">サービスの動作を構成することができます、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>機能で、SQL Server 2005 または SQL Server 2008 データベースにワークフロー サービス インスタンスの永続化の状態情報をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="32f56-103">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="32f56-104">この機能の詳細については、次を参照してください。 [SQL Workflow Instance Store](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)です。</span><span class="sxs-lookup"><span data-stu-id="32f56-104">For more information on this feature, see [SQL Workflow Instance Store](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span>  
  
<span data-ttu-id="32f56-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="32f56-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="32f56-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="32f56-106">\<behaviors></span></span>  
<span data-ttu-id="32f56-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="32f56-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="32f56-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="32f56-108">\<behavior></span></span>  
<span data-ttu-id="32f56-109">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="32f56-109">\<sqlWorkflowInstanceStore></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32f56-110">構文</span><span class="sxs-lookup"><span data-stu-id="32f56-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String" 
                                honstLockRenewalPeriod="TimeSpan" 
                                instanceCompletionAction="DeleteNothing/DeleteAll" 
                                instanceEncodingAction="None/GZip" 
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32f56-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="32f56-111">Attributes and Elements</span></span>  
 <span data-ttu-id="32f56-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="32f56-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32f56-113">属性</span><span class="sxs-lookup"><span data-stu-id="32f56-113">Attributes</span></span>  
  
|<span data-ttu-id="32f56-114">属性</span><span class="sxs-lookup"><span data-stu-id="32f56-114">Attribute</span></span>|<span data-ttu-id="32f56-115">説明</span><span class="sxs-lookup"><span data-stu-id="32f56-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32f56-116">connectionString</span><span class="sxs-lookup"><span data-stu-id="32f56-116">connectionString</span></span>|<span data-ttu-id="32f56-117">基になる永続性データベースへの接続に使用する接続文字列を含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="32f56-117">A string that contains a connection string used to connect to an underlying persistence database.</span></span>|  
|<span data-ttu-id="32f56-118">connectionStringName</span><span class="sxs-lookup"><span data-stu-id="32f56-118">connectionStringName</span></span>|<span data-ttu-id="32f56-119">データベース サーバーに名前付き接続文字列を含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="32f56-119">A string that contains a named connection string to the database server.</span></span> <span data-ttu-id="32f56-120">名前付き接続文字列の例は、"DefaultConnectionString"です。</span><span class="sxs-lookup"><span data-stu-id="32f56-120">An example of a named connection string is "DefaultConnectionString".</span></span>|  
|<span data-ttu-id="32f56-121">honstLockRenewalPeriod</span><span class="sxs-lookup"><span data-stu-id="32f56-121">honstLockRenewalPeriod</span></span>|<span data-ttu-id="32f56-122">ホストがインスタンスのロックを更新するまでの時間を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="32f56-122">A Timespan value that specifies the time period in which the host must renew the lock on an instance.</span></span> <span data-ttu-id="32f56-123">指定した時間内にホストがロックを更新しない場合は、インスタンスのロックが解除され、他のホストがそのインスタンスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="32f56-123">If the host does not renew the lock in the specified time period, the instance is unlocked and may be picked up by another host.</span></span><br /><br /> <span data-ttu-id="32f56-124">ワークフローをアンロードすることは、同時に、永続化することも意味します。</span><span class="sxs-lookup"><span data-stu-id="32f56-124">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="32f56-125">この属性は、ワークフロー インスタンスが永続化し、アンロードした直後にゼロに設定されている場合、ワークフローはアイドル状態になります。</span><span class="sxs-lookup"><span data-stu-id="32f56-125">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="32f56-126">この属性を TimeSpan.MaxValue を効果的に設定すると、アンロード操作が無効にします。</span><span class="sxs-lookup"><span data-stu-id="32f56-126">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="32f56-127">アイドル状態になったワークフロー インスタンスはアンロードされません。</span><span class="sxs-lookup"><span data-stu-id="32f56-127">Idle workflow instances are never unloaded.</span></span>|  
|<span data-ttu-id="32f56-128">instanceCompletionAction</span><span class="sxs-lookup"><span data-stu-id="32f56-128">instanceCompletionAction</span></span>|<span data-ttu-id="32f56-129">ワークフロー インスタンス完了後にワークフロー インスタンス データを永続化ストアに保持するか、またはその時点で削除するかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="32f56-129">A value that specifies whether workflow instance data is kept in the persistence store after the workflow instance completes or if it is deleted at that point.</span></span> <span data-ttu-id="32f56-130">この値は、<xref:System.Activities.DurableInstancing.InstanceCompletionAction> 型です。</span><span class="sxs-lookup"><span data-stu-id="32f56-130">This value is of type <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.</span></span><br /><br /> <span data-ttu-id="32f56-131">列挙されるアクションは、インスタンスがその操作を完了したとき、永続化ストアからインスタンス データを削除するかどうかで構成されます。</span><span class="sxs-lookup"><span data-stu-id="32f56-131">The enumerated actions consist of deleting the instance data from the persistence store or not deleting the instance data from the persistence store, when the instance has completed its operation.</span></span><br /><br /> <span data-ttu-id="32f56-132">完了後にインスタンスを保持すると、永続性データベースが急速に増大して、データベースのパフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="32f56-132">Keeping instances after completion causes the persistence database to grow rapidly and this affects the performance of the database.</span></span> <span data-ttu-id="32f56-133">データベースのパフォーマンスがパフォーマンス要件を満たすレベルになるように、これらのレコードを定期的に削除するパージ ポリシーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32f56-133">You should configure a database purge policy to delete these records periodically to ensure that the performance of the database is at the level that satisfy your performance requirements.</span></span>|  
|<span data-ttu-id="32f56-134">instanceEncodingOption</span><span class="sxs-lookup"><span data-stu-id="32f56-134">instanceEncodingOption</span></span>|<span data-ttu-id="32f56-135">インスタンス状態情報を永続化ストアに格納する前に、GZip アルゴリズムで圧縮するかどうかを指定する、省略可能な値。</span><span class="sxs-lookup"><span data-stu-id="32f56-135">An optional value that specifies  whether the instance state information is compressed using the GZip algorithm before the information is saved in the persistence store..</span></span> <span data-ttu-id="32f56-136">この値は、`System.Activities.DurableInstancing.InstanceEncodingAction` 型です。</span><span class="sxs-lookup"><span data-stu-id="32f56-136">This value is of type `System.Activities.DurableInstancing.InstanceEncodingAction`.</span></span> <span data-ttu-id="32f56-137">このプロパティの使用可能な値は"None"、圧縮、および"GZip"は、データは圧縮され、gzip アルゴリズムを使用して、そのインスタンスの指定がないを指定します。</span><span class="sxs-lookup"><span data-stu-id="32f56-137">Possible values for this property are "None", which specifies no compression, and "GZip", which specifies that instance data is compressed and uses the gzip algorithm.</span></span>|  
|<span data-ttu-id="32f56-138">instanceLockedExceptionAction</span><span class="sxs-lookup"><span data-stu-id="32f56-138">instanceLockedExceptionAction</span></span>|<span data-ttu-id="32f56-139">現在、他のホストにロックされているインスタンスをホストがロックしようとしたときにスローされる例外への応答として発生するアクションを指定する値。</span><span class="sxs-lookup"><span data-stu-id="32f56-139">A value that specifies the action that occurs in response to an exception that is thrown when the host tries to lock an instance because the instance is currently locked by another host.</span></span> <span data-ttu-id="32f56-140">この値は、<xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> 型です。</span><span class="sxs-lookup"><span data-stu-id="32f56-140">This value is of type <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.</span></span><br /><br /> <span data-ttu-id="32f56-141">このフィールドで使用できるオプションは、None、Basic Retry、および Aggressive Retry です。</span><span class="sxs-lookup"><span data-stu-id="32f56-141">The options allowed for this field are: None, Basic Retry, and Aggressive Retry.</span></span> <span data-ttu-id="32f56-142">既定値は None です。</span><span class="sxs-lookup"><span data-stu-id="32f56-142">The default value is None.</span></span> <span data-ttu-id="32f56-143">これら 3 つのオプションの説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="32f56-143">The following list provides you with the descriptions for these three options:</span></span><br /><br /> <span data-ttu-id="32f56-144">- なし。</span><span class="sxs-lookup"><span data-stu-id="32f56-144">-   None.</span></span> <span data-ttu-id="32f56-145">サービス ホストはインスタンスをロックしようとせず、<xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。</span><span class="sxs-lookup"><span data-stu-id="32f56-145">The service host does not attempt to lock the instance and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller.</span></span><br /><span data-ttu-id="32f56-146">-基本的な再試行してください。</span><span class="sxs-lookup"><span data-stu-id="32f56-146">-   Basic Retry.</span></span> <span data-ttu-id="32f56-147">サービス ホストは一定の再試行間隔でインスタンスのロックを再試行し、シーケンスの最後に例外を呼び出し元に渡します。</span><span class="sxs-lookup"><span data-stu-id="32f56-147">The service host reattempts to lock the instance with a linear retry interval and passes the exception to the caller at the end of the sequence.</span></span><br /><span data-ttu-id="32f56-148">-積極的な再試行します。</span><span class="sxs-lookup"><span data-stu-id="32f56-148">-   Aggressive Retry.</span></span> <span data-ttu-id="32f56-149">サービス ホストは指数関数的に増加する遅延を使用してインスタンスのロックを再試行し、シーケンスの最後に <xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。</span><span class="sxs-lookup"><span data-stu-id="32f56-149">The service host reattempts to lock the instance with an exponentially increasing delay and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller at the end of the sequence.</span></span>|  
|<span data-ttu-id="32f56-150">runnableInstancesDetectionPeriod</span><span class="sxs-lookup"><span data-stu-id="32f56-150">runnableInstancesDetectionPeriod</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="32f56-151">子要素</span><span class="sxs-lookup"><span data-stu-id="32f56-151">Child Elements</span></span>  
 <span data-ttu-id="32f56-152">なし。</span><span class="sxs-lookup"><span data-stu-id="32f56-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32f56-153">親要素</span><span class="sxs-lookup"><span data-stu-id="32f56-153">Parent Elements</span></span>  
  
|<span data-ttu-id="32f56-154">要素</span><span class="sxs-lookup"><span data-stu-id="32f56-154">Element</span></span>|<span data-ttu-id="32f56-155">説明</span><span class="sxs-lookup"><span data-stu-id="32f56-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32f56-156">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="32f56-156">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="32f56-157">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="32f56-157">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32f56-158">参照</span><span class="sxs-lookup"><span data-stu-id="32f56-158">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>  
 [<span data-ttu-id="32f56-159">SQL Workflow Instance Store</span><span class="sxs-lookup"><span data-stu-id="32f56-159">SQL Workflow Instance Store</span></span>](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)
