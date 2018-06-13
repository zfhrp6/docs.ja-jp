---
title: 簡単なポリシー
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: dff3979d75fdeb5a45be3940af3568c26f5e8f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515897"
---
# <a name="simple-policy"></a><span data-ttu-id="26080-102">簡単なポリシー</span><span class="sxs-lookup"><span data-stu-id="26080-102">Simple Policy</span></span>
<span data-ttu-id="26080-103">このサンプルでは、ワークフロー内で <xref:System.Workflow.Activities.PolicyActivity> アクティビティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="26080-103">This sample shows how to use a <xref:System.Workflow.Activities.PolicyActivity> activity in a workflow.</span></span>  
  
 <span data-ttu-id="26080-104">このサンプルのシーケンシャル ワークフローは、<xref:System.Workflow.Activities.PolicyActivity> アクティビティを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="26080-104">The sequential workflow in this sample is created by using a <xref:System.Workflow.Activities.PolicyActivity> activity.</span></span> <span data-ttu-id="26080-105">ワークフローは、製品割引ワークフローを定義するために使用するフィールド `orderValue`、`customerType`、および `discount` を定義します。</span><span class="sxs-lookup"><span data-stu-id="26080-105">The workflow defines `orderValue`, `customerType`, and `discount` fields that are used to define a product discount workflow.</span></span> <span data-ttu-id="26080-106">ルール ファイルに定義済みのルールは、`orderValue` と `customerType` に基づいて、割引金額を設定します。</span><span class="sxs-lookup"><span data-stu-id="26080-106">The rules defined in the rules file set a discount value that is based on the `orderValue` and `customerType`.</span></span> <span data-ttu-id="26080-107">`orderValue` と `customerType` が `SimplePolicyWorkflow` クラス定義で設定されています。これを変更すると、動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="26080-107">The `orderValue` and `customerType` are set in the `SimplePolicyWorkflow` class definition and can be changed to alter the behavior.</span></span> <span data-ttu-id="26080-108">結果として得られた割引率は、<xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> クラスに定義されているイベント ハンドラ `SimplePolicyWorkflow` でコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="26080-108">The resulting discount is written to the console in the <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> event handler that is defined in the `SimplePolicyWorkflow` class.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="26080-109">サンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="26080-109">To build the sample</span></span>  
  
1.  <span data-ttu-id="26080-110">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="26080-110">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="26080-111">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="26080-111">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="26080-112">Ctrl キーを押しながら F5 キーを押して、ソリューションをデバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="26080-112">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="26080-113">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="26080-113">To run the sample</span></span>  
  
-   <span data-ttu-id="26080-114">[SDK コマンド プロンプト] ウィンドウで、SimplePolicy\bin\debug フォルダー (Visual Basic バージョンのサンプルの場合は SimplePolicy\bin フォルダー) にある .exe ファイルを実行します。このフォルダーは、サンプルのメイン フォルダーの下に作成されます。</span><span class="sxs-lookup"><span data-stu-id="26080-114">In the SDK Command Prompt window, run the .exe file in the SimplePolicy\bin\debug folder (or the SimplePolicy\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="26080-115">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="26080-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="26080-116">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="26080-116">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="26080-117">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="26080-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="26080-118">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="26080-118">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a><span data-ttu-id="26080-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="26080-119">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="26080-120">高度なポリシー</span><span class="sxs-lookup"><span data-stu-id="26080-120">Advanced Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
