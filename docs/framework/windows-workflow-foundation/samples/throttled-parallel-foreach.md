---
title: "制限された並列 ForEach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b8811327fee8eb2ca3b2ba87d54a0014b20673a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="16871-102">制限された並列 ForEach</span><span class="sxs-lookup"><span data-stu-id="16871-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="16871-103">`ThrottleParallelForEach`アクティビティがに似ていますが、 <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach`例外の 1 つのアクティビティが設定できるは同時実行要因を実行する同時分岐の数を制限します。</span><span class="sxs-lookup"><span data-stu-id="16871-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="16871-104">`ThrottleParallelForEach` アクティビティは、<xref:System.Activities.NativeActivity> クラスを介してのみアクセスできる他のアクティビティ (子アクティビティ) をスケジュールする必要があるため、<xref:System.Activities.NativeActivityContext> クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="16871-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
## <a name="projects"></a><span data-ttu-id="16871-105">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="16871-105">Projects</span></span>  
  
|<span data-ttu-id="16871-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="16871-106">**ProjectName**</span></span>|<span data-ttu-id="16871-107">**説明**</span><span class="sxs-lookup"><span data-stu-id="16871-107">**Description**</span></span>|<span data-ttu-id="16871-108">**メイン ファイルします。**</span><span class="sxs-lookup"><span data-stu-id="16871-108">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="16871-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="16871-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="16871-110">`ThrottledParallelForEach` アクティビティとそのデザイナーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="16871-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="16871-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="16871-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="16871-112">`ThrottledParallelForEach` アクティビティ定義。</span><span class="sxs-lookup"><span data-stu-id="16871-112">The `ThrottledParallelForEach` activity definition.</span></span>|  
|<span data-ttu-id="16871-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="16871-113">CodeTestClient</span></span>|<span data-ttu-id="16871-114">命令型コードを使用して、`ThrottledParallelForEach` を含むワークフローを構成および実行するサンプル クライアント アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="16871-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="16871-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="16871-115">Program.cs</span></span><br /><br /> <span data-ttu-id="16871-116">サンプル ワークフローのインスタンスを定義および実行します。</span><span class="sxs-lookup"><span data-stu-id="16871-116">Defines and runs an instance of the sample workflow.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="16871-117">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="16871-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="16871-118">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ThrottledParallelForEach.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="16871-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ThrottledParallelForEach.sln file.</span></span>  
  
2.  <span data-ttu-id="16871-119">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="16871-119">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="16871-120">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="16871-120">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16871-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="16871-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="16871-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="16871-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="16871-123">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="16871-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="16871-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="16871-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`