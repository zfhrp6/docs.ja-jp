---
title: WorkflowServiceHost を使用してアイドル動作を構成する方法
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22c71c0840b4fa44c585dfac4d99bdcbb3227fdb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="8b17f-102">WorkflowServiceHost を使用してアイドル動作を構成する方法</span><span class="sxs-lookup"><span data-stu-id="8b17f-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="8b17f-103">ワークフローは、外部からの働きかけによって再開される必要があるブックマークに遭遇すると、アイドル状態になります。たとえば、 <xref:System.ServiceModel.Activities.Receive> アクティビティを使用して配信されるメッセージをワークフローが待機している場合などです。</span><span class="sxs-lookup"><span data-stu-id="8b17f-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="8b17f-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> は、サービス インスタンスがアイドル状態になってから、インスタンスが永続化またはアンロードされるまでの時間を指定できる動作です。</span><span class="sxs-lookup"><span data-stu-id="8b17f-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="8b17f-105">これには、これらの時間の範囲を設定する 2 つのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8b17f-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="8b17f-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスが永続化されるまでの時間の範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="8b17f-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="8b17f-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスがアンロードされるまでの時間の範囲を指定します。アンロードとは、インスタンスをインスタンス ストアに永続化し、メモリから削除することを意味します。</span><span class="sxs-lookup"><span data-stu-id="8b17f-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="8b17f-108">このトピックでは、 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> を構成ファイルで構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8b17f-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="8b17f-109">WorkflowIdleBehavior を構成するには</span><span class="sxs-lookup"><span data-stu-id="8b17f-109">To configure WorkflowIdleBehavior</span></span>  
  
1.  <span data-ttu-id="8b17f-110">追加、<`workflowIdle`> 要素を <`behavior`> 内の要素、<`serviceBehaviors`> 要素の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="8b17f-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="8b17f-111">`timeToUnload` 属性は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスがアンロードされるまでの時間の範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="8b17f-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="8b17f-112">`timeToPersist` 属性は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスが永続化されるまでの時間の範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="8b17f-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="8b17f-113">`timeToUnload` の既定値は 1 分です。</span><span class="sxs-lookup"><span data-stu-id="8b17f-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="8b17f-114">`timeToPersist` の既定値は <xref:System.TimeSpan.MaxValue>です。</span><span class="sxs-lookup"><span data-stu-id="8b17f-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="8b17f-115">インスタンスをメモリ内でアイドル状態を保ちながら信頼性を保持する場合、 `timeToPersist` < `timeToUnload`です。</span><span class="sxs-lookup"><span data-stu-id="8b17f-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="8b17f-116">アイドル状態のインスタンスがアンロードされないようにするには、 `timeToUnload` を <xref:System.TimeSpan.MaxValue>に設定します。</span><span class="sxs-lookup"><span data-stu-id="8b17f-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="8b17f-117">詳細については<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>を参照してください[ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="8b17f-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b17f-118">前の構成サンプルでは、簡略化された構成を使用しています。</span><span class="sxs-lookup"><span data-stu-id="8b17f-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="8b17f-119">詳細については、次を参照してください。[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="8b17f-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="8b17f-120">コードのアイドル動作を変更するには</span><span class="sxs-lookup"><span data-stu-id="8b17f-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="8b17f-121">次の例では、プログラムによって永続化とアンロードを行う前に待機する時間を変更します。</span><span class="sxs-lookup"><span data-stu-id="8b17f-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8b17f-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b17f-122">See Also</span></span>  
 [<span data-ttu-id="8b17f-123">ワークフロー サービス ホストの拡張機能</span><span class="sxs-lookup"><span data-stu-id="8b17f-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="8b17f-124">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="8b17f-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="8b17f-125">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="8b17f-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
