---
title: "制約の種類"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd73776aebb571fad732f554d6a96c1611506e8c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="constraint-types"></a><span data-ttu-id="83a02-102">制約の種類</span><span class="sxs-lookup"><span data-stu-id="83a02-102">Constraint Types</span></span>
<span data-ttu-id="83a02-103">このサンプルでは、ワークフローに制約を適用する 2 種類の方法を示します。1 つはアクティビティの内部 (ビルド) から適用する方法で、もう 1 つはアクティビティの外部 (ポリシー) から適用する方法です。</span><span class="sxs-lookup"><span data-stu-id="83a02-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="83a02-104">このシナリオでは、(サードパーティのソフトウェア会社の) アクティビティ作成者が 2 つの引数間のリレーションシップを検証します。</span><span class="sxs-lookup"><span data-stu-id="83a02-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="83a02-105">ここでは、コストが価格以下になるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a02-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="83a02-106">これは、一般的な検証ビルド制約です。</span><span class="sxs-lookup"><span data-stu-id="83a02-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="83a02-107">次に、ショップ オーナーがこの一般的なアクティビティに検証を追加します。</span><span class="sxs-lookup"><span data-stu-id="83a02-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="83a02-108">ここでは、製品のほとんどを $9.99 以下にします。</span><span class="sxs-lookup"><span data-stu-id="83a02-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="83a02-109">したがって、`CreateProduct` アクティビティに基づくポリシー制約を使用します。</span><span class="sxs-lookup"><span data-stu-id="83a02-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="83a02-110">このサンプルでは、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="83a02-110">In the sample:</span></span>  
  
 <span data-ttu-id="83a02-111">アクティビティ作成者 (ビルド) は、次を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a02-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="83a02-112">制約 (`PriceGreaterThanCost`) を作成します。</span><span class="sxs-lookup"><span data-stu-id="83a02-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="83a02-113">ここには、すべての検証ロジックが存在します。</span><span class="sxs-lookup"><span data-stu-id="83a02-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="83a02-114">`System.Activities.CodeActivity.OnGetConstraints()` をオーバーライドし、制約 (`PriceGreaterThanCost`) を制約 <xref:System.Collections.IList> に追加します。</span><span class="sxs-lookup"><span data-stu-id="83a02-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="83a02-115">ワークフロー作成者 (ポリシー) は、次を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a02-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="83a02-116">検証するアクティビティのインスタンスを含むワークフローを作成します (`CreateProduct`)。</span><span class="sxs-lookup"><span data-stu-id="83a02-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="83a02-117">制約 (`MaxPrice`) を作成します。</span><span class="sxs-lookup"><span data-stu-id="83a02-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="83a02-118"><xref:System.Activities.Validation.ValidationSettings> インスタンス (`validationSettings`) を作成し、制約 (`MaxPrice`) をコレクション `AdditionalConstraints` に追加します。</span><span class="sxs-lookup"><span data-stu-id="83a02-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="83a02-119">ここで、ワークフロー作成者は、シーケンスや並列などのアクティビティにポリシー制約を追加できます。</span><span class="sxs-lookup"><span data-stu-id="83a02-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="83a02-120"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> を呼び出すと、<xref:System.Activities.Validation.ValidationResults> オブジェクトの <xref:System.Activities.Validation.ValidationError> コレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="83a02-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="83a02-121">(省略可能) <xref:System.Activities.Validation.ValidationError> オブジェクトを出力します。</span><span class="sxs-lookup"><span data-stu-id="83a02-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="83a02-122">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="83a02-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="83a02-123">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ConstraintTypes.sln サンプル ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="83a02-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="83a02-124">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="83a02-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83a02-125">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="83a02-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83a02-126">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="83a02-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="83a02-127">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="83a02-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83a02-128">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="83a02-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`