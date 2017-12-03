---
title: "入力アクティビティの待機"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d877c147a19635782b652d96031644b3be42448a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wait-for-input-activity"></a><span data-ttu-id="38d02-102">入力アクティビティの待機</span><span class="sxs-lookup"><span data-stu-id="38d02-102">Wait For Input Activity</span></span>
<span data-ttu-id="38d02-103">このサンプルでは、ワークフローに名前付きブックマークを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="38d02-103">This sample demonstrates how to create named bookmarks in a workflow.</span></span> [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="38d02-104"> には、宣言型ブックマークを作成するアクティビティは用意されていません。</span><span class="sxs-lookup"><span data-stu-id="38d02-104"> does not provide an activity for declarative bookmark creation.</span></span> <span data-ttu-id="38d02-105">そのため、ワークフローにブックマークを作成する場合は、ブックマークを作成するカスタム アクティビティを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38d02-105">Therefore, when you want to create a bookmark in your workflow, you must write a custom activity that creates it.</span></span> <span data-ttu-id="38d02-106">このサンプルで定義される `WaitForInput` アクティビティはこの機能を提供します。そのため、ユーザーはワークフロー内で宣言によってブックマークを作成できます。</span><span class="sxs-lookup"><span data-stu-id="38d02-106">The `WaitForInput` activity defined in this sample provides this functionality, so that users can create bookmarks declaratively within a workflow.</span></span>  
  
## <a name="projects-in-this-sample"></a><span data-ttu-id="38d02-107">このサンプルのプロジェクト</span><span class="sxs-lookup"><span data-stu-id="38d02-107">Projects in this sample</span></span>  
  
|<span data-ttu-id="38d02-108">**プロジェクト名**</span><span class="sxs-lookup"><span data-stu-id="38d02-108">**Project Name**</span></span>|<span data-ttu-id="38d02-109">**説明**</span><span class="sxs-lookup"><span data-stu-id="38d02-109">**Description**</span></span>|<span data-ttu-id="38d02-110">**メイン ファイルします。**</span><span class="sxs-lookup"><span data-stu-id="38d02-110">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="38d02-111">WaitForInput</span><span class="sxs-lookup"><span data-stu-id="38d02-111">WaitForInput</span></span>|<span data-ttu-id="38d02-112">`WaitForInput` アクティビティとそのデザイナーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="38d02-112">Contains `WaitForInput` activity and its designer</span></span>|<span data-ttu-id="38d02-113">WaitForInput.cs</span><span class="sxs-lookup"><span data-stu-id="38d02-113">WaitForInput.cs</span></span><br /><br /> <span data-ttu-id="38d02-114">`WaitForInput` アクティビティ定義。</span><span class="sxs-lookup"><span data-stu-id="38d02-114">`WaitForInput` activity definition.</span></span>|  
|||<span data-ttu-id="38d02-115">WaitForInputDesigner.xaml</span><span class="sxs-lookup"><span data-stu-id="38d02-115">WaitForInputDesigner.xaml</span></span><br /><br /> <span data-ttu-id="38d02-116">`WaitForInput` アクティビティのカスタム デザイナー。</span><span class="sxs-lookup"><span data-stu-id="38d02-116">Custom designer for the `WaitForInput` activity.</span></span>|  
|||<span data-ttu-id="38d02-117">TypeToFirstGenericArgumentConverter.cs</span><span class="sxs-lookup"><span data-stu-id="38d02-117">TypeToFirstGenericArgumentConverter.cs</span></span><br /><br /> <span data-ttu-id="38d02-118">デザイナーでアクティビティのジェネリック型を更新するために使用される WPF 型コンバーター。</span><span class="sxs-lookup"><span data-stu-id="38d02-118">WPF type converter used to update the generic type of the activity in the designer.</span></span>|  
|<span data-ttu-id="38d02-119">WaitForInputTestClient</span><span class="sxs-lookup"><span data-stu-id="38d02-119">WaitForInputTestClient</span></span>|<span data-ttu-id="38d02-120">ワークフロー デザイナーで、複数の WaitForInput アクティビティを使用してワークフローを構成および実行するサンプル クライアント アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="38d02-120">Sample client application that configures and runs a workflow using several WaitForInput activities using the workflow designer.</span></span>|<span data-ttu-id="38d02-121">Sequence1.xaml</span><span class="sxs-lookup"><span data-stu-id="38d02-121">Sequence1.xaml</span></span><br /><br /> <span data-ttu-id="38d02-122">`WaitForInput` アクティビティを使用するシーケンシャル ワークフロー。</span><span class="sxs-lookup"><span data-stu-id="38d02-122">A sequential workflow that uses the `WaitForInput` activity.</span></span>|  
|||<span data-ttu-id="38d02-123">Program.cs</span><span class="sxs-lookup"><span data-stu-id="38d02-123">Program.cs</span></span><br /><br /> <span data-ttu-id="38d02-124">Sequence1.xaml で定義されているワークフローのインスタンスを実行します。</span><span class="sxs-lookup"><span data-stu-id="38d02-124">Runs an instance of the workflow defined in Sequence1.xaml.</span></span>|  
  
## <a name="waitforinput-activity"></a><span data-ttu-id="38d02-125">WaitForInput アクティビティ</span><span class="sxs-lookup"><span data-stu-id="38d02-125">WaitForInput Activity</span></span>  
 <span data-ttu-id="38d02-126">`WaitForInput` アクティビティは、ワークフローに名前付きブックマークを作成します。</span><span class="sxs-lookup"><span data-stu-id="38d02-126">The `WaitForInput` activity creates a named bookmark in a workflow.</span></span> <span data-ttu-id="38d02-127">ブックマークはシグナルを待機し、構成された型のデータを受信します。</span><span class="sxs-lookup"><span data-stu-id="38d02-127">The bookmark waits for a signal and receives data of its configured type.</span></span> <span data-ttu-id="38d02-128">ブックマークが再開されると、ワークフローに渡されたデータを `Result` プロパティで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="38d02-128">After the bookmark is resumed the data passed into the workflow is available through the `Result` property.</span></span>  
  
 <span data-ttu-id="38d02-129">`WaitForInput` アクティビティは、<xref:System.Activities.NativeActivity> クラスを介してのみアクセスできるブックマークを作成する必要があるため、<xref:System.Activities.NativeActivityContext> クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="38d02-129">The `WaitForInput` activity derives from the <xref:System.Activities.NativeActivity> class because it must create bookmarks, which are only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
 <span data-ttu-id="38d02-130">このアクティビティには、デザイナーをバインドするための属性、更新可能なジェネリック引数機能を追加するための属性、および既定のジェネリック型を文字列に設定するための属性が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="38d02-130">The activity has three attributes applied to it for binding a designer, adding the generic argument feature that can be updated, and setting the default generic type to string.</span></span> <span data-ttu-id="38d02-131">また、このアクティビティには、次の表に示す引数があります。</span><span class="sxs-lookup"><span data-stu-id="38d02-131">The activity also has the arguments  listed in the following table.</span></span>  
  
|<span data-ttu-id="38d02-132">**名前**</span><span class="sxs-lookup"><span data-stu-id="38d02-132">**Name**</span></span>|<span data-ttu-id="38d02-133">**Type**</span><span class="sxs-lookup"><span data-stu-id="38d02-133">**Type**</span></span>|<span data-ttu-id="38d02-134">**説明**</span><span class="sxs-lookup"><span data-stu-id="38d02-134">**Description**</span></span>|  
|-|-|-|  
|<span data-ttu-id="38d02-135">TResult</span><span class="sxs-lookup"><span data-stu-id="38d02-135">TResult</span></span>|<span data-ttu-id="38d02-136">ジェネリック引数 (TResult)</span><span class="sxs-lookup"><span data-stu-id="38d02-136">Generic argument (TResult)</span></span>|<span data-ttu-id="38d02-137">ブックマークの型。</span><span class="sxs-lookup"><span data-stu-id="38d02-137">Type of the bookmark.</span></span> <span data-ttu-id="38d02-138">これは再開時にブックマークに渡されるデータの型です。</span><span class="sxs-lookup"><span data-stu-id="38d02-138">This is the type of the data to be passed to the bookmark when resumed.</span></span>|  
|<span data-ttu-id="38d02-139">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="38d02-139">BookmarkName</span></span>|<span data-ttu-id="38d02-140">InArgument\<文字列 ></span><span class="sxs-lookup"><span data-stu-id="38d02-140">InArgument\<string></span></span>|<span data-ttu-id="38d02-141">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="38d02-141">Name of the bookmark.</span></span>|  
|<span data-ttu-id="38d02-142">結果</span><span class="sxs-lookup"><span data-stu-id="38d02-142">Result</span></span>|<span data-ttu-id="38d02-143">InArgument\<TResult ></span><span class="sxs-lookup"><span data-stu-id="38d02-143">InArgument\<TResult></span></span>|<span data-ttu-id="38d02-144">ブックマークが再開されたときにアクティビティに渡されるデータ。</span><span class="sxs-lookup"><span data-stu-id="38d02-144">Data passed to the activity when the bookmark is resumed.</span></span>|  
  
## <a name="waitforinput-activity-designer"></a><span data-ttu-id="38d02-145">WaitForInput アクティビティ デザイナー</span><span class="sxs-lookup"><span data-stu-id="38d02-145">WaitForInput activity designer</span></span>  
 <span data-ttu-id="38d02-146">`WaitForInput` アクティビティ デザイナーは、WaitForInputDesigner.xaml ファイルで実装されます。</span><span class="sxs-lookup"><span data-stu-id="38d02-146">The `WaitForInput` activity designer is implemented in the WaitForInputDesigner.xaml file.</span></span> <span data-ttu-id="38d02-147">`WaitForInput` アクティビティとそのデザイナーは、同じアセンブリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="38d02-147">The `WaitForInput` activity and its designer are included in the same assembly.</span></span> <span data-ttu-id="38d02-148">次の図は、アセンブリと同じ名前を持つカテゴリ内のツールボックスに含まれる `WaitForInput` アクティビティを示しています。</span><span class="sxs-lookup"><span data-stu-id="38d02-148">The following graphic shows the `WaitForInput` activity in the toolbox within a category that has the same name as the assembly.</span></span>  
  
 <span data-ttu-id="38d02-149">![WaitForInput ツールボックスのスクリーン ショット](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")</span><span class="sxs-lookup"><span data-stu-id="38d02-149">![WaitForInput toolbox screenshot](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")</span></span>  
  
 <span data-ttu-id="38d02-150">次の図は、`WaitForInput` デザイナーを示しています。</span><span class="sxs-lookup"><span data-stu-id="38d02-150">The following graphic shows the `WaitForInput` designer.</span></span> <span data-ttu-id="38d02-151">`WaitForInput` アクティビティは非常に基本的なアクティビティであるため、そのすべての引数をデザイナー サーフェイスで直接設定できます。</span><span class="sxs-lookup"><span data-stu-id="38d02-151">Because, the `WaitForInput` activity is very basic, the designer allows setting all its arguments directly in the designer surface.</span></span>  
  
 <span data-ttu-id="38d02-152">![WaitForInput アクティビティ デザイナー](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")</span><span class="sxs-lookup"><span data-stu-id="38d02-152">![WaitForInput Activity Designer](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="38d02-153">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="38d02-153">To use this sample</span></span>  
  
1.  <span data-ttu-id="38d02-154">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、WaitForInput.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="38d02-154">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WaitForInput.sln file.</span></span>  
  
2.  <span data-ttu-id="38d02-155">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="38d02-155">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="38d02-156">サンプルをデバッグなしで開始するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="38d02-156">To start the sample without debugging, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="38d02-157">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="38d02-157">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38d02-158">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="38d02-158">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="38d02-159">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="38d02-159">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38d02-160">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="38d02-160">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`