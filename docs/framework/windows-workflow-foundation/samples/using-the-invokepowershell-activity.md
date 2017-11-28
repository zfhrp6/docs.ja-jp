---
title: "InvokePowerShell アクティビティの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23351ad32e608dc27b973691ec9a00fc2f94b3fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-invokepowershell-activity"></a><span data-ttu-id="f93e4-102">InvokePowerShell アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="f93e4-102">Using the InvokePowerShell Activity</span></span>
<span data-ttu-id="f93e4-103">InvokePowerShell サンプルでは、`InvokePowerShell` アクティビティを使用して Windows PowerShell コマンドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-103">The InvokePowerShell sample demonstrates how to invoke Windows PowerShell commands using the `InvokePowerShell` activity.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f93e4-104">使用例</span><span class="sxs-lookup"><span data-stu-id="f93e4-104">Demonstrates</span></span>  
  
-   <span data-ttu-id="f93e4-105">Windows PowerShell コマンドの簡便さと革新性。</span><span class="sxs-lookup"><span data-stu-id="f93e4-105">Simple innovation of Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="f93e4-106">Windows PowerShell の出力パイプラインから値を取得してワークフロー変数に格納する。</span><span class="sxs-lookup"><span data-stu-id="f93e4-106">Retrieve values from the Windows PowerShell output pipeline and store them in workflow variables.</span></span>  
  
-   <span data-ttu-id="f93e4-107">実行するコマンドのための入力パイプラインとして Windows PowerShell にデータを渡す。</span><span class="sxs-lookup"><span data-stu-id="f93e4-107">Pass data into windows PowerShell as input pipeline for an executing command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f93e4-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f93e4-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f93e4-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f93e4-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f93e4-110">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="f93e4-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f93e4-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a><span data-ttu-id="f93e4-112">説明</span><span class="sxs-lookup"><span data-stu-id="f93e4-112">Discussion</span></span>  
 <span data-ttu-id="f93e4-113">このサンプルには次の 3 つのプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f93e4-113">This sample contains the following three projects.</span></span>  
  
|<span data-ttu-id="f93e4-114">プロジェクト名</span><span class="sxs-lookup"><span data-stu-id="f93e4-114">Project Name</span></span>|<span data-ttu-id="f93e4-115">説明</span><span class="sxs-lookup"><span data-stu-id="f93e4-115">Description</span></span>|<span data-ttu-id="f93e4-116">メイン ファイル</span><span class="sxs-lookup"><span data-stu-id="f93e4-116">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="f93e4-117">CodedClient</span><span class="sxs-lookup"><span data-stu-id="f93e4-117">CodedClient</span></span>|<span data-ttu-id="f93e4-118">PowerShell アクティビティを使用するサンプル クライアント アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="f93e4-118">A sample client application that uses the PowerShell activity.</span></span>|<span data-ttu-id="f93e4-119">-   **Program.cs**: InvokePowerShell アクティビティを呼び出すシーケンス ベースのワークフローをプログラムで作成します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-119">-   **Program.cs**: Programmatically creates a sequence-based workflow that calls the InvokePowerShell activity.</span></span>|  
|<span data-ttu-id="f93e4-120">DesignerClient</span><span class="sxs-lookup"><span data-stu-id="f93e4-120">DesignerClient</span></span>|<span data-ttu-id="f93e4-121">`InvokePowerShell` カスタム アクティビティや他のさまざまなカスタム アクティビティを含むカスタム アクティビティのセットと、それらを使用するワークフロー。</span><span class="sxs-lookup"><span data-stu-id="f93e4-121">A set of custom activities that contain the `InvokePowerShell` custom activity and other miscellaneous custom activities, and a workflow that uses them.</span></span>|<ul><li><span data-ttu-id="f93e4-122">アクティビティ:</span><span class="sxs-lookup"><span data-stu-id="f93e4-122">Activities:</span></span><br /><br /> <ul><li><span data-ttu-id="f93e4-123">**PrintCollection.cs**: コンソールをコレクション内のすべての項目を出力するヘルパー アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-123">**PrintCollection.cs**: A helper activity that prints all the items in a collection to the console.</span></span></li><li><span data-ttu-id="f93e4-124">**ReadLine.cs**: コンソールからの入力を読み取るのためのヘルパー アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-124">**ReadLine.cs**: A helper activity for reading input from the console.</span></span></li></ul></li><li><span data-ttu-id="f93e4-125">ファイル システム:</span><span class="sxs-lookup"><span data-stu-id="f93e4-125">File System:</span></span><br /><br /> <ul><li><span data-ttu-id="f93e4-126">**Copy.xaml**: ファイルをコピーするアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-126">**Copy.xaml**: An activity that copies a file.</span></span></li><li><span data-ttu-id="f93e4-127">**CreateFile.xaml**: ファイルを作成するアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-127">**CreateFile.xaml**: An activity that creates a file.</span></span></li><li><span data-ttu-id="f93e4-128">**DeleteFile.xaml**: ファイルを削除するアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-128">**DeleteFile.xaml**: An activity that deletes a file.</span></span></li><li><span data-ttu-id="f93e4-129">**MakeDir.xaml**: ディレクトリを作成するアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-129">**MakeDir.xaml**: An activity that creates a directory.</span></span></li><li><span data-ttu-id="f93e4-130">**Move.xaml**: ファイルを移動するアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-130">**Move.xaml**: An activity that moves a file.</span></span></li><li><span data-ttu-id="f93e4-131">**ReadFile.xaml**: ファイルを読み取り、その内容を返すアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-131">**ReadFile.xaml**: An activity that reads a file and returns its contents.</span></span></li><li><span data-ttu-id="f93e4-132">**TestPath.xaml**: パスの存在をテストするアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-132">**TestPath.xaml**: An activity that tests for the existence of a path.</span></span></li></ul></li><li><span data-ttu-id="f93e4-133">プロセス:</span><span class="sxs-lookup"><span data-stu-id="f93e4-133">Process:</span></span><br /><br /> <ul><li><span data-ttu-id="f93e4-134">**GetProcess.xaml**: 実行中のプロセス一覧を取得するアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-134">**GetProcess.xaml**: An activity that gets a list of running processes.</span></span></li><li><span data-ttu-id="f93e4-135">**StopProcess.xaml**: 特定のプロセスを停止するアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-135">**StopProcess.xaml**: An activity that stops a specific process.</span></span></li></ul></li><li><span data-ttu-id="f93e4-136">**Program.cs**: Sequence1 ワークフローを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-136">**Program.cs**: Calls the Sequence1 workflow.</span></span></li><li><span data-ttu-id="f93e4-137">**Sequence1.xaml**: シーケンス ベースのワークフローです。</span><span class="sxs-lookup"><span data-stu-id="f93e4-137">**Sequence1.xaml**: A sequence-based workflow.</span></span></li></ul>|  
|<span data-ttu-id="f93e4-138">PowerShell</span><span class="sxs-lookup"><span data-stu-id="f93e4-138">PowerShell</span></span>|<span data-ttu-id="f93e4-139">`InvokePowerShell` アクティビティと、それに関連付けられたデザイナー。</span><span class="sxs-lookup"><span data-stu-id="f93e4-139">The `InvokePowerShell` activity and its associated designers.</span></span>|<span data-ttu-id="f93e4-140">アクティビティのファイル</span><span class="sxs-lookup"><span data-stu-id="f93e4-140">Activity Files</span></span><br /><br /> <span data-ttu-id="f93e4-141">-   **ExecutePowerShell.cs**: アクティビティのメインの実行ロジック。</span><span class="sxs-lookup"><span data-stu-id="f93e4-141">-   **ExecutePowerShell.cs**: The main execution logic of the activity.</span></span><br /><span data-ttu-id="f93e4-142">-   **InvokePowerShell.cs**: ジェネリック (値を返す) バージョンと非ジェネリック (値) のバージョンを含むメインの実行ロジックのラッパー。</span><span class="sxs-lookup"><span data-stu-id="f93e4-142">-   **InvokePowerShell.cs**: The wrapper around the main execution logic, which contains a generic (return value) version and a non-generic (non-return value) version.</span></span> <span data-ttu-id="f93e4-143">これは、アクティビティのパブリック インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f93e4-143">This is the public interface for the activity.</span></span><br /><span data-ttu-id="f93e4-144">-   **NoPersistZone.cs**: このアクティビティでは、すべての子アクティビティがの永続化します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-144">-   **NoPersistZone.cs**: This activity prevents any child activities from persisting.</span></span> <span data-ttu-id="f93e4-145">このクラスは、`InvokePowerShell` アクティビティの実装の中で、アクティビティが実行の途中で永続化されるのを防ぐために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-145">This class is used within the `InvokePowerShell` activity implementation to prevent the activity from being persisted mid-execution.</span></span><br /><br /> <span data-ttu-id="f93e4-146">デザイナーのファイル:</span><span class="sxs-lookup"><span data-stu-id="f93e4-146">Designer files:</span></span><br /><br /> <span data-ttu-id="f93e4-147">1.**ArgumentDictionaryEditor.cs**: ユーザーがの引数を編集できる Windows ダイアログ、`InvokePowerShell`アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f93e4-147">1.  **ArgumentDictionaryEditor.cs**: A Windows dialog that allows the user to edit the arguments of the `InvokePowerShell` activity.</span></span><br /><span data-ttu-id="f93e4-148">2.**GenericInvokePowerShellDesigner.xaml**と**GenericInvokePowerShellDesigner.xaml.cs**: ジェネリックの外観を定義`InvokePowerShell`でアクティビティ[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f93e4-148">2.  **GenericInvokePowerShellDesigner.xaml** and **GenericInvokePowerShellDesigner.xaml.cs**: Defines the appearance of the generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span><br /><span data-ttu-id="f93e4-149">3.**InvokePowerShellDesigner.xaml**と**InvokePowerShellDesigner.cs**: 非ジェネリックの外観を定義`InvokePowerShell`でアクティビティ[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f93e4-149">3.  **InvokePowerShellDesigner.xaml** and **InvokePowerShellDesigner.cs**: Defines the appearance of the non-generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>|  
  
 <span data-ttu-id="f93e4-150">PowerShell アクティビティの使用方法を把握しているとその内部機能を理解しやすくなるため、クライアント プロジェクトから先に説明します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-150">The client projects are discussed first, as it is easier to understand the internal functionality of the PowerShell activity once its use is understood.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="f93e4-151">このサンプルの使用</span><span class="sxs-lookup"><span data-stu-id="f93e4-151">Using This Sample</span></span>  
 <span data-ttu-id="f93e4-152">以降では、このサンプルの 3 つのプロジェクトの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-152">The following sections describe how to use the three projects in the sample.</span></span>  
  
### <a name="using-the-coded-client-project"></a><span data-ttu-id="f93e4-153">CodedClient プロジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="f93e4-153">Using the Coded Client Project</span></span>  
 <span data-ttu-id="f93e4-154">このサンプル クライアントは、`InvokePowerShell` アクティビティのさまざまな使用方法の例を含むシーケンス アクティビティをプログラムで作成します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-154">The sample client programmatically creates a sequence activity, which contains examples of several different methods of using the `InvokePowerShell` activity.</span></span> <span data-ttu-id="f93e4-155">最初の呼び出しでは、メモ帳を起動します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-155">The first invocation launches Notepad.</span></span>  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 <span data-ttu-id="f93e4-156">2 番目の呼び出しでは、ローカル コンピューターで実行されているプロセスのリストを取得します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-156">The second invocation gets a list of the processes running on the local machine.</span></span>  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 <span data-ttu-id="f93e4-157">`Output` は、コマンドの出力を格納するための変数です。</span><span class="sxs-lookup"><span data-stu-id="f93e4-157">`Output` is the variable used to store the output of the command.</span></span>  
  
 <span data-ttu-id="f93e4-158">次の呼び出しは、PowerShell 呼び出しの個々の出力の後処理のステップを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-158">The next call demonstrates how to run a post-processing step on each individual output of the PowerShell invocation.</span></span> <span data-ttu-id="f93e4-159">`InitializationAction` は、各プロセスの文字列形式を出力する関数に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-159">`InitializationAction` is set to the function that outputs a string representation for each process.</span></span> <span data-ttu-id="f93e4-160">それらの文字列のコレクションは、`Output` アクティビティによって `InvokePowerShell<string>` 変数で返されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-160">The collection of these strings is returned in the `Output` variable by the `InvokePowerShell<string>` activity.</span></span>  
  
 <span data-ttu-id="f93e4-161">その後に続く一連の `InvokePowerShell` の呼び出しは、アクティビティにデータを渡して出力とエラーを取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f93e4-161">The succeeding `InvokePowerShell` calls demonstrate passing data into the activity and getting outputs and errors out.</span></span>  
  
### <a name="using-the-designer-client-project"></a><span data-ttu-id="f93e4-162">DesignerClient プロジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="f93e4-162">Using the Designer Client Project</span></span>  
 <span data-ttu-id="f93e4-163">DesignerClient プロジェクトは一連のカスタム アクティビティで構成されていますが、それらのほぼすべてに `InvokePowerShell` アクティビティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f93e4-163">The DesignerClient project consists of a set of custom activities, almost all of which are built containing the `InvokePowerShell` activity.</span></span> <span data-ttu-id="f93e4-164">ほとんどのアクティビティは、非ジェネリック バージョンの `InvokePowerShell` アクティビティを呼び出します。したがって、戻り値を受け取りません。</span><span class="sxs-lookup"><span data-stu-id="f93e4-164">Most of the activities call the non-generic version of the `InvokePowerShell` activity, and do not expect a return value.</span></span> <span data-ttu-id="f93e4-165">ジェネリック バージョンの `InvokePowerShell` アクティビティを使用するその他のアクティビティは、`InitializationAction` 引数を使用して結果の後処理を行います。</span><span class="sxs-lookup"><span data-stu-id="f93e4-165">Other activities use the generic version of the `InvokePowerShell` activity, and use the `InitializationAction` argument to post-process the results.</span></span>  
  
## <a name="using-the-powershell-project"></a><span data-ttu-id="f93e4-166">PowerShell プロジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="f93e4-166">Using the PowerShell Project</span></span>  
 <span data-ttu-id="f93e4-167">アクティビティの主要なアクションは `ExecutePowerShell` クラスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-167">The main action of the activity takes place in the `ExecutePowerShell` class.</span></span> <span data-ttu-id="f93e4-168">PowerShell コマンドの実行によってメインのワークフロー スレッドがブロックされないようにする必要があるため、アクティビティは、<xref:System.Activities.AsyncCodeActivity> クラスを継承して非同期アクティビティとして作成されています。</span><span class="sxs-lookup"><span data-stu-id="f93e4-168">Because the execution of PowerShell commands should not block the main workflow thread, the activity is created to be an asynchronous activity by inheriting from the <xref:System.Activities.AsyncCodeActivity> class.</span></span>  
  
 <span data-ttu-id="f93e4-169">ワークフロー ランタイムによって <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> メソッドが呼び出されると、アクティビティの実行が開始されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-169">The <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> method is called by the workflow runtime to begin running the activity.</span></span> <span data-ttu-id="f93e4-170">このメソッドは、まず最初に、PowerShell API を呼び出して PowerShell パイプラインを作成します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-170">It starts by calling PowerShell APIs to create a PowerShell pipeline.</span></span>  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 <span data-ttu-id="f93e4-171">次に、PowerShell コマンドを作成してパラメーターと変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-171">It then creates a PowerShell command and populates it with parameters and variables.</span></span>  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 <span data-ttu-id="f93e4-172">この時点で、パイプ入力された入力がパイプラインにも送信されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-172">The inputs piped in are also sent to the pipeline at this point.</span></span> <span data-ttu-id="f93e4-173">最後に、パイプラインが `PipelineInvokerAsyncResult` オブジェクトでラップされて返されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-173">Finally, the pipeline is wrapped in a `PipelineInvokerAsyncResult` object and returned.</span></span> <span data-ttu-id="f93e4-174">`PipelineInvokerAsyncResult` オブジェクトは、リスナーを登録してパイプラインを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-174">The `PipelineInvokerAsyncResult` object registers a listener and invokes the pipeline.</span></span>  
  
```  
pipeline.InvokeAsync();  
```  
  
 <span data-ttu-id="f93e4-175">実行が終了すると、出力とエラーが同じ `PipelineInvokerAsyncResult` オブジェクトに格納され、最初に <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> に渡されたコールバック メソッドが呼び出されてワークフロー ランタイムに制御が返されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-175">When execution finishes, output and errors are stored within the same `PipelineInvokerAsyncResult` object, and control is handed back to the workflow runtime by calling the callback method originally passed to <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span></span>  
  
 <span data-ttu-id="f93e4-176">メソッドの実行の最後に、ワークフロー ランタイムがアクティビティの <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-176">At the end of the method's execution, the workflow runtime calls the activity’s <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> method.</span></span>  
  
 <span data-ttu-id="f93e4-177">`InvokePowerShell` クラスは `ExecutePowerShellCommand` クラスをラップして、ジェネリック バージョンと非ジェネリック バージョンの 2 つのバージョンのアクティビティを作成します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-177">The `InvokePowerShell` class wraps the `ExecutePowerShellCommand` class and creates two versions of the activity; a generic version and a non-generic version.</span></span> <span data-ttu-id="f93e4-178">非ジェネリック バージョンは PowerShell の実行の出力をそのまま返しますが、ジェネリック バージョンは個々の結果をジェネリック型に変換します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-178">The non-generic version returns the output of the PowerShell execution directly, whereas the generic version transforms the individual results to the generic type.</span></span>  
  
 <span data-ttu-id="f93e4-179">ジェネリック バージョンのアクティビティは、`ExecutePowerShellCommand` を呼び出してその結果の後処理を行うシーケンシャル ワークフローとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="f93e4-179">The generic version of the activity is implemented as a sequential workflow that calls `ExecutePowerShellCommand` and post-processes its results.</span></span> <span data-ttu-id="f93e4-180">後処理のステップでは、結果のコレクションの各要素に対して、`InitializationAction` が設定されている場合にはそれが呼び出され、</span><span class="sxs-lookup"><span data-stu-id="f93e4-180">For each element in the result collection, the post-processing step calls `InitializationAction` if it is set.</span></span> <span data-ttu-id="f93e4-181">設定されていない場合には単純なキャストが行われます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-181">Otherwise, it does a simple cast.</span></span>  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 <span data-ttu-id="f93e4-182">2 つの `InvokePowerShell` アクティビティ (ジェネリックと非ジェネリック) のそれぞれにデザイナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f93e4-182">For each of the two `InvokePowerShell` activities (generic, and non-generic), a designer was created.</span></span> <span data-ttu-id="f93e4-183">InvokePowerShellDesigner.xaml とその関連 .cs ファイルは、非ジェネリック バージョンの [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] アクティビティの`InvokePowerShell`での外観を定義します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-183">InvokePowerShellDesigner.xaml and its associated .cs file define the appearance in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] for the non-generic version of the `InvokePowerShell` activity.</span></span> <span data-ttu-id="f93e4-184">InvokePowerShellDesigner.xaml では、<xref:System.Windows.Controls.DockPanel> を使用してグラフィカル インターフェイスを表しています。</span><span class="sxs-lookup"><span data-stu-id="f93e4-184">Inside InvokePowerShellDesigner.xaml, a <xref:System.Windows.Controls.DockPanel> is used to represent the graphical interface.</span></span>  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 <span data-ttu-id="f93e4-185">テキスト ボックスの `Text` プロパティが双方向のバインドになっているため、アクティビティの `CommandText` プロパティの値がデザイナーに入力された値と同じになります。</span><span class="sxs-lookup"><span data-stu-id="f93e4-185">Note that the `Text` property of the text box is a two-way binding that ensures that the value of the activity’s `CommandText` property is equivalent to the value input into the designer.</span></span>  
  
 <span data-ttu-id="f93e4-186">GenericInvokePowerShellDesigner.xaml とその関連 .cs ファイルは、ジェネリック `InvokePowerShell` アクティビティのグラフィカル インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-186">GenericInvokePowerShellDesigner.xaml and its associated .cs file define the graphical interface for the generic `InvokePowerShell` activity.</span></span> <span data-ttu-id="f93e4-187">このデザイナーは、`InitializationAction` を設定できるようになっているため、非ジェネリック バージョンのデザイナーに比べてやや複雑です。</span><span class="sxs-lookup"><span data-stu-id="f93e4-187">The designer is slightly more complicated because it allows users to set an `InitializationAction`.</span></span> <span data-ttu-id="f93e4-188">ここでのポイントは、<xref:System.Activities.Presentation.WorkflowItemPresenter> を使用して、`InvokePowerShell` のデザイナー画面に子アクティビティをドラッグ アンド ドロップできるようにしていることです。</span><span class="sxs-lookup"><span data-stu-id="f93e4-188">The key element is the usage of <xref:System.Activities.Presentation.WorkflowItemPresenter> to allow drag and drop of child activities onto the `InvokePowerShell` designer surface.</span></span>  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 <span data-ttu-id="f93e4-189">デザイナーでカスタマイズできるのは、デザイン キャンバスでのアクティビティの外観を定義する .xaml ファイルだけではありません。</span><span class="sxs-lookup"><span data-stu-id="f93e4-189">The designer customization does not stop with the .xaml files that define the appearance of the activity on the design canvas.</span></span> <span data-ttu-id="f93e4-190">アクティビティのパラメーターを表示するために使用されるダイアログ ボックスもカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-190">The dialog boxes used to display the parameters of the activity can also be customized.</span></span> <span data-ttu-id="f93e4-191">これらのパラメーターや PowerShell 変数は、PowerShell コマンドの動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-191">These parameters and PowerShell variables affect the behavior of PowerShell commands.</span></span> <span data-ttu-id="f93e4-192">アクティビティとして公開<!--zz <xref:System.Collections.Generic.Dictionary%601>-->`System.Collections.Generic.Dictionary`型です。</span><span class="sxs-lookup"><span data-stu-id="f93e4-192">The activity exposes them as <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` types.</span></span> <span data-ttu-id="f93e4-193">これらの型を編集できるダイアログ ボックスは、ArgumentDictionaryEditor.cs、PropertyEditorResources.xaml、および PropertyEditorResources.cs で定義されています。</span><span class="sxs-lookup"><span data-stu-id="f93e4-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml and PropertyEditorResources.cs define the dialog box that allows you to edit these types.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f93e4-194">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="f93e4-194">To set up, build, and run the sample</span></span>  
 <span data-ttu-id="f93e4-195">このサンプルを実行するには Windows PowerShell をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f93e4-195">You must install Windows PowerShell to run this sample.</span></span> <span data-ttu-id="f93e4-196">この場所から Windows PowerShell をインストールすることができます: [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383)です。</span><span class="sxs-lookup"><span data-stu-id="f93e4-196">Windows PowerShell can be installed from this location: [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).</span></span>  
  
#### <a name="to-run-the-coded-client"></a><span data-ttu-id="f93e4-197">コード クライアントを実行するには</span><span class="sxs-lookup"><span data-stu-id="f93e4-197">To run the coded client</span></span>  
  
1.  <span data-ttu-id="f93e4-198">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して PowerShell.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-198">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f93e4-199">ソリューションを右クリックしてビルドします。</span><span class="sxs-lookup"><span data-stu-id="f93e4-199">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="f93e4-200">右クリックし、 **CodedClient**プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="f93e4-200">Right-click the **CodedClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="f93e4-201">Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-201">Press CTRL+F5 to run the application.</span></span>  
  
#### <a name="to-run-the-designer-client"></a><span data-ttu-id="f93e4-202">デザイナー クライアントを実行するには</span><span class="sxs-lookup"><span data-stu-id="f93e4-202">To run the designer client</span></span>  
  
1.  <span data-ttu-id="f93e4-203">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して PowerShell.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-203">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f93e4-204">ソリューションを右クリックしてビルドします。</span><span class="sxs-lookup"><span data-stu-id="f93e4-204">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="f93e4-205">右クリックし、 **DesignerClient**プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="f93e4-205">Right-click the **DesignerClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="f93e4-206">Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="f93e4-206">Press CTRL+F5 to run the application.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="f93e4-207">既知の問題</span><span class="sxs-lookup"><span data-stu-id="f93e4-207">Known Issues</span></span>  
  
1.  <span data-ttu-id="f93e4-208">`InvokePowerShell` アクティビティのアセンブリやプロジェクトを別のプロジェクトから参照してビルド エラーが発生した場合は、必要に応じて、新しいプロジェクトの .csproj ファイル (`<SpecificVersion>True</SpecificVersion>` を参照している行の下) に `InvokePowerShell` 要素を手動で追加してください。</span><span class="sxs-lookup"><span data-stu-id="f93e4-208">If referencing the `InvokePowerShell` activity assembly or project from another project results in a build error, you may need to manually add the `<SpecificVersion>True</SpecificVersion>` element to the .csproj file of the new project under the line that references `InvokePowerShell`.</span></span>  
  
2.  <span data-ttu-id="f93e4-209">追加するとすぐに Visual Studio で次のエラー メッセージが表示される Windows PowerShell がインストールされていない場合、`InvokePowerShell`アクティビティをワークフローに。`Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span><span class="sxs-lookup"><span data-stu-id="f93e4-209">If Windows PowerShell is not installed, the following error message is displayed in Visual Studio as soon as you add an `InvokePowerShell` activity onto a workflow: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span></span>  
  
3.  <span data-ttu-id="f93e4-210">Windows PowerShell 2.0 では、プログラムで `$input.MoveNext()` を呼び出すと呼び出しが失敗します。そのため、`$input.MoveNext()` を使用するスクリプトで予想外のエラーと結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-210">In Windows PowerShell 2.0, programmatically calling `$input.MoveNext()` fails and scripts using `$input.MoveNext()` produce unintended errors and results.</span></span> <span data-ttu-id="f93e4-211">この問題を回避するには、配列を反復処理するときに、`foreach` を呼び出す代わりに PowerShell の動詞 `MoveNext()` を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f93e4-211">To work around this issue, consider using the PowerShell verb `foreach` instead of calling `MoveNext()` when iterating an array.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f93e4-212">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f93e4-212">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f93e4-213">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f93e4-213">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f93e4-214">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="f93e4-214">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f93e4-215">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f93e4-215">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="see-also"></a><span data-ttu-id="f93e4-216">関連項目</span><span class="sxs-lookup"><span data-stu-id="f93e4-216">See Also</span></span>
