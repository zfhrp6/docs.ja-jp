---
title: "For アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e77800b21d671a0de0cab6f442919f50ce5ca51b
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="for-activity"></a><span data-ttu-id="53c78-102">For アクティビティ</span><span class="sxs-lookup"><span data-stu-id="53c78-102">For Activity</span></span>
<span data-ttu-id="53c78-103">For サンプルでは、<xref:System.Activities.NativeActivity> から継承するカスタム アクティビティを構築し、そのアクティビティをワークフローで使用して実際の例を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="53c78-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="53c78-104">このサンプルに含まれるカスタム アクティビティは、C# の `for` ステートメントと同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="53c78-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="53c78-105">T</span><span class="sxs-lookup"><span data-stu-id="53c78-105">T</span></span>  
  
 <span data-ttu-id="53c78-106">`For` カスタム アクティビティには、`InitAction`、`IterationAction`、`Condition`、および `Body` というプロパティがあります。これらのプロパティは、標準的な C# の `For` ステートメントの初期化ステートメント、反復ステートメント、継続条件、および本体ステートメントにそれぞれ対応します。</span><span class="sxs-lookup"><span data-stu-id="53c78-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="53c78-107">次の表で、サンプルの主要なファイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="53c78-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="53c78-108">ファイル</span><span class="sxs-lookup"><span data-stu-id="53c78-108">File</span></span>|<span data-ttu-id="53c78-109">説明</span><span class="sxs-lookup"><span data-stu-id="53c78-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="53c78-110">For.cs</span><span class="sxs-lookup"><span data-stu-id="53c78-110">For.cs</span></span>|<span data-ttu-id="53c78-111">`For` カスタム アクティビティのクラス定義。<xref:System.Activities.NativeActivity> クラスを拡張して C# の `For` ステートメントの機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="53c78-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="53c78-112">Program.cs</span><span class="sxs-lookup"><span data-stu-id="53c78-112">Program.cs</span></span>|<span data-ttu-id="53c78-113">カスタム `For` アクティビティを使用してコレクションに対して基本的な反復処理を実行するクライアント アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="53c78-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="53c78-114">`For` カスタム アクティビティを使用する場合は、必ず `Condition` プロパティを設定してください。そうしないと、無限ループが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="53c78-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="53c78-115">使用例</span><span class="sxs-lookup"><span data-stu-id="53c78-115">Demonstrates</span></span>  
 <span data-ttu-id="53c78-116"><xref:System.Activities.NativeActivity> から継承するカスタム アクティビティを作成します。</span><span class="sxs-lookup"><span data-stu-id="53c78-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="53c78-117">説明</span><span class="sxs-lookup"><span data-stu-id="53c78-117">Discussion</span></span>  
 <span data-ttu-id="53c78-118">次の表で、このサンプルに含まれるアクティビティのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="53c78-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="53c78-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="53c78-119">InitAction</span></span>  
 <span data-ttu-id="53c78-120">初期化ステートメント</span><span class="sxs-lookup"><span data-stu-id="53c78-120">Initialization statement</span></span>  
  
 <span data-ttu-id="53c78-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="53c78-121">IterationAction</span></span>  
 <span data-ttu-id="53c78-122">反復ステートメント</span><span class="sxs-lookup"><span data-stu-id="53c78-122">Iterative statement</span></span>  
  
 <span data-ttu-id="53c78-123">状態</span><span class="sxs-lookup"><span data-stu-id="53c78-123">Condition</span></span>  
 <span data-ttu-id="53c78-124">条件ステートメント</span><span class="sxs-lookup"><span data-stu-id="53c78-124">Continuation statement</span></span>  
  
 <span data-ttu-id="53c78-125">Body</span><span class="sxs-lookup"><span data-stu-id="53c78-125">Body</span></span>  
 <span data-ttu-id="53c78-126">本体ステートメント</span><span class="sxs-lookup"><span data-stu-id="53c78-126">Body statement</span></span>  
  
 <span data-ttu-id="53c78-127">このアクティビティは、<xref:System.Activities.NativeActivity> から継承して、ランタイム機能 (`ScheduleActivity` のいずれかの <xref:System.Activities.NativeActivityContext> メソッドを使用した追加アクティビティの実行スケジュールの設定など) へのアクセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="53c78-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="53c78-128">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="53c78-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="53c78-129">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、For.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="53c78-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="53c78-130">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="53c78-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="53c78-131">F5 キーを押して、ソリューションを実行します。</span><span class="sxs-lookup"><span data-stu-id="53c78-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="53c78-132">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="53c78-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="53c78-133">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="53c78-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="53c78-134">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="53c78-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="53c78-135">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="53c78-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`