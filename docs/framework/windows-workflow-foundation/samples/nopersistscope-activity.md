---
title: "NoPersistScope アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f0dae84428f079dc3efb0c7ee620fa8c6ff87a8f
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="nopersistscope-activity"></a><span data-ttu-id="e18bd-102">NoPersistScope アクティビティ</span><span class="sxs-lookup"><span data-stu-id="e18bd-102">NoPersistScope Activity</span></span>
<span data-ttu-id="e18bd-103">このサンプルでは、ワークフローでシリアル化不可能で破棄可能な状態を処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e18bd-103">This sample shows how to manipulate a non-serializable and disposable state within a workflow.</span></span> <span data-ttu-id="e18bd-104">ワークフローでシリアル化不可能な状態を永続化しないようにし、破棄可能なオブジェクトをワークフローで使用した後にクリーンアップすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="e18bd-104">It is important that workflows do not attempt to persist non-serializable state and it is also important for disposable objects to be cleaned up after they are used in workflow.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e18bd-105">使用例</span><span class="sxs-lookup"><span data-stu-id="e18bd-105">Demonstrates</span></span>  
 <span data-ttu-id="e18bd-106">`NoPersistScope` カスタム アクティビティおよびデザイナー。</span><span class="sxs-lookup"><span data-stu-id="e18bd-106">`NoPersistScope` custom activity and designer.</span></span>  
  
## <a name="using-the-nopersistzone-activity"></a><span data-ttu-id="e18bd-107">NoPersistZone アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="e18bd-107">Using the NoPersistZone activity</span></span>  
 <span data-ttu-id="e18bd-108">サンプル ワークフローの実行時に、`CreateTextWriter` というカスタム アクティビティによって、<xref:System.IO.TextWriter> 型のオブジェクトが作成されてワークフロー変数に保存されます。</span><span class="sxs-lookup"><span data-stu-id="e18bd-108">When the sample workflow runs, a custom activity called `CreateTextWriter` creates an object of type <xref:System.IO.TextWriter> and saves it into a workflow variable.</span></span> <span data-ttu-id="e18bd-109"><xref:System.IO.TextWriter> は <xref:System.IDisposable> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e18bd-109"><xref:System.IO.TextWriter> is an <xref:System.IDisposable> object.</span></span> <span data-ttu-id="e18bd-110">この <xref:System.IO.TextWriter> は、サンプルが実行されるディレクトリにある out.txt という名前のファイルに書き込むように構成されており、コンソールで入力するテキストをエコーするときに <xref:System.Activities.Statements.WriteLine> アクティビティによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="e18bd-110">This <xref:System.IO.TextWriter>, which is configured to write to a file named ‘out.txt’ in the directory in which the sample runs, is used by a <xref:System.Activities.Statements.WriteLine> activity as it echoes any text you type in at the console.</span></span>  
  
 <span data-ttu-id="e18bd-111">エコー ロジックは、ワークフローが永続化されないようにする `NoPersistScope` アクティビティ (このサンプルの一部でもあるコード) 内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="e18bd-111">The echo logic runs within a `NoPersistScope` activity (the code for which is also part of this sample), which prevents the workflow from being persisted.</span></span> <span data-ttu-id="e18bd-112">入力した場合`unload`コンソールで、ホストはワークフロー インスタンスを永続化を試みますが、ワークフロー内に留まるので、この操作がタイムアウト、`NoPersistScope`です。</span><span class="sxs-lookup"><span data-stu-id="e18bd-112">If you type in `unload` at the console, the host attempts to persist the workflow instance but this operation times out because the workflow remains within a `NoPersistScope`.</span></span> <span data-ttu-id="e18bd-113">また、ワークフローは `Dispose` というカスタム アクティビティを使用して、<xref:System.IO.TextWriter> オブジェクトを使い終わったら破棄します。</span><span class="sxs-lookup"><span data-stu-id="e18bd-113">The workflow also utilizes a custom activity called `Dispose` to dispose the <xref:System.IO.TextWriter> object when the workflow is finished using it.</span></span> <span data-ttu-id="e18bd-114">`Dispose` アクティビティは、Try ブロックの実行中に例外が発生した場合でも実行されるように、<xref:System.Activities.Statements.TryCatch.Finally%2A> 変数が宣言される <xref:System.Activities.Statements.TryCatch> アクティビティの <xref:System.IO.TextWriter> ブロック内に配置されます。</span><span class="sxs-lookup"><span data-stu-id="e18bd-114">The `Dispose` activity is placed within the <xref:System.Activities.Statements.TryCatch.Finally%2A> block of the <xref:System.Activities.Statements.TryCatch> activity in which the <xref:System.IO.TextWriter> variable is declared, to ensure that it runs even if an exception should occur during execution of the Try block.</span></span>  
  
 <span data-ttu-id="e18bd-115">入力できます`exit`をワークフロー インスタンスを完了し、プログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="e18bd-115">You can type in `exit` to complete the workflow instance and exit the program.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="e18bd-116">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="e18bd-116">To run the sample</span></span>  
  
1.  <span data-ttu-id="e18bd-117">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で NoPersistZone.sln ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="e18bd-117">Open the NoPersistZone.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="e18bd-118">ソリューションをビルドするには、ctrl キーと shift キーを押しながら B キーを押してまたは選択**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="e18bd-118">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="e18bd-119">F5 キーを押してビルドが成功した後、または選択**デバッグの開始**から、**デバッグ**メニューまたは、ctrl キーを押しながら f5 キーを押してまたは選択**デバッグなしで開始**から、**デバッグ** メニューの デバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="e18bd-119">Once the build has succeeded, press F5 or select **Start Debugging** from the **Debug** menu alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="e18bd-120">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="e18bd-120">To cleanup (optional)</span></span>  
  
1.  <span data-ttu-id="e18bd-121">SQL インスタンス ストアを削除するには、Cleanup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="e18bd-121">To remove the SQL Instance Store, run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e18bd-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e18bd-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e18bd-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e18bd-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e18bd-124">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="e18bd-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e18bd-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e18bd-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`