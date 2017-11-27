---
title: "高度なポリシー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3dd941509c37618480a20530d3f5239750917e98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="advanced-policy"></a><span data-ttu-id="7c1e6-102">高度なポリシー</span><span class="sxs-lookup"><span data-stu-id="7c1e6-102">Advanced Policy</span></span>
<span data-ttu-id="7c1e6-103">このサンプルは、単純なポリシーのサンプルを拡張するものです。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="7c1e6-104">単純なポリシーのサンプルに含まれる個人向け割引ルールとビジネス割引ルールの他に、新しいルールがいくつか追加されています。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="7c1e6-105">高額な注文に対する割引額を大きく設定する、高額ルールが追加されています。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="7c1e6-106">このルールの優先順位の値は前の 2 つのルールより小さいので、割引フィールドを上書きし、個人向けおよびビジネス向けの割引ルールより優先されます。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="7c1e6-107">割引レベルに基づいて合計額を計算する、合計の計算ルールも追加されています。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="7c1e6-108">ワークフロー アクティビティに定義されたメソッドの参照方法と、他のアクションの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="7c1e6-109">また、このルールは、割引フィールドが変更されるたびに評価されるため、チェーン動作についても示します。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="7c1e6-110">さらに、メソッドに対する属性の適用についても、CalculateTotal メソッドに RuleWriteAttribute 属性を適用する例で示します。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="7c1e6-111">これにより、メソッドが実行されるたびに、影響を受けるルール (ErrorTotalRule) が再評価されます。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="7c1e6-112">追加されている最後のルールは、エラーを検出します (ここでは、合計が 0 未満)。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="7c1e6-113">エラーが検出されると、ポリシーの実行は停止されます。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="7c1e6-114">最後に、`Console.Writeline` 呼び出しがアクションとして各ルールに追加されています。これは、ルール実行についての詳細を表示できるようにするためで、また、参照型の静的メソッドにアクセスできることも示します。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="7c1e6-115">追跡を使用して、実行されるルールの詳細を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="7c1e6-116">このサンプルで使用されているルールを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="7c1e6-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="7c1e6-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="7c1e6-118">IF OrderValue > 500 AND CustomerType = Residential</span><span class="sxs-lookup"><span data-stu-id="7c1e6-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="7c1e6-119">THEN Discount = 5%</span><span class="sxs-lookup"><span data-stu-id="7c1e6-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="7c1e6-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="7c1e6-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="7c1e6-121">IF OrderValue > 10000 AND CustomerType = Business</span><span class="sxs-lookup"><span data-stu-id="7c1e6-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="7c1e6-122">THEN Discount = 10%</span><span class="sxs-lookup"><span data-stu-id="7c1e6-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="7c1e6-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="7c1e6-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="7c1e6-124">IF OrderValue > 20000</span><span class="sxs-lookup"><span data-stu-id="7c1e6-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="7c1e6-125">THEN Discount = 15%</span><span class="sxs-lookup"><span data-stu-id="7c1e6-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="7c1e6-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="7c1e6-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="7c1e6-127">IF Discount > 0</span><span class="sxs-lookup"><span data-stu-id="7c1e6-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="7c1e6-128">THEN CalculateTotal(OrderValue, Discount)</span><span class="sxs-lookup"><span data-stu-id="7c1e6-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="7c1e6-129">ELSE Total = OrderValue</span><span class="sxs-lookup"><span data-stu-id="7c1e6-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="7c1e6-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="7c1e6-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="7c1e6-131">場合は合計\<0</span><span class="sxs-lookup"><span data-stu-id="7c1e6-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="7c1e6-132">THEN Error = "Fired ErrorTotalRule"; Halt</span><span class="sxs-lookup"><span data-stu-id="7c1e6-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="7c1e6-133">ルールの評価と実行は、トレースと追跡で確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="7c1e6-134">サンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="7c1e6-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="7c1e6-135">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="7c1e6-136">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7c1e6-137">Ctrl キーを押しながら F5 キーを押して、ソリューションをデバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="7c1e6-138">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="7c1e6-138">To run the sample</span></span>  
  
-   <span data-ttu-id="7c1e6-139">[SDK コマンド プロンプト] ウィンドウで、AdvancedPolicy\bin\debug フォルダー (Visual Basic バージョンのサンプルの場合は AdvancedPolicy\bin フォルダー) にある .exe ファイルを実行します。このフォルダーは、サンプルのメイン フォルダーの下に作成されます。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c1e6-140">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7c1e6-141">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7c1e6-142">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c1e6-143">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7c1e6-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="7c1e6-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c1e6-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="7c1e6-145">単純なポリシー</span><span class="sxs-lookup"><span data-stu-id="7c1e6-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
