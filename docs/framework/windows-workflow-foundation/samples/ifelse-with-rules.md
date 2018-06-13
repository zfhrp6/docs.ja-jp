---
title: ルール付き IfElse
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 179ec29f957894433fb527a14048460f5ff6ee5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515122"
---
# <a name="ifelse-with-rules"></a><span data-ttu-id="04ed0-102">ルール付き IfElse</span><span class="sxs-lookup"><span data-stu-id="04ed0-102">IfElse With Rules</span></span>
<span data-ttu-id="04ed0-103">このサンプルでは、ルール条件を <xref:System.Workflow.Activities.IfElseActivity> アクティビティで使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="04ed0-103">This sample shows the use of a rule condition with an <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span>  
  
 <span data-ttu-id="04ed0-104">このサンプルでは、ホストから `OrderValue` パラメータが渡されます。</span><span class="sxs-lookup"><span data-stu-id="04ed0-104">The sample passes in an `OrderValue` parameter from the host.</span></span> <span data-ttu-id="04ed0-105">このパラメータの値は、<xref:System.Workflow.Activities.IfElseActivity> アクティビティの最初の分岐のルール条件で使用されます。</span><span class="sxs-lookup"><span data-stu-id="04ed0-105">The value of the parameter is used in a rule condition on the first branch of the <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span> <span data-ttu-id="04ed0-106">場合、値が 10,000 未満の場合、最初の分岐が実行され、<xref:System.Workflow.Activities.CodeActivity>最初の分岐のアクティビティの出力**マネージャーの承認を取得**コンソールにします。</span><span class="sxs-lookup"><span data-stu-id="04ed0-106">If the value is less than 10,000, the first branch executes, and the <xref:System.Workflow.Activities.CodeActivity> activity in the first branch prints **Get Manager Approval** to the console.</span></span> <span data-ttu-id="04ed0-107">値が 10,000 を超える場合、 <xref:System.Workflow.Activities.CodeActivity> 2 番目の分岐のアクティビティが実行され、印刷**取得 VP 承認**です。</span><span class="sxs-lookup"><span data-stu-id="04ed0-107">If the value is greater than 10,000, the <xref:System.Workflow.Activities.CodeActivity> activity in the second branch executes and prints **Get VP Approval**.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="04ed0-108">サンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="04ed0-108">To build the sample</span></span>  
  
1.  <span data-ttu-id="04ed0-109">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="04ed0-109">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="04ed0-110">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="04ed0-110">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="04ed0-111">Ctrl キーを押しながら F5 キーを押して、ソリューションをデバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="04ed0-111">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="04ed0-112">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="04ed0-112">To run the sample</span></span>  
  
-   <span data-ttu-id="04ed0-113">[SDK コマンド プロンプト] ウィンドウで、IfElseWithRules\bin\debug フォルダー (Visual Basic バージョンのサンプルの場合は IfElseWithRules\bin フォルダー) にある .exe ファイルを実行します。このフォルダーは、サンプルのメイン フォルダーの下に作成されます。</span><span class="sxs-lookup"><span data-stu-id="04ed0-113">In the SDK Command Prompt window, run the .exe file in the IfElseWithRules\bin\debug folder (or the IfElseWithRules\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="04ed0-114">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="04ed0-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="04ed0-115">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="04ed0-115">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="04ed0-116">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="04ed0-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04ed0-117">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="04ed0-117">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a><span data-ttu-id="04ed0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="04ed0-118">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
