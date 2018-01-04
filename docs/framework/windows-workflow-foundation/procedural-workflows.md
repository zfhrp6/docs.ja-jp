---
title: "手続き型ワークフロー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10cf83264fbdc2ed3dc088c11865c630c0b8f4f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="procedural-workflows"></a><span data-ttu-id="30ee3-102">手続き型ワークフロー</span><span class="sxs-lookup"><span data-stu-id="30ee3-102">Procedural Workflows</span></span>
<span data-ttu-id="30ee3-103">手続き型ワークフローでは、手続き型言語と似たフロー制御方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="30ee3-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="30ee3-104">これらの構造には `While` と `If` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="30ee3-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="30ee3-105">これらのワークフローは、<xref:System.Activities.Statements.Flowchart> や <xref:System.Activities.Statements.Sequence> など、他のフロー制御アクティビティを使用して自由に構成できます。</span><span class="sxs-lookup"><span data-stu-id="30ee3-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="30ee3-106">実行フローの制御</span><span class="sxs-lookup"><span data-stu-id="30ee3-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="30ee3-107">ワークフロー アクティビティ ライブラリには、手続き型言語で使用されるほとんどのフロー制御方法をモデル化するアクティビティがあります。</span><span class="sxs-lookup"><span data-stu-id="30ee3-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="30ee3-108">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="30ee3-108">These include:</span></span>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="30ee3-109">フロー制御アクティビティを使用するドラッグ アンド ドロップしてから、**アクティビティ**ツールボックス、デザイナー ウィンドウ内の複合アクティビティにします。</span><span class="sxs-lookup"><span data-stu-id="30ee3-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30ee3-110">[!INCLUDE[dublin](../../../includes/dublin-md.md)] を使用して Web ファーム上でワークフローをホストすると、AppFabric のインスタンスは複数の AppFabric サーバー間を移動します。</span><span class="sxs-lookup"><span data-stu-id="30ee3-110">If using the [!INCLUDE[dublin](../../../includes/dublin-md.md)] to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="30ee3-111">この機能を利用するには、リソースがすべてのノード間で共有可能になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="30ee3-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="30ee3-112">既定の NET 4 ワークフロー アクティビティには、ローカル リソースにアクセスする操作は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="30ee3-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="30ee3-113">AppFabric には特定のワークフローを不変に設定するメカニズムがないため、ワークフローが移動されるとエラーが発生するようなカスタム アクティビティは絶対に作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="30ee3-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ee3-114">参照</span><span class="sxs-lookup"><span data-stu-id="30ee3-114">See Also</span></span>  
 [<span data-ttu-id="30ee3-115">Flowchart のワークフロー</span><span class="sxs-lookup"><span data-stu-id="30ee3-115">Flowchart Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
