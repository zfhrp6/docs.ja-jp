---
title: "ワークフロー インスタンスの作成と実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d53becfc126f1acee4759ddff956b4435c9aa769
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="af855-102">ワークフロー インスタンスの作成と実行</span><span class="sxs-lookup"><span data-stu-id="af855-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="af855-103">このサンプルでは、ワークフロー インスタンスを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af855-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="af855-104">ここでは、ワークフロー インスタンスを同期的または非同期的に実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af855-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="af855-105">使用例</span><span class="sxs-lookup"><span data-stu-id="af855-105">Demonstrates</span></span>  
 <span data-ttu-id="af855-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="af855-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="af855-107">説明</span><span class="sxs-lookup"><span data-stu-id="af855-107">Discussion</span></span>  
 <span data-ttu-id="af855-108">サンプルの最初の部分では <xref:System.Activities.WorkflowInvoker.Invoke%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="af855-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="af855-109">これはワークフローを実行する最も基本的な方法です。</span><span class="sxs-lookup"><span data-stu-id="af855-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="af855-110"><xref:System.Activities.WorkflowInvoker.Invoke%2A> を使用して実行するワークフローは同期的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="af855-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="af855-111">サンプルの 2 番目の部分は <xref:System.Activities.WorkflowApplication> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="af855-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="af855-112"><xref:System.Activities.WorkflowApplication> を使用すると、各インスタンスをより細かく制御できるようになり、実行中のワークフローと対話したり、ワークフローを非同期的に実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="af855-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="af855-113">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="af855-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="af855-114">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="af855-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="af855-115">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="af855-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af855-116">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="af855-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="af855-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="af855-117">See Also</span></span>  
 [<span data-ttu-id="af855-118">WorkflowInvoker と WorkflowApplication の使用</span><span class="sxs-lookup"><span data-stu-id="af855-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
