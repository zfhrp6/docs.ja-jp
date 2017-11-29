---
title: "基本検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d388b3d6acad28e4ff952f72aa64a607d745f307
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="basic-validation"></a><span data-ttu-id="b3a91-102">基本検証</span><span class="sxs-lookup"><span data-stu-id="b3a91-102">Basic Validation</span></span>
<span data-ttu-id="b3a91-103">このサンプルは、`CreateProduct` アクティビティで構成されています。このアクティビティでは、その `Cost` 引数が `Price` 引数以下であることを検証します。</span><span class="sxs-lookup"><span data-stu-id="b3a91-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="b3a91-104">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="b3a91-104">Sample Details</span></span>  
 <span data-ttu-id="b3a91-105">検証を使用する 2 人の作成者が存在します。1 人はアクティビティの検証ロジックを作成するアクティビティ作成者で、もう 1 人は、特定のワークフローで検証サービスを呼び出すワークフロー作成者です。</span><span class="sxs-lookup"><span data-stu-id="b3a91-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="b3a91-106">このシナリオでは、アクティビティ作成者はアクティビティのすべてのインスタンスで、コストが必ず価格以下になるように強制します。</span><span class="sxs-lookup"><span data-stu-id="b3a91-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="b3a91-107">アクティビティ作成者 (アクティビティ内) は、次を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3a91-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="b3a91-108">制約 (`PriceGreaterThanCost`) を作成します。</span><span class="sxs-lookup"><span data-stu-id="b3a91-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="b3a91-109">ここには、すべての検証ロジックが存在します。</span><span class="sxs-lookup"><span data-stu-id="b3a91-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="b3a91-110">`System.Activities.CodeActivity.OnGetConstraints()` をオーバーライドし、制約 (`PriceGreaterThanCost`) を制約 <xref:System.Collections.IList> に追加します。</span><span class="sxs-lookup"><span data-stu-id="b3a91-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="b3a91-111">ワークフロー作成者 (メイン プログラム) は次を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3a91-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="b3a91-112">検証するアクティビティのインスタンスを含むワークフローを作成します (`CreateProduct`)。</span><span class="sxs-lookup"><span data-stu-id="b3a91-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="b3a91-113"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> を呼び出すと、<xref:System.Activities.Validation.ValidationResults> の <xref:System.Activities.Validation.ValidationError> コレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="b3a91-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="b3a91-114">(省略可能) <xref:System.Activities.Validation.ValidationError> オブジェクトを出力します。</span><span class="sxs-lookup"><span data-stu-id="b3a91-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b3a91-115">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b3a91-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b3a91-116">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で BasicValidation.sln サンプル ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="b3a91-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b3a91-117">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="b3a91-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3a91-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3a91-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b3a91-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b3a91-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b3a91-120">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="b3a91-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3a91-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b3a91-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`  
  
## <a name="see-also"></a><span data-ttu-id="b3a91-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3a91-122">See Also</span></span>
