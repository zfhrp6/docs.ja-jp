---
title: "アクティビティの関係の検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d527b728d0b4ac86a8dd98afb45a09585bd0c96
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="231c7-102">アクティビティの関係の検証</span><span class="sxs-lookup"><span data-stu-id="231c7-102">Activity Relationships Validation</span></span>
<span data-ttu-id="231c7-103">このサンプルには 3 つのアクティビティ `CreateCity`、`CreateState`、および `CreateCountry` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="231c7-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="231c7-104">`CreateCity` は `CreateState` アクティビティ内にあり、`CreateState` は `CreateCountry` アクティビティ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="231c7-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="231c7-105">このサンプルの目的から、検証ロジックは、`CreateState` アクティビティについてはコードで記述され、`CreateCity` アクティビティについては XAML で記述されます。</span><span class="sxs-lookup"><span data-stu-id="231c7-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="231c7-106">制約の動作は両方とも同じです。</span><span class="sxs-lookup"><span data-stu-id="231c7-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="231c7-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] には、アクティビティ間の関係を検証するために使用できる次の 3 つのヘルパー アクティビティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="231c7-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="231c7-108">現在のノードの親に属しているすべてのアクティビティのコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="231c7-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="231c7-109">現在のノードのサブツリーに属しているすべてのアクティビティのコレクションを提供します (現在のノードを除く)。</span><span class="sxs-lookup"><span data-stu-id="231c7-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="231c7-110">現在のノードと同じツリーにあるすべてのアクティビティのコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="231c7-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="231c7-111">このサンプルでは、<xref:System.Activities.Statements.ForEach%601> アクティビティを使用して、<xref:System.Activities.Validation.GetParentChain> から返されたコレクション内のすべての要素を処理します。</span><span class="sxs-lookup"><span data-stu-id="231c7-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="231c7-112">コレクション内の要素ごとに、その型が `CreateCountry` (`CreateState` を検証する場合は `CreateCity`) と比較され、一致が見つかると、結果フラグが `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="231c7-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="231c7-113">最後に、結果フラグが <xref:System.Activities.Validation.AssertValidation> に設定される場合は、`false` を使用して検証エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="231c7-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="231c7-114">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="231c7-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="231c7-115">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ContainmentValidation.sln サンプル ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="231c7-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="231c7-116">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="231c7-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="231c7-117">Ctrl キーを押しながら F5 キーを押して、プログラムを起動します。</span><span class="sxs-lookup"><span data-stu-id="231c7-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="231c7-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="231c7-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="231c7-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="231c7-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="231c7-120">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="231c7-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="231c7-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="231c7-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
