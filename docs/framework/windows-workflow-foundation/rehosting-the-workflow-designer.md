---
title: ワークフロー デザイナーのホスト変更
ms.date: 03/30/2017
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
ms.openlocfilehash: e4e061c078626a90641f84b5ea0875f63bb42f9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513312"
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="74036-102">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="74036-102">Rehosting the Workflow Designer</span></span>
<span data-ttu-id="74036-103">[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]は、ワークフローを作成、変更、および監視する目的で [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 以外の環境にホストを変更できます。</span><span class="sxs-lookup"><span data-stu-id="74036-103">The [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] can be rehosted in environments outside of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] for the purposes of creating, modifying, and monitoring workflows.</span></span>  
  
 <span data-ttu-id="74036-104"><xref:System.Activities.Presentation.WorkflowDesigner> 型はキャンバス、プロパティ グリッド、および他の要素のラッパーであり、デザイナーのホスト変更シナリオの多くに対応する基本的なプログラミング モデルを公開しています。</span><span class="sxs-lookup"><span data-stu-id="74036-104">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="74036-105">ホストしている、<xref:System.Activities.Presentation.WorkflowDesigner>中は、Windows Presentation Foundation (WPF) アプリケーションは、の一般的なホスト変更シナリオ[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="74036-105">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a Windows Presentation Foundation (WPF) application is a common rehosting scenario for [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74036-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="74036-106">In This Section</span></span>  
 [<span data-ttu-id="74036-107">タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="74036-107">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
  
 [<span data-ttu-id="74036-108">タスク 2: ワークフロー デザイナーのホスティング</span><span class="sxs-lookup"><span data-stu-id="74036-108">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)  
  
 [<span data-ttu-id="74036-109">タスク 3: ツールボックス ペインと PropertyGrid ペインの作成</span><span class="sxs-lookup"><span data-stu-id="74036-109">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)  
  
 [<span data-ttu-id="74036-110">再ホストされたワークフロー デザイナーにおける Workflow Foundation 4.5 の新機能のサポート</span><span class="sxs-lookup"><span data-stu-id="74036-110">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)  
  
## <a name="see-also"></a><span data-ttu-id="74036-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="74036-111">See Also</span></span>  
 [<span data-ttu-id="74036-112">ワークフローのデザイン エクスペリエンスのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="74036-112">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
