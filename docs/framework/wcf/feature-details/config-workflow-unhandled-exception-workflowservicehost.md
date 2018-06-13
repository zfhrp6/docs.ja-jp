---
title: ワークフロー サービスの未処理の例外動作を構成する方法
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: e09575a7998f676ea188a0500f31012c25c19738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489194"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="cb36c-102">ワークフロー サービスの未処理の例外動作を構成する方法</span><span class="sxs-lookup"><span data-stu-id="cb36c-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="cb36c-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> は、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフロー内で未処理の例外が発生した場合のアクションを指定できるようにする動作です。</span><span class="sxs-lookup"><span data-stu-id="cb36c-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="cb36c-104">このトピックでは、この動作を構成ファイルで構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cb36c-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="cb36c-105">WorkflowUnhandledExceptionBehavior を構成するには</span><span class="sxs-lookup"><span data-stu-id="cb36c-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1.  <span data-ttu-id="cb36c-106">追加、<`workflowUnhandledException`> 内の要素、<`behavior`> 内の要素、<`serviceBehaviors`> 要素を使用して、`action`属性を次の例で示すように、ハンドルされない例外が発生したときに実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb36c-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="cb36c-107">前の構成サンプルでは、簡略化された構成を使用しています。</span><span class="sxs-lookup"><span data-stu-id="cb36c-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="cb36c-108">詳細については、次を参照してください。[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb36c-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="cb36c-109">この動作は、次の例に示すように、コードで構成できます。</span><span class="sxs-lookup"><span data-stu-id="cb36c-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="cb36c-110">`action`の属性、<`workflowUnhandledException`> 要素は、次の値のいずれかに設定することができます。</span><span class="sxs-lookup"><span data-stu-id="cb36c-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="cb36c-111">**破棄します。**</span><span class="sxs-lookup"><span data-stu-id="cb36c-111">**abandon**</span></span>  
     <span data-ttu-id="cb36c-112">永続化されているインスタンス状態を変更することなく、メモリ内のインスタンスを中止します (つまり、最後の永続性ポイントにロールバックします)。</span><span class="sxs-lookup"><span data-stu-id="cb36c-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="cb36c-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="cb36c-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="cb36c-114">メモリ内のインスタンスを中止し、永続化されているインスタンスを中断状態に更新します。</span><span class="sxs-lookup"><span data-stu-id="cb36c-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="cb36c-115">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="cb36c-115">**cancel**</span></span>  
     <span data-ttu-id="cb36c-116">インスタンスのキャンセル ハンドラーを呼び出してから、メモリ内のインスタンスを完了状態にします。これにより、そのインスタンスがインスタンス ストアから削除される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="cb36c-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="cb36c-117">**terminate**</span><span class="sxs-lookup"><span data-stu-id="cb36c-117">**terminate**</span></span>  
     <span data-ttu-id="cb36c-118">メモリ内のインスタンスを完了状態にし、そのインスタンスをインスタンス ストアから削除します。</span><span class="sxs-lookup"><span data-stu-id="cb36c-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="cb36c-119">詳細については<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>を参照してください[ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)します。</span><span class="sxs-lookup"><span data-stu-id="cb36c-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb36c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb36c-120">See Also</span></span>  
 [<span data-ttu-id="cb36c-121">ワークフロー サービス ホストの拡張機能</span><span class="sxs-lookup"><span data-stu-id="cb36c-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="cb36c-122">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="cb36c-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
