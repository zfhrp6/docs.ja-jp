---
title: ワークフロー サービスのホストの概要
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 7b5de31b5931af13b41b11af6e48a52b5628e27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="cea08-102">ワークフロー サービスのホストの概要</span><span class="sxs-lookup"><span data-stu-id="cea08-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="cea08-103">ワークフロー サービスを実行するには、ホストされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cea08-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="cea08-104"><xref:System.ServiceModel.WorkflowServiceHost> は、複数のインスタンス、構成、および WCF メッセージングをサポートする標準ワークフロー ホストです (ワークフローはホストされるためにメッセージングを使用する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="cea08-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="cea08-105">また、一連のサービス動作を介して永続性、追跡、およびインスタンス コントロールを統合します。</span><span class="sxs-lookup"><span data-stu-id="cea08-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="cea08-106">WCF の <xref:System.ServiceModel.ServiceHost> と同様に、<xref:System.ServiceModel.WorkflowServiceHost> は任意のマネージ .NET アプリケーションでの自己ホスト、または IIS/WAS での Web ホスト (.xamlx ファイルとして) が可能です。</span><span class="sxs-lookup"><span data-stu-id="cea08-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="cea08-107">このセクションのトピックでは、ワークフロー サービスをホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cea08-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cea08-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="cea08-108">In This Section</span></span>  
 [<span data-ttu-id="cea08-109">ワークフロー サービスのホスティング</span><span class="sxs-lookup"><span data-stu-id="cea08-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="cea08-110">ワークフロー サービスのホスティングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cea08-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="cea08-111">ワークフロー サービス ホストの内部</span><span class="sxs-lookup"><span data-stu-id="cea08-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="cea08-112"><xref:System.ServiceModel.WorkflowServiceHost> がどのように受信メッセージを処理するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cea08-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="cea08-113">ワークフロー サービス ホストの拡張機能</span><span class="sxs-lookup"><span data-stu-id="cea08-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="cea08-114">ワークフロー サービス ホストの機能を拡張する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cea08-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="cea08-115">ワークフロー コントロール エンドポイント</span><span class="sxs-lookup"><span data-stu-id="cea08-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="cea08-116">ワークフロー インスタンスを作成できるエンドポイントを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cea08-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>  
  
 [<span data-ttu-id="cea08-117">方法 : IIS でサービス以外のワークフローをホストする</span><span class="sxs-lookup"><span data-stu-id="cea08-117">How to: Host a non-service workflow in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 <span data-ttu-id="cea08-118">IIS のワークフロー サービスではないワークフローのホスティングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cea08-118">Demonstrates hosting a workflow that is not a workflow service in IIS.</span></span>  
  
 [<span data-ttu-id="cea08-119">方法 : Windows Server AppFabric を使用してワークフロー サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="cea08-119">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="cea08-120">Windows Server AppFabric の既存のワークフロー サービスをホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cea08-120">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="cea08-121">WorkflowServiceHost の構成</span><span class="sxs-lookup"><span data-stu-id="cea08-121">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="cea08-122">永続性、追跡、アイドル状態、および未処理の例外動作を制御する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="cea08-122">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cea08-123">参照</span><span class="sxs-lookup"><span data-stu-id="cea08-123">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="cea08-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="cea08-124">Related Sections</span></span>  
 [<span data-ttu-id="cea08-125">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="cea08-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
