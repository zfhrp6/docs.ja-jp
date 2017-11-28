---
title: "簡単なポリシー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c704a9f3f27d63fb1a28db61f03cdc9b8de4370
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="simple-policy"></a><span data-ttu-id="c1c9b-102">簡単なポリシー</span><span class="sxs-lookup"><span data-stu-id="c1c9b-102">Simple Policy</span></span>
<span data-ttu-id="c1c9b-103">このサンプルでは、ワークフロー内で <xref:System.Workflow.Activities.PolicyActivity> アクティビティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-103">This sample shows how to use a <xref:System.Workflow.Activities.PolicyActivity> activity in a workflow.</span></span>  
  
 <span data-ttu-id="c1c9b-104">このサンプルのシーケンシャル ワークフローは、<xref:System.Workflow.Activities.PolicyActivity> アクティビティを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-104">The sequential workflow in this sample is created by using a <xref:System.Workflow.Activities.PolicyActivity> activity.</span></span> <span data-ttu-id="c1c9b-105">ワークフローは、製品割引ワークフローを定義するために使用するフィールド `orderValue`、`customerType`、および `discount` を定義します。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-105">The workflow defines `orderValue`, `customerType`, and `discount` fields that are used to define a product discount workflow.</span></span> <span data-ttu-id="c1c9b-106">ルール ファイルに定義済みのルールは、`orderValue` と `customerType` に基づいて、割引金額を設定します。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-106">The rules defined in the rules file set a discount value that is based on the `orderValue` and `customerType`.</span></span> <span data-ttu-id="c1c9b-107">`orderValue` と `customerType` が `SimplePolicyWorkflow` クラス定義で設定されています。これを変更すると、動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-107">The `orderValue` and `customerType` are set in the `SimplePolicyWorkflow` class definition and can be changed to alter the behavior.</span></span> <span data-ttu-id="c1c9b-108">結果として得られた割引率は、<xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> クラスに定義されているイベント ハンドラ `SimplePolicyWorkflow` でコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-108">The resulting discount is written to the console in the <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> event handler that is defined in the `SimplePolicyWorkflow` class.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="c1c9b-109">サンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="c1c9b-109">To build the sample</span></span>  
  
1.  <span data-ttu-id="c1c9b-110">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-110">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c1c9b-111">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-111">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c1c9b-112">Ctrl キーを押しながら F5 キーを押して、ソリューションをデバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-112">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="c1c9b-113">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="c1c9b-113">To run the sample</span></span>  
  
-   <span data-ttu-id="c1c9b-114">[SDK コマンド プロンプト] ウィンドウで、SimplePolicy\bin\debug フォルダー (Visual Basic バージョンのサンプルの場合は SimplePolicy\bin フォルダー) にある .exe ファイルを実行します。このフォルダーは、サンプルのメイン フォルダーの下に作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-114">In the SDK Command Prompt window, run the .exe file in the SimplePolicy\bin\debug folder (or the SimplePolicy\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c1c9b-115">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c1c9b-116">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-116">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c1c9b-117">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c1c9b-118">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c1c9b-118">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a><span data-ttu-id="c1c9b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1c9b-119">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="c1c9b-120">高度なポリシー</span><span class="sxs-lookup"><span data-stu-id="c1c9b-120">Advanced Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
