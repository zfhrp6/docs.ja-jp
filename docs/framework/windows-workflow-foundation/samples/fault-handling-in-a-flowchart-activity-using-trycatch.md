---
title: "TryCatch を使用した Flowchart アクティビティでのエラー処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a179ae5aaca959383a88105b96cbba2cebd1919
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="918dc-102">TryCatch を使用した Flowchart アクティビティでのエラー処理</span><span class="sxs-lookup"><span data-stu-id="918dc-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="918dc-103">このサンプルでは、複雑な制御フロー アクティビティ内で <xref:System.Activities.Statements.TryCatch> アクティビティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="918dc-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>  
  
 <span data-ttu-id="918dc-104">このサンプルでは、販売促進コードに対応する式に基づいて割引率を計算する <xref:System.Activities.Statements.Flowchart> アクティビティに、販売促進コードと子供の数が変数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="918dc-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="918dc-105">このサンプルには、命令型コードとワークフロー デザイナー バージョンのサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="918dc-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>  
  
 <span data-ttu-id="918dc-106">次の表で、`CreateFlowchartWithFaults` アクティビティの変数の詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="918dc-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>  
  
|<span data-ttu-id="918dc-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="918dc-107">Parameters</span></span>|<span data-ttu-id="918dc-108">説明</span><span class="sxs-lookup"><span data-stu-id="918dc-108">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="918dc-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="918dc-109">promoCode</span></span>|<span data-ttu-id="918dc-110">販売促進コード。</span><span class="sxs-lookup"><span data-stu-id="918dc-110">The promotion code.</span></span> <span data-ttu-id="918dc-111">型: String</span><span class="sxs-lookup"><span data-stu-id="918dc-111">Type: String</span></span><br /><br /> <span data-ttu-id="918dc-112">使用できる値は次のとおりです (かっこ内は値の説明)。</span><span class="sxs-lookup"><span data-stu-id="918dc-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="918dc-113">単一 (単一)</span><span class="sxs-lookup"><span data-stu-id="918dc-113">-   Single (Single)</span></span><br /><span data-ttu-id="918dc-114">MNK (子供のいないで既婚。)</span><span class="sxs-lookup"><span data-stu-id="918dc-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="918dc-115">MWK (子供の既婚。)</span><span class="sxs-lookup"><span data-stu-id="918dc-115">-   MWK (Married with kids.)</span></span>|  
|<span data-ttu-id="918dc-116">numKids</span><span class="sxs-lookup"><span data-stu-id="918dc-116">numKids</span></span>|<span data-ttu-id="918dc-117">子供の数。</span><span class="sxs-lookup"><span data-stu-id="918dc-117">The number of children.</span></span> <span data-ttu-id="918dc-118">型: int</span><span class="sxs-lookup"><span data-stu-id="918dc-118">Type: int</span></span>|  
  
 <span data-ttu-id="918dc-119">`CreateFlowchartWithFaults` アクティビティでは、<xref:System.Activities.Statements.FlowSwitch%601> 引数を有効にする `promoCode` アクティビティを使用し、次の式を使って割引率を計算します。</span><span class="sxs-lookup"><span data-stu-id="918dc-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>  
  
|<span data-ttu-id="918dc-120">`promoCode` の値</span><span class="sxs-lookup"><span data-stu-id="918dc-120">Value of `promoCode`</span></span>|<span data-ttu-id="918dc-121">割引率 (%)</span><span class="sxs-lookup"><span data-stu-id="918dc-121">Discount (%)</span></span>|  
|--------------------------|--------------------|  
|<span data-ttu-id="918dc-122">Single</span><span class="sxs-lookup"><span data-stu-id="918dc-122">Single</span></span>|<span data-ttu-id="918dc-123">10</span><span class="sxs-lookup"><span data-stu-id="918dc-123">10</span></span>|  
|<span data-ttu-id="918dc-124">MNK</span><span class="sxs-lookup"><span data-stu-id="918dc-124">MNK</span></span>|<span data-ttu-id="918dc-125">16</span><span class="sxs-lookup"><span data-stu-id="918dc-125">15</span></span>|  
|<span data-ttu-id="918dc-126">MWK</span><span class="sxs-lookup"><span data-stu-id="918dc-126">MWK</span></span>|<span data-ttu-id="918dc-127">15 + (1 – 1/`numberOfKids`)\*10**注:**可能性のある、この計算がスローすることが、<xref:System.DivideByZeroException>です。</span><span class="sxs-lookup"><span data-stu-id="918dc-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="918dc-128">そのため、割引率の計算は、<xref:System.Activities.Statements.TryCatch> 例外をキャッチして割引率をゼロに設定する <xref:System.DivideByZeroException> アクティビティでラップされます。</span><span class="sxs-lookup"><span data-stu-id="918dc-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="918dc-129">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="918dc-129">To use this sample</span></span>  
  
1.  <span data-ttu-id="918dc-130">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、FlowchartWithFaultHandling.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="918dc-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the FlowchartWithFaultHandling.sln solution file.</span></span>  
  
2.  <span data-ttu-id="918dc-131">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="918dc-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="918dc-132">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="918dc-132">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="918dc-133">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="918dc-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="918dc-134">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="918dc-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="918dc-135">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="918dc-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="918dc-136">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="918dc-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="918dc-137">参照</span><span class="sxs-lookup"><span data-stu-id="918dc-137">See Also</span></span>  
 [<span data-ttu-id="918dc-138">Flowchart のワークフロー</span><span class="sxs-lookup"><span data-stu-id="918dc-138">Flowchart Workflows</span></span>](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [<span data-ttu-id="918dc-139">例外</span><span class="sxs-lookup"><span data-stu-id="918dc-139">Exceptions</span></span>](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
