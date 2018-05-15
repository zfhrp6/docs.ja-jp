---
title: .NET Framework 3.5 ルールセットでの変数の使用
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 9fa6eaf58aaddc4673f08ec9a9001647a494877d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a><span data-ttu-id="c5d2e-102">.NET Framework 3.5 ルールセットでの変数の使用</span><span class="sxs-lookup"><span data-stu-id="c5d2e-102">Using Variables with a .NET Framework 3.5 Ruleset</span></span>
<span data-ttu-id="c5d2e-103">このサンプルでは、<xref:System.Activities.Statements.Interop> アクティビティを使用するワークフローを作成し、ポリシーとルールを使用する、[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] で記述されたカスタム アクティビティを統合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-103">This sample demonstrates how to create a workflow that uses the <xref:System.Activities.Statements.Interop> activity to integrate a custom activity written in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] that uses policy and rules.</span></span> <span data-ttu-id="c5d2e-104">このワークフローでは、カスタム アクティビティで公開されている依存プロパティに変数をバインドすることで、カスタム アクティビティにデータを渡します。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-104">The workflow passes data to the custom activity by binding variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="sample-walkthrough"></a><span data-ttu-id="c5d2e-105">サンプルのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="c5d2e-105">Sample walkthrough</span></span>  
  
#### <a name="to-examine-travelrulelibrary"></a><span data-ttu-id="c5d2e-106">TravelRuleLibrary を検証するには</span><span class="sxs-lookup"><span data-stu-id="c5d2e-106">To examine TravelRuleLibrary</span></span>  
  
1.  <span data-ttu-id="c5d2e-107">Visual Studio を使用して、InteropWith35RuleSet.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-107">Using Visual Studio, open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="c5d2e-108">ワークフロー デザイナーで TravelRuleSet.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-108">Open the TravelRuleSet.cs in the workflow designer.</span></span>  
  
     <span data-ttu-id="c5d2e-109"><xref:System.Workflow.Activities.PolicyActivity> を含むカスタム シーケンシャル アクティビティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-109">A custom sequential activity that contains a <xref:System.Workflow.Activities.PolicyActivity> is displayed.</span></span>  
  
3.  <span data-ttu-id="c5d2e-110">ルールを検証するには、DiscountPolicy ポリシー アクティビティをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-110">Double-click the DiscountPolicy policy activity to examine the rules.</span></span>  
  
     <span data-ttu-id="c5d2e-111">ルール エディターがポップアップで開き、ルールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-111">The Rules editor pops up to show the rules.</span></span>  
  
4.  <span data-ttu-id="c5d2e-112">右クリックして、`DiscountPolicy`を選択し、**コードの表示**アクティビティの c# コードの横にあるコードをチェックするオプションです。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-112">Right click the `DiscountPolicy` and select the **View Code** option to examine the code beside C# code for the activity.</span></span>  
  
     <span data-ttu-id="c5d2e-113">`DiscountLevel` の依存関係プロパティの設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-113">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="c5d2e-114">これは [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] の引数と同じです。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-114">This is equivalent to arguments in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="c5d2e-115">引数の詳細については、次を参照してください。[変数と引数](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md)です。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-115">For more information about arguments, see [Variables and Arguments](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span></span>  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="c5d2e-116">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="c5d2e-116">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="c5d2e-117">これは、<xref:System.Activities.Statements.Interop> アクティビティを使用して、`TravelRuleLibrary` プロジェクトで作成されたカスタム ルール セットと統合するシーケンシャル ワークフロー プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-117">This is a sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom Rule set created in the `TravelRuleLibrary` project.</span></span> <span data-ttu-id="c5d2e-118">変数は、最上位レベルの <xref:System.Activities.Statements.Sequence> アクティビティで作成されます。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-118">Variables are created on the top level <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="c5d2e-119"><xref:System.Activities.Statements.Interop> アクティビティは、`TravelRuleSet` アクティビティと統合するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-119">The <xref:System.Activities.Statements.Interop> activity is used to integrate with the `TravelRuleSet` activity.</span></span> <span data-ttu-id="c5d2e-120"><xref:System.Activities.Statements.Sequence> で宣言された変数は、依存プロパティにバインドするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-120">The variables that are declared on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="c5d2e-121">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="c5d2e-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="c5d2e-122">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、InteropWith35RuleSet.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="c5d2e-123">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c5d2e-124">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5d2e-125">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c5d2e-126">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c5d2e-127">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5d2e-128">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5d2e-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`