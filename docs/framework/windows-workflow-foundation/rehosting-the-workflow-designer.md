---
title: "ワークフロー デザイナーのホスト変更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba0308505f54b7c96259af5d797dd7c1957e6a92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="e846d-102">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="e846d-102">Rehosting the Workflow Designer</span></span>
<span data-ttu-id="e846d-103">[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]は、ワークフローを作成、変更、および監視する目的で [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 以外の環境にホストを変更できます。</span><span class="sxs-lookup"><span data-stu-id="e846d-103">The [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] can be rehosted in environments outside of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] for the purposes of creating, modifying, and monitoring workflows.</span></span>  
  
 <span data-ttu-id="e846d-104"><xref:System.Activities.Presentation.WorkflowDesigner> 型はキャンバス、プロパティ グリッド、および他の要素のラッパーであり、デザイナーのホスト変更シナリオの多くに対応する基本的なプログラミング モデルを公開しています。</span><span class="sxs-lookup"><span data-stu-id="e846d-104">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="e846d-105"><xref:System.Activities.Presentation.WorkflowDesigner> アプリケーション内での [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] のホストは、[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]の一般的なホスト変更シナリオです。</span><span class="sxs-lookup"><span data-stu-id="e846d-105">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application is a common rehosting scenario for [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e846d-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e846d-106">In This Section</span></span>  
 [<span data-ttu-id="e846d-107">タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="e846d-107">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
  
 [<span data-ttu-id="e846d-108">タスク 2: ワークフロー デザイナーのホスティング</span><span class="sxs-lookup"><span data-stu-id="e846d-108">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)  
  
 [<span data-ttu-id="e846d-109">タスク 3: ツールボックス ペインと PropertyGrid ペインの作成</span><span class="sxs-lookup"><span data-stu-id="e846d-109">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)  
  
 [<span data-ttu-id="e846d-110">再ホストされたワークフロー デザイナーにおける Workflow Foundation 4.5 の新機能のサポート</span><span class="sxs-lookup"><span data-stu-id="e846d-110">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)  
  
## <a name="see-also"></a><span data-ttu-id="e846d-111">参照</span><span class="sxs-lookup"><span data-stu-id="e846d-111">See Also</span></span>  
 [<span data-ttu-id="e846d-112">ワークフロー デザイン操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="e846d-112">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
