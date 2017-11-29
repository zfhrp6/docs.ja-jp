---
title: "ワークフローを作成する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
caps.latest.revision: "34"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f16df123837b2233efd156bf35975e3adbe7279
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="6603e-102">ワークフローを作成する方法</span><span class="sxs-lookup"><span data-stu-id="6603e-102">How to: Create a Workflow</span></span>
<span data-ttu-id="6603e-103">ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。</span><span class="sxs-lookup"><span data-stu-id="6603e-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="6603e-104">など、両方の組み込みのアクティビティを使用するワークフローの作成には、このセクションで手順内のこのトピック、<xref:System.Activities.Statements.Flowchart>アクティビティ、およびカスタム アクティビティを以前から[する方法: アクティビティを作成する](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="6603e-104">This topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="6603e-105">このワークフローは、数値推測ゲームをモデル化しています。</span><span class="sxs-lookup"><span data-stu-id="6603e-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="6603e-106">このセクションのトピックの 1 つだけでチュートリアルを終わることができます。目的のスタイルを選択し、手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="6603e-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="6603e-107">ただし、必要に応じて、すべてのトピックを修了することができます。</span><span class="sxs-lookup"><span data-stu-id="6603e-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6603e-108">チュートリアル入門の各トピックは、前のトピックに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="6603e-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="6603e-109">このトピックの内容を完了する必要があります最初に完了する[する方法: アクティビティを作成する](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)です。</span><span class="sxs-lookup"><span data-stu-id="6603e-109">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6603e-110">チュートリアルの完成版をダウンロードするには、「 [Windows Workflow Foundation (WF45) - Getting Started Tutorial (Windows Workflow Foundation (WF45) - チュートリアル入門)](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6603e-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6603e-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6603e-111">In This Section</span></span>  
 [<span data-ttu-id="6603e-112">シーケンシャル ワークフローを作成する方法</span><span class="sxs-lookup"><span data-stu-id="6603e-112">How to: Create a Sequential Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="6603e-113"><xref:System.Activities.Statements.Sequence> アクティビティを使用してシーケンシャルなワークフローを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6603e-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="6603e-114">フローチャート ワークフローを作成する方法</span><span class="sxs-lookup"><span data-stu-id="6603e-114">How to: Create a Flowchart Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="6603e-115"><xref:System.Activities.Statements.Flowchart> アクティビティを使用してフローチャート ワークフローを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6603e-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="6603e-116">方法: ステート マシン ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="6603e-116">How to: Create a State Machine Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="6603e-117"><xref:System.Activities.Statements.StateMachine> アクティビティを使用してステート マシン ワークフローを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6603e-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6603e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6603e-118">See Also</span></span>  
 [<span data-ttu-id="6603e-119">Windows Workflow Foundation プログラミング</span><span class="sxs-lookup"><span data-stu-id="6603e-119">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
