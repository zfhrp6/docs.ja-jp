---
title: "ワークフロー ホスティングのオプション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be885a964ad7e8d63045febfa279b23d0d85ab1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-hosting-options"></a><span data-ttu-id="3484d-102">ワークフロー ホスティングのオプション</span><span class="sxs-lookup"><span data-stu-id="3484d-102">Workflow Hosting Options</span></span>
<span data-ttu-id="3484d-103">[!INCLUDE[wf](../../../includes/wf-md.md)] のほとんどのサンプルでは、コンソール アプリケーションでホストされているワークフローが使用されていますが、これは実際のワークフローにとって現実的なシナリオではありません。</span><span class="sxs-lookup"><span data-stu-id="3484d-103">Most of the [!INCLUDE[wf](../../../includes/wf-md.md)] samples use workflows that are hosted in a console application, but this isn't a realistic scenario for real-world workflows.</span></span> <span data-ttu-id="3484d-104">実際のビジネス アプリケーションのワークフローは、開発者が作成した Windows サービス、[!INCLUDE[iisver](../../../includes/iisver-md.md)] や AppFabric などのサーバー アプリケーションのいずれかの永続的なプロセスでホストされます。</span><span class="sxs-lookup"><span data-stu-id="3484d-104">Workflows in actual business applications will be hosted in persistent processes- either a Windows service authored by the developer, or a server application such as [!INCLUDE[iisver](../../../includes/iisver-md.md)] or AppFabric.</span></span> <span data-ttu-id="3484d-105">これらの方法の違いを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3484d-105">The differences between these approaches are as follows.</span></span>  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a><span data-ttu-id="3484d-106">Windows AppFabric を使用した IIS でのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="3484d-106">Hosting workflows in IIS with Windows AppFabric</span></span>  
 <span data-ttu-id="3484d-107">IIS と AppFabric は、ワークフローに推奨されるホストです。</span><span class="sxs-lookup"><span data-stu-id="3484d-107">Using IIS with AppFabric is the preferred host for workflows.</span></span> <span data-ttu-id="3484d-108">AppFabric を使用したワークフローのホスト アプリケーションは Windows プロセス アクティブ化サービスで、これは IIS を介した HTTP への依存関係のみを解消します。</span><span class="sxs-lookup"><span data-stu-id="3484d-108">The host application for workflows using AppFabric is Windows Activation Service, which removes the dependency on HTTP over IIS alone.</span></span>  
  
## <a name="hosting-workflows-in-iis-alone"></a><span data-ttu-id="3484d-109">IIS のみでのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="3484d-109">Hosting workflows in IIS alone</span></span>  
 <span data-ttu-id="3484d-110">[!INCLUDE[iisver](../../../includes/iisver-md.md)] のみを使用することは推奨されていません。AppFabric には、実行中のアプリケーションのメンテナンスを容易にする管理ツールと監視ツールがあるためです。</span><span class="sxs-lookup"><span data-stu-id="3484d-110">Using [!INCLUDE[iisver](../../../includes/iisver-md.md)] alone is not recommended, as there are management and monitoring tools available with AppFabric that facilitate maintenance of running applications.</span></span> <span data-ttu-id="3484d-111">ワークフローを [!INCLUDE[iisver](../../../includes/iisver-md.md)] のみでホストする必要があるのは、AppFabric への移行に関してインフラストラクチャ上の問題がある場合だけです。</span><span class="sxs-lookup"><span data-stu-id="3484d-111">Workflows should only be hosted in [!INCLUDE[iisver](../../../includes/iisver-md.md)] alone if there are infrastructure concerns with moving to AppFabric.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3484d-112">さまざまな理由により、アプリケーション プールは [!INCLUDE[iisver](../../../includes/iisver-md.md)] によって定期的にリサイクルされます。</span><span class="sxs-lookup"><span data-stu-id="3484d-112">[!INCLUDE[iisver](../../../includes/iisver-md.md)] recycles application pools periodically for various reasons.</span></span> <span data-ttu-id="3484d-113">アプリケーション プールがリサイクルされると、IIS は古いプールへのメッセージの受け取りを中止し、新しいアプリケーション プールをインスタンス化して新しい要求を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3484d-113">When an application pool is recycled, IIS stops accepting messages to the old pool, and instantiates a new application pool to accept new requests.</span></span> <span data-ttu-id="3484d-114">ワークフローが応答の送信後も動作し続ける場合、[!INCLUDE[iisver](../../../includes/iisver-md.md)] は作業が完了したことを認識せず、ホスト アプリケーション プールをリサイクルする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3484d-114">If a workflow continues working after sending a response, [!INCLUDE[iisver](../../../includes/iisver-md.md)] will not be aware of the work being done, and may recycle the hosting application pool.</span></span> <span data-ttu-id="3484d-115">このエラーは、ワークフローが中断され、追跡サービスが記録される場合、 [1004 - WorkflowInstanceAborted](../../../docs/framework/windows-workflow-foundation/1004-workflowinstanceaborted.md)理由フィールドが空白のメッセージ。</span><span class="sxs-lookup"><span data-stu-id="3484d-115">If this happens, the workflow will abort, and tracking services will record a [1004 - WorkflowInstanceAborted](../../../docs/framework/windows-workflow-foundation/1004-workflowinstanceaborted.md) message with an empty Reason field.</span></span>  
>   
>  <span data-ttu-id="3484d-116">永続化を使用する場合、ホストは、最後の永続性ポイントから、中止されたインスタンスを明示的に再開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3484d-116">If persistence is used, the host must explicitly restart aborted instances from the last persistence point.</span></span>  
>   
>  <span data-ttu-id="3484d-117">AppFabric を使用する場合、永続化を使用すると、ワークフロー管理サービスは、最終的に、最後に成功した永続性ポイントからワークフローを再開します。</span><span class="sxs-lookup"><span data-stu-id="3484d-117">If AppFabric is used, the workflow management service will eventually resume the workflow from the last successful persistence point if persistence is used.</span></span> <span data-ttu-id="3484d-118">永続化を使用せず、ワークフローが要求/応答パターン以外の操作を実行している場合、ワークフローが中止されるとデータは失われます。</span><span class="sxs-lookup"><span data-stu-id="3484d-118">If no persistence is used, and the workflow performs operations outside a Request/Response pattern, data will be lost when the workflow aborts.</span></span>  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a><span data-ttu-id="3484d-119">カスタム Windows サービスでのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="3484d-119">Hosting a workflow in a custom Windows Service</span></span>  
 <span data-ttu-id="3484d-120">カスタム ワークフロー サービスを作成してワークフローをホストする場合、開発者は AppFabric に標準搭載されている多くの機能を複製する必要がありますが、カスタム機能をより柔軟に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3484d-120">Creating a custom workflow service to host the workflow will require the developer to duplicate a lot of the functionality provided out-of-box by AppFabric, but will allow for more flexibility with custom functionality.</span></span> <span data-ttu-id="3484d-121">このオプションは、AppFabric を選択できない場合にのみ検討してください。</span><span class="sxs-lookup"><span data-stu-id="3484d-121">This option should only be considered if AppFabric proves to not be an option.</span></span>
