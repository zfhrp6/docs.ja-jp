---
title: カスタム追跡参加要素を作成する方法
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d53035c2fb41800a91d3cdea134ae811a09fa3e9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="11e74-102">カスタム追跡参加要素を作成する方法</span><span class="sxs-lookup"><span data-stu-id="11e74-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="11e74-103">ワークフロー追跡により、ワークフロー実行の状態が視覚的に示されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="11e74-104">ワークフロー ランタイムによって、ワークフローのライフサイクル イベント、アクティビティのライフサイクル イベント、ブックマークの再開、およびエラーについて説明する追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="11e74-105">これらの追跡レコードは、追跡参加要素によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="11e74-106">Windows Workflow Foundation (WF) には、追跡レコードを Event Tracing for Windows (ETW) イベントとして書き込む標準の追跡参加要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="11e74-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="11e74-107">これで要件が満たされない場合は、カスタムの追跡参加要素を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="11e74-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="11e74-108">チュートリアルのこの手順では、`WriteLine` アクティビティの出力をキャプチャするカスタム追跡参加要素と追跡プロファイルを作成して、ユーザーに表示できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11e74-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11e74-109">チュートリアル入門の各トピックは、前のトピックに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="11e74-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="11e74-110">このトピックを完了する前に、これまでのトピックを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11e74-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="11e74-111">完成版をダウンロードまたはチュートリアルのビデオ チュートリアルを表示を参照してください。 [Windows Workflow Foundation (WF45) - チュートリアル入門](http://go.microsoft.com/fwlink/?LinkID=248976)です。</span><span class="sxs-lookup"><span data-stu-id="11e74-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="11e74-112">このトピックの内容</span><span class="sxs-lookup"><span data-stu-id="11e74-112">In this topic</span></span>  
  
-   [<span data-ttu-id="11e74-113">カスタム追跡参加要素を作成するには</span><span class="sxs-lookup"><span data-stu-id="11e74-113">To create the custom tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [<span data-ttu-id="11e74-114">追跡プロファイルを作成して、追跡参加要素を登録するには</span><span class="sxs-lookup"><span data-stu-id="11e74-114">To create the tracking profile and register the tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [<span data-ttu-id="11e74-115">追跡情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="11e74-115">To display the tracking information</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [<span data-ttu-id="11e74-116">ビルドおよびアプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="11e74-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a> <span data-ttu-id="11e74-117">カスタム追跡参加要素を作成するには</span><span class="sxs-lookup"><span data-stu-id="11e74-117">To create the custom tracking participant</span></span>  
  
1.  <span data-ttu-id="11e74-118">右クリック**NumberGuessWorkflowHost**で**ソリューション エクスプ ローラー**選択**追加**、**クラス**です。</span><span class="sxs-lookup"><span data-stu-id="11e74-118">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="11e74-119">型`StatusTrackingParticipant`に、**名前**ボックスし、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="11e74-119">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="11e74-120">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="11e74-120">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="11e74-121">`StatusTrackingParticipant` クラスを変更して、`TrackingParticipant` から継承されるようにします。</span><span class="sxs-lookup"><span data-stu-id="11e74-121">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4.  <span data-ttu-id="11e74-122">次の `Track` メソッド オーバーライドを追加します。</span><span class="sxs-lookup"><span data-stu-id="11e74-122">Add the following `Track` method override.</span></span> <span data-ttu-id="11e74-123">追跡レコードには、いくつかの種類があります。</span><span class="sxs-lookup"><span data-stu-id="11e74-123">There are several different types of tracking records.</span></span> <span data-ttu-id="11e74-124">ここでは、アクティビティ追跡レコードに含まれる `WriteLine` アクティビティの出力に注目します。</span><span class="sxs-lookup"><span data-stu-id="11e74-124">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="11e74-125">`TrackingRecord` が `ActivityTrackingRecord` アクティビティの `WriteLine` である場合は、ワークフローの `Text` に基づいた名前の付いたファイルに `WriteLine` の `InstanceId` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-125">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="11e74-126">このチュートリアルでは、ファイルはホスト アプリケーションの現在のフォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-126">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="11e74-127">追跡プロファイルを指定しない場合は、既定の追跡プロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-127">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="11e74-128">既定の追跡プロファイルを使用する場合は、すべての `ActivityStates` に関する追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-128">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="11e74-129">ここでは、`WriteLine` アクティビティのライフサイクル中に 1 回だけテキストをキャプチャする必要があるため、`ActivityStates.Executing` 状態からテキストを抽出するだけです。</span><span class="sxs-lookup"><span data-stu-id="11e74-129">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="11e74-130">[追跡プロファイルを作成して、追跡参加要素を登録する](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)、だけを指定する追跡プロファイルが作成された`WriteLine``ActivityStates.Executing`追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-130">In [To create the tracking profile and register the tracking participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
###  <a name="BKMK_TrackingProfile"></a> <span data-ttu-id="11e74-131">追跡プロファイルを作成して、追跡参加要素を登録するには</span><span class="sxs-lookup"><span data-stu-id="11e74-131">To create the tracking profile and register the tracking participant</span></span>  
  
1.  <span data-ttu-id="11e74-132">右クリック**WorkflowHostForm**で**ソリューション エクスプ ローラー**選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="11e74-132">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="11e74-133">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="11e74-133">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  <span data-ttu-id="11e74-134">ワークフロー拡張機能に `ConfigureWorkflowApplication` を追加するコードの直後で、ワークフロー ライフサイクル ハンドラーの前に、`StringWriter` に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="11e74-134">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =   
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="11e74-135">この追跡プロファイルでは、`WriteLine` 状態の `Executing` アクティビティのアクティビティ状態レコードのみがカスタム追跡参加要素に出力されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="11e74-135">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="11e74-136">このコードを追加した後、`ConfigureWorkflowApplication` の先頭は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="11e74-136">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =   
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
###  <a name="BKMK_DisplayTracking"></a> <span data-ttu-id="11e74-137">追跡情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="11e74-137">To display the tracking information</span></span>  
  
1.  <span data-ttu-id="11e74-138">右クリック**WorkflowHostForm**で**ソリューション エクスプ ローラー**選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="11e74-138">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="11e74-139">`InstanceId_SelectedIndexChanged` ハンドラーで、ステータス ウィンドウをクリアするコードの直後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="11e74-139">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="11e74-140">ワークフローの一覧で新しいワークフローを選択すると、そのワークフローの追跡レコードがステータス ウィンドウに読み込まれて表示されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-140">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="11e74-141">完成した `InstanceId_SelectedIndexChanged` ハンドラーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="11e74-141">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="11e74-142">ビルドおよびアプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="11e74-142">To build and run the application</span></span>  
  
1.  <span data-ttu-id="11e74-143">Ctrl キーと Shift キーを押しながら B キーを押してアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="11e74-143">Press Ctrl+Shift+B to build the application.</span></span>  
  
2.  <span data-ttu-id="11e74-144">Ctrl キーを押しながら F5 キーを押してアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="11e74-144">Press Ctrl+F5 to start the application.</span></span>  
  
3.  <span data-ttu-id="11e74-145">推測ゲームを開始、およびをクリックするワークフローの種類の範囲を選択して**新しいゲーム**です。</span><span class="sxs-lookup"><span data-stu-id="11e74-145">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="11e74-146">推定値を入力、**推測**ボックスし、をクリックして**移動**推定値を送信します。</span><span class="sxs-lookup"><span data-stu-id="11e74-146">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="11e74-147">ワークフローの状態がステータス ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-147">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="11e74-148">この出力は、`WriteLine` アクティビティからキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="11e74-148">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="11e74-149">選択して、別のワークフローに切り替え、**ワークフロー インスタンス Id**コンボ ボックスと、現在のワークフローの状態が削除されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="11e74-149">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="11e74-150">以前のワークフローに戻して、次の例のように、状態が復元されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="11e74-150">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11e74-151">追跡が有効になる前に開始されたワークフローに切り替えた場合、状態は表示されません。</span><span class="sxs-lookup"><span data-stu-id="11e74-151">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="11e74-152">ただし、推定値を追加すると、この時点では追跡が有効になっているため、その状態が保存されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-152">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
 <span data-ttu-id="11e74-153">**1 ~ 10 の間の数値を入力してください。**</span><span class="sxs-lookup"><span data-stu-id="11e74-153">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="11e74-154">**推定値が大きすぎます。** </span><span class="sxs-lookup"><span data-stu-id="11e74-154">**Your guess is too high.** </span></span>  
<span data-ttu-id="11e74-155">**1 ~ 10 の間の数値を入力してください。**</span><span class="sxs-lookup"><span data-stu-id="11e74-155">**Please enter a number between 1 and 10**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="11e74-156">この情報は、乱数の範囲を決定する場合に役立ちますが、これまでに作成された推定値に関する情報を含んでいません。</span><span class="sxs-lookup"><span data-stu-id="11e74-156">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="11e74-157">この情報は、次の手順で[する方法: 複数のバージョンのホストはワークフロー サイド バイ サイドの](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)します。</span><span class="sxs-lookup"><span data-stu-id="11e74-157">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
     <span data-ttu-id="11e74-158">ワークフロー インスタンス ID を書き留め、ゲームを最後まで実行します。</span><span class="sxs-lookup"><span data-stu-id="11e74-158">Make a note of the workflow instance id, and play the game through to its completion.</span></span>  
  
4.  <span data-ttu-id="11e74-159">Windows エクスプ ローラーを開きに移動、 **numberguessworkflowhost \bin\debug**フォルダー (または**bin \release**プロジェクトの設定によって)。</span><span class="sxs-lookup"><span data-stu-id="11e74-159">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="11e74-160">プロジェクトの実行可能ファイルに加え、GUID ファイル名が付いたファイルがあることに注意します。</span><span class="sxs-lookup"><span data-stu-id="11e74-160">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="11e74-161">前の手順で完了したワークフローのワークフロー インスタンス ID に対応するファイルを特定してメモ帳で開きます。</span><span class="sxs-lookup"><span data-stu-id="11e74-161">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="11e74-162">追跡情報は、次のような情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="11e74-162">The tracking information contains information similar to the following.</span></span>  
  
 <span data-ttu-id="11e74-163">**1 ~ 10 の間の数値を入力してください。**</span><span class="sxs-lookup"><span data-stu-id="11e74-163">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="11e74-164">**推定値が大きすぎます。** </span><span class="sxs-lookup"><span data-stu-id="11e74-164">**Your guess is too high.** </span></span>  
<span data-ttu-id="11e74-165">**1 ~ 10 の間の数値を入力してください。** </span><span class="sxs-lookup"><span data-stu-id="11e74-165">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="11e74-166">**推定値が大きすぎます。** </span><span class="sxs-lookup"><span data-stu-id="11e74-166">**Your guess is too high.** </span></span>  
<span data-ttu-id="11e74-167">**1 ~ 10 の間の数値を入力してください**だけでなく、ユーザーの推定値がない場合、この追跡データは、ワークフローの最後の推定値に関する情報。</span><span class="sxs-lookup"><span data-stu-id="11e74-167">**Please enter a number between 1 and 10**      In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="11e74-168">これは、追跡情報がワークフローからの `WriteLine` 出力のみで構成されており、表示される最後のメッセージがワークフロー完了後に `Completed` ハンドラーから表示されるためです。</span><span class="sxs-lookup"><span data-stu-id="11e74-168">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="11e74-169">チュートリアルでは、次の手順で[する方法: ホストはワークフロー サイド バイ サイドの複数のバージョン](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)、既存の`WriteLine`アクティビティが変更され、ユーザーの推定値と追加の表示を`WriteLine`アクティビティを追加します。最終的な結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="11e74-169">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="11e74-170">これらの変更が統合されると、[する方法: ホストはワークフロー サイド バイ サイドの複数のバージョン](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)同時に複数のバージョンのワークフローをホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="11e74-170">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
