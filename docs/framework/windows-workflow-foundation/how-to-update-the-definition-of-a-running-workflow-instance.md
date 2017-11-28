---
title: "実行中のワークフロー インスタンスの定義を更新する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73b36ca4dfd5ba61e99531df53a0e71dd4d32551
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="e0b5a-102">実行中のワークフロー インスタンスの定義を更新する方法</span><span class="sxs-lookup"><span data-stu-id="e0b5a-102">How to: Update the Definition of a Running Workflow Instance</span></span>
<span data-ttu-id="e0b5a-103">動的更新は、ワークフロー アプリケーションの開発者が永続化されたワークフロー インスタンスのワークフロー定義を更新するためのメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="e0b5a-104">必要な変更には、バグ修正の実装、新しい要件の実装、または予期しない変更への対応があります。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-104">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="e0b5a-105">チュートリアルでは、この手順は、動的更新を使用して永続化されたインスタンスを変更する方法を示します、`v1`で導入された新機能と一致するワークフローを推測数値[する方法: 複数のバージョンをワークフロー サイド バイ サイドのホスト](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="e0b5a-105">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0b5a-106">完成版をダウンロードまたはチュートリアルのビデオ チュートリアルを表示を参照してください。 [Windows Workflow Foundation (WF45) - チュートリアル入門](http://go.microsoft.com/fwlink/?LinkID=248976)です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="e0b5a-107">このトピックの内容</span><span class="sxs-lookup"><span data-stu-id="e0b5a-107">In this topic</span></span>  
  
-   [<span data-ttu-id="e0b5a-108">CreateUpdateMaps プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-108">To create the CreateUpdateMaps project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)  
  
-   [<span data-ttu-id="e0b5a-109">StateMachineNumberGuessWorkflow を更新するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-109">To update StateMachineNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)  
  
-   [<span data-ttu-id="e0b5a-110">FlowchartNumberGuessWorkflow を更新するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-110">To update FlowchartNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)  
  
-   [<span data-ttu-id="e0b5a-111">SequentialNumberGuessWorkflow を更新するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-111">To update SequentialNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)  
  
-   [<span data-ttu-id="e0b5a-112">CreateUpdateMaps アプリケーションをビルドして、実行</span><span class="sxs-lookup"><span data-stu-id="e0b5a-112">To build and run the CreateUpdateMaps application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)  
  
-   [<span data-ttu-id="e0b5a-113">更新されたワークフロー アセンブリをビルドするには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-113">To build the updated workflow assembly</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)  
  
-   [<span data-ttu-id="e0b5a-114">新しいバージョンで WorkflowVersionMap を更新するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-114">To update WorkflowVersionMap with the new versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="e0b5a-115">動的更新を適用するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-115">To apply the dynamic updates</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)  
  
-   [<span data-ttu-id="e0b5a-116">更新されたワークフローを含むアプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-116">To run the application with the updated workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)  
  
-   [<span data-ttu-id="e0b5a-117">ワークフローの以前のバージョンを開始できるようにするには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-117">To enable starting previous versions of the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)  
  
###  <span data-ttu-id="e0b5a-118"><a name="BKMK_CreateProject"></a>CreateUpdateMaps プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-118"><a name="BKMK_CreateProject"></a> To create the CreateUpdateMaps project</span></span>  
  
1.  <span data-ttu-id="e0b5a-119">右クリック**WF45GettingStartedTutorial**で**ソリューション エクスプ ローラー**選択**追加**、**新しいプロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-119">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="e0b5a-120">**インストール**ノード、 **Visual c#**、 **Windows** (または**Visual Basic**、 **Windows**)。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-120">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0b5a-121">Visual Studio で第一言語として設定されているプログラミング言語に応じて、 **[インストール済み]** ノードの **[他の言語]** ノードの下に、 **[Visual C#]** ノードまたは **[Visual Basic]** ノードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-121">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="e0b5a-122">.NET Framework バージョンのドロップダウン リストで **[.NET Framework 4.5]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-122">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="e0b5a-123">選択**コンソール アプリケーション**から、 **Windows**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-123">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="e0b5a-124">型**CreateUpdateMaps**に、**名前**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-124">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="e0b5a-125">右クリック**CreateUpdateMaps**で**ソリューション エクスプ ローラー**選択**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-125">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="e0b5a-126">選択**Framework**から、**アセンブリ**内のノード、**参照の追加** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-126">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="e0b5a-127">型**System.Activities**に、**アセンブリの検索**ボックスをアセンブリをフィルター処理し、目的の参照を容易に選択します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-127">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>  
  
5.  <span data-ttu-id="e0b5a-128">横にあるチェック ボックスをオン**System.Activities**から、**検索結果** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-128">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
6.  <span data-ttu-id="e0b5a-129">型**シリアル化**に、**アセンブリの検索**ボックスし、チェック ボックスの横にある**System.Runtime.Serialization**から、**検索結果**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-129">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="e0b5a-130">型**System.Xaml**に、**アセンブリの検索**ボックスし、チェック ボックスの横にある**System.Xaml**から、**検索結果** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-130">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="e0b5a-131">をクリックして**OK**を閉じる**参照マネージャー**参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-131">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
9. <span data-ttu-id="e0b5a-132">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-132">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.Statements  
    Imports System.Xaml  
    Imports System.Reflection  
    Imports System.IO  
    Imports System.Activities.XamlIntegration  
    Imports System.Activities.DynamicUpdate  
    Imports System.Runtime.Serialization  
    Imports Microsoft.VisualBasic.Activities  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.IO;  
    using System.Xaml;  
    using System.Reflection;  
    using System.Activities.XamlIntegration;  
    using System.Activities.DynamicUpdate;  
    using System.Runtime.Serialization;  
    using Microsoft.CSharp.Activities;  
    ```  
  
10. <span data-ttu-id="e0b5a-133">`Program` クラス (または `Module1`) に次の 2 つの文字列メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-133">Add the following two string members to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const mapPath = "..\..\..\PreviousVersions"  
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"  
    ```  
  
    ```csharp  
    const string mapPath = @"..\..\..\PreviousVersions";  
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";  
    ```  
  
11. <span data-ttu-id="e0b5a-134">`StartUpdate` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-134">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e0b5a-135">このメソッドにより、指定した xaml ワークフロー定義が `ActivityBuilder` に読み込まれた後、`DynamicUpdate.PrepareForUpdate` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-135">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="e0b5a-136">`PrepareForUpdate` は `ActivityBuilder` 内にワークフロー定義のコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-136">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="e0b5a-137">ワークフロー定義が変更されると、更新マップを作成するように変更されたワークフロー定義と共に、このコピーは使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-137">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>  
  
    ```vb  
    Private Function StartUpdate(name As String) As ActivityBuilder  
        'Create the XamlXmlReaderSettings.  
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()  
        'In the XAML the "local" namespace referes to artifacts that come from   
        'the same project as the XAML. When loading XAML if the currently executing   
        'assembly is not the same assembly that was referred to as "local" in the XAML  
        'LocalAssembly must be set to the assembly containing the artifacts.  
        'Assembly.LoadFile requires an absolute path so convert this relative path  
        'to an absolute path.  
        readerSettings.LocalAssembly = Assembly.LoadFile(  
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))  
  
        Dim fullPath As String = Path.Combine(definitionPath, name)  
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)  
  
        'Load the workflow definition into an ActivityBuilder.  
        Dim wf As ActivityBuilder = XamlServices.Load(  
            ActivityXamlServices.CreateBuilderReader(xamlReader))  
  
        'PrepareForUpdate makes a copy of the workflow definition in the  
        'ActivityBuilder that is used for comparison when the update  
        'map is created.  
        DynamicUpdateServices.PrepareForUpdate(wf)  
  
        Return wf  
    End Function  
    ```  
  
    ```csharp  
    private static ActivityBuilder StartUpdate(string name)  
    {  
        // Create the XamlXmlReaderSettings.  
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()  
        {  
            // In the XAML the "local" namespace referes to artifacts that come from   
            // the same project as the XAML. When loading XAML if the currently executing   
            // assembly is not the same assembly that was referred to as "local" in the XAML  
            // LocalAssembly must be set to the assembly containing the artifacts.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            LocalAssembly = Assembly.LoadFile(  
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))  
        };  
  
        string path = Path.Combine(definitionPath, name);  
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);  
  
        // Load the workflow definition into an ActivityBuilder.  
        ActivityBuilder wf = XamlServices.Load(  
            ActivityXamlServices.CreateBuilderReader(xamlReader))  
            as ActivityBuilder;  
  
        // PrepareForUpdate makes a copy of the workflow definition in the  
        // ActivityBuilder that is used for comparison when the update  
        // map is created.  
        DynamicUpdateServices.PrepareForUpdate(wf);  
  
        return wf;  
    }  
    ```  
  
12. <span data-ttu-id="e0b5a-138">次に、`CreateUpdateMethod` クラス (または `Program`) に次の `Module1` を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-138">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e0b5a-139">これにより、DynamicUpdateServices.CreateUpdateMap が呼び出されて動的更新マップが作成され、指定した名前を使用してその更新マップが保存されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-139">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="e0b5a-140">この更新マップには、`ActivityBuilder` に格納されている元のワークフロー定義を使用して開始された、永続化されたワークフロー インスタンスが、更新されたワークフロー定義を使用して完了するよう更新するために、ワークフロー ランタイムで必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-140">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>  
  
    ```vb  
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)  
        'Create the UpdateMap.  
        Dim map As DynamicUpdateMap =  
            DynamicUpdateServices.CreateUpdateMap(wf)  
  
        'Serialize it to a file.  
        Dim mapFullPath As String = Path.Combine(mapPath, name)  
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))  
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)  
            sz.WriteObject(fs, map)  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)  
    {  
        // Create the UpdateMap.  
        DynamicUpdateMap map =  
            DynamicUpdateServices.CreateUpdateMap(wf);  
  
        // Serialize it to a file.  
        string path = Path.Combine(mapPath, name);  
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));  
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))  
        {  
            sz.WriteObject(fs, map);  
        }  
    }  
    ```  
  
13. <span data-ttu-id="e0b5a-141">`SaveUpdatedDefinition` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-141">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e0b5a-142">このメソッドは、更新マップが作成されると、更新されたワークフロー定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-142">This method saves the updated workflow definition once the update map is created.</span></span>  
  
    ```vb  
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)  
        Dim xamlPath As String = Path.Combine(definitionPath, name)  
        Dim sw As StreamWriter = File.CreateText(xamlPath)  
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(  
            New XamlXmlWriter(sw, New XamlSchemaContext()))  
        XamlServices.Save(xw, wf)  
        sw.Close()  
    End Sub  
    ```  
  
    ```csharp  
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)  
    {  
        string xamlPath = Path.Combine(definitionPath, name);  
        StreamWriter sw = File.CreateText(xamlPath);  
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(  
            new XamlXmlWriter(sw, new XamlSchemaContext()));  
        XamlServices.Save(xw, wf);  
        sw.Close();  
    }  
    ```  
  
###  <span data-ttu-id="e0b5a-143"><a name="BKMK_StateMachine"></a>StateMachineNumberGuessWorkflow を更新するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-143"><a name="BKMK_StateMachine"></a> To update StateMachineNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="e0b5a-144">`CreateStateMachineUpdateMap` クラス (または `Program`) に `Module1` を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-144">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {    
    }  
    ```  
  
2.  <span data-ttu-id="e0b5a-145">`StartUpdate` を呼び出し、ワークフローのルート `StateMachine` アクティビティへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-145">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>  
  
    ```vb  
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")  
  
    'Get a reference to the root StateMachine activity.  
    Dim sm As StateMachine = wf.Implementation  
    ```  
  
    ```csharp  
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");  
  
    // Get a reference to the root StateMachine activity.  
    StateMachine sm = wf.Implementation as StateMachine;  
    ```  
  
3.  <span data-ttu-id="e0b5a-146">2 つの式を次に、更新`WriteLine`に加えられた更新と一致するようにユーザーの推定値が大きすぎるか小さすぎるかどうかを表示するアクティビティ[する方法: 複数のバージョンをワークフロー サイド バイ サイドのホスト](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-146">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
    ```vb  
    'Update the Text of the two WriteLine activities that write the  
    'results of the user's guess. They are contained in the workflow as the  
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action  
  
    'Update the "too low" message.  
    Dim tooLow As WriteLine = guessLow.Then  
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
    'Update the "too high" message.  
    Dim tooHigh As WriteLine = guessLow.Else  
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
    ```  
  
    ```csharp  
    // Update the Text of the two WriteLine activities that write the  
    // results of the user's guess. They are contained in the workflow as the  
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
    If guessLow = sm.States[1].Transitions[1].Action as If;  
  
    // Update the "too low" message.  
    WriteLine tooLow = guessLow.Then as WriteLine;  
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
    // Update the "too high" message.  
    WriteLine tooHigh = guessLow.Else as WriteLine;  
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
    ```  
  
4.  <span data-ttu-id="e0b5a-147">終了メッセージを表示する新しい `WriteLine` アクティビティを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-147">Next, add the new `WriteLine` activity that displays the closing message.</span></span>  
  
    ```vb  
    'Create the new WriteLine that displays the closing message.  
    Dim wl As New WriteLine() With  
    {  
        .Text = New VisualBasicValue(Of String) _  
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
    }  
  
    'Add it as the Action for the Guess Correct transition. The Guess Correct  
    'transition is the first transition of States[1]. The transitions are listed  
    'at the bottom of the State activity designer.  
    sm.States(1).Transitions(0).Action = wl  
    ```  
  
    ```csharp  
    // Create the new WriteLine that displays the closing message.  
    WriteLine wl = new WriteLine  
    {  
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
    };  
  
    // Add it as the Action for the Guess Correct transition. The Guess Correct  
    // transition is the first transition of States[1]. The transitions are listed  
    // at the bottom of the State activity designer.  
    sm.States[1].Transitions[0].Action = wl;  
    ```  
  
5.  <span data-ttu-id="e0b5a-148">ワークフローを更新したら、`CreateUpdateMaps` と `SaveUpdatedDefinition` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-148">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="e0b5a-149">`CreateUpdateMaps` は `DynamicUpdateMap` を作成して保存し、`SaveUpdatedDefinition` は更新されたワークフロー定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-149">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>  
  
    ```vb  
    'Create the update map.  
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")  
  
    'Save the updated workflow definition.  
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")  
    ```  
  
    ```csharp  
    // Create the update map.  
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");  
  
    // Save the updated workflow definition.  
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");  
    ```  
  
     <span data-ttu-id="e0b5a-150">完成した `CreateStateMachineUpdateMap` メソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-150">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root StateMachine activity.  
        Dim sm As StateMachine = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action  
  
        'Update the "too low" message.  
        Dim tooLow As WriteLine = guessLow.Then  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
        'Update the "too high" message.  
        Dim tooHigh As WriteLine = guessLow.Else  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Add it as the Action for the Guess Correct transition. The Guess Correct  
        'transition is the first transition of States[1]. The transitions are listed  
        'at the bottom of the State activity designer.  
        sm.States(1).Transitions(0).Action = wl  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root StateMachine activity.  
        StateMachine sm = wf.Implementation as StateMachine;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
        If guessLow = sm.States[1].Transitions[1].Action as If;  
  
        // Update the "too low" message.  
        WriteLine tooLow = guessLow.Then as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
        // Update the "too high" message.  
        WriteLine tooHigh = guessLow.Else as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Create the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Add it as the Action for the Guess Correct transition. The Guess Correct  
        // transition is the first transition of States[1]. The transitions are listed  
        // at the bottom of the State activity designer.  
        sm.States[1].Transitions[0].Action = wl;  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");  
  
        // Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <span data-ttu-id="e0b5a-151"><a name="BKMK_Flowchart"></a>FlowchartNumberGuessWorkflow を更新するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-151"><a name="BKMK_Flowchart"></a> To update FlowchartNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="e0b5a-152">`CreateFlowchartUpdateMethod` クラス (または `Program`) に次の `Module1` を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-152">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e0b5a-153">このメソッドは `CreateStateMachineUpdateMap` に似ています。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-153">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="e0b5a-154">最初に `StartUpdate` を呼び出し、フローチャート ワークフロー定義を更新して、最後に更新マップおよび更新されたワークフロー定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-154">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
    ```vb  
    Private Sub CreateFlowchartUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root Flowchart activity.  
        Dim fc As Flowchart = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'True and False action of the "Guess < Target" FlowDecision, which is  
        'Nodes[4].  
        Dim guessLow As FlowDecision = fc.Nodes(4)  
  
        'Update the "too low" message.  
        Dim trueStep As FlowStep = guessLow.True  
        Dim tooLow As WriteLine = trueStep.Action  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
        'Update the "too high" message.  
        Dim falseStep As FlowStep = guessLow.False  
        Dim tooHigh As WriteLine = falseStep.Action  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Create a FlowStep to hold the WriteLine.  
        Dim closingStep As New FlowStep() With  
        {  
            .Action = wl  
        }  
  
        'Add this new FlowStep to the True action of the   
        '"Guess = Guess" FlowDecision  
        Dim guessCorrect As FlowDecision = fc.Nodes(3)  
        guessCorrect.True = closingStep  
  
        'Add the new FlowStep to the Nodes collection.  
        'If closingStep was replacing an existing node then  
        'we would need to remove that Step from the collection.  
        'In this example there was no existing True step to remove.  
        fc.Nodes.Add(closingStep)  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateFlowchartUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root Flowchart activity.  
        Flowchart fc = wf.Implementation as Flowchart;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // True and False action of the "Guess < Target" FlowDecision, which is  
        // Nodes[4].  
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;  
  
        // Update the "too low" message.  
        FlowStep trueStep = guessLow.True as FlowStep;  
        WriteLine tooLow = trueStep.Action as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
        // Update the "too high" message.  
        FlowStep falseStep = guessLow.False as FlowStep;  
        WriteLine tooHigh = falseStep.Action as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Add the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Create a FlowStep to hold the WriteLine.  
        FlowStep closingStep = new FlowStep  
        {  
            Action = wl  
        };  
  
        // Add this new FlowStep to the True action of the   
        // "Guess == Guess" FlowDecision  
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;  
        guessCorrect.True = closingStep;  
  
        // Add the new FlowStep to the Nodes collection.  
        // If closingStep was replacing an existing node then  
        // we would need to remove that Step from the collection.  
        // In this example there was no existing True step to remove.  
        fc.Nodes.Add(closingStep);  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");  
  
        //  Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <span data-ttu-id="e0b5a-155"><a name="BKMK_Sequential"></a>SequentialNumberGuessWorkflow を更新するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-155"><a name="BKMK_Sequential"></a> To update SequentialNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="e0b5a-156">`CreateSequentialUpdateMethod` クラス (または `Program`) に次の `Module1` を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-156">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e0b5a-157">このメソッドは、他の 2 つのメソッドに似ています。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-157">This method is similar to the other two methods.</span></span> <span data-ttu-id="e0b5a-158">最初に `StartUpdate` を呼び出し、シーケンシャル ワークフロー定義を更新して、最後に更新マップおよび更新されたワークフロー定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-158">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
    ```vb  
    Private Sub CreateSequentialUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root activity in the workflow.  
        Dim rootSequence As Sequence = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'Then and Else action of the "Guess < Target" If activity.  
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If  
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)  
        Dim gameBody As Sequence = gameLoop.Body  
        Dim guessCorrect As Statements.If = gameBody.Activities(2)  
        Dim guessLow As Statements.If = guessCorrect.Then  
        Dim tooLow As WriteLine = guessLow.Then  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
        Dim tooHigh As WriteLine = guessLow.Else  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Insert it as the third activity in the root sequence  
        rootSequence.Activities.Insert(2, wl)  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateSequentialUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root activity in the workflow.  
        Sequence rootSequence = wf.Implementation as Sequence;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // Then and Else action of the "Guess < Target" If activity.  
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If  
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;  
        Sequence gameBody = gameLoop.Body as Sequence;  
        If guessCorrect = gameBody.Activities[2] as If;  
        If guessLow = guessCorrect.Then as If;  
        WriteLine tooLow = guessLow.Then as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
        WriteLine tooHigh = guessLow.Else as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Add the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Insert it as the third activity in the root sequence  
        rootSequence.Activities.Insert(2, wl);  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");  
  
        // Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <span data-ttu-id="e0b5a-159"><a name="BKMK_CreateUpdateMaps"></a>CreateUpdateMaps アプリケーションをビルドして、実行</span><span class="sxs-lookup"><span data-stu-id="e0b5a-159"><a name="BKMK_CreateUpdateMaps"></a> To build and run the CreateUpdateMaps application</span></span>  
  
1.  <span data-ttu-id="e0b5a-160">`Main` メソッドを更新し、次の 3 つのメソッド呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-160">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="e0b5a-161">これらのメソッドは次のセクションで追加されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-161">These methods are added in the following sections.</span></span> <span data-ttu-id="e0b5a-162">各メソッドは、対応する数値推測ワークフローを更新し、更新内容を示す `DynamicUpdateMap` を作成します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-162">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>  
  
    ```vb  
    Sub Main()  
        'Create the update maps for the changes needed to the v1 activities  
        'so they match the v2 activities.  
        CreateSequentialUpdateMap()  
        CreateFlowchartUpdateMap()  
        CreateStateMachineUpdateMap()  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the update maps for the changes needed to the v1 activities  
        // so they match the v2 activities.  
        CreateSequentialUpdateMap();  
        CreateFlowchartUpdateMap();  
        CreateStateMachineUpdateMap();  
    }  
    ```  
  
2.  <span data-ttu-id="e0b5a-163">右クリック**CreateUpdateMaps**で**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-163">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
3.  <span data-ttu-id="e0b5a-164">Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押して `CreateUpdateMaps` アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-164">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0b5a-165">`CreateUpdateMaps`確認する場合は、実行中にステータス情報がアプリケーションに表示されません、 **NumberGuessWorkflowActivities_du**フォルダーおよび**PreviousVersions**フォルダーが表示されます更新されたワークフロー定義ファイルおよびマップを更新します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-165">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>  
  
     <span data-ttu-id="e0b5a-166">更新マップが作成され、ワークフロー定義が更新されたら、次に、更新された定義を含む更新されたワークフロー アセンブリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-166">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>  
  
###  <span data-ttu-id="e0b5a-167"><a name="BKMK_BuildAssembly"></a>更新されたワークフロー アセンブリをビルドするには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-167"><a name="BKMK_BuildAssembly"></a> To build the updated workflow assembly</span></span>  
  
1.  <span data-ttu-id="e0b5a-168">[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] の別のインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-168">Open a second instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="e0b5a-169">選択**開く**、**プロジェクト/ソリューション**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-169">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>  
  
3.  <span data-ttu-id="e0b5a-170">移動し、 **NumberGuessWorkflowActivities_du**で作成したフォルダー[する方法: ホストはワークフロー サイド バイ サイドの複数のバージョン](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) **NumberGuessWorkflowActivities.csproj** (または**vbproj**)、をクリックして**開く**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-170">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>  
  
4.  <span data-ttu-id="e0b5a-171">**ソリューション エクスプ ローラー**を右クリックして**SequentialNumberGuessWorkflow.xaml**選択**プロジェクトから除外**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-171">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="e0b5a-172">同じ操作を行う**FlowchartNumberGuessWorkflow.xaml**と**StateMachineNumberGuessWorkflow.xaml**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-172">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="e0b5a-173">この手順により、以前のバージョンのワークフロー定義がプロジェクトから削除されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-173">This step removes the previous versions of the workflow definitions from the project.</span></span>  
  
5.  <span data-ttu-id="e0b5a-174">選択**既存項目の追加**から、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-174">Choose **Add Existing Item** from the **Project** menu.</span></span>  
  
6.  <span data-ttu-id="e0b5a-175">移動、 **NumberGuessWorkflowActivities_du**で作成したフォルダー[する方法: 複数のバージョンのホストはワークフロー サイド バイ サイドの](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-175">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
7.  <span data-ttu-id="e0b5a-176">選択**XAML ファイル (\*.xaml;\*です。xoml)**から、**ファイルの種類**ドロップダウン リスト。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-176">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>  
  
8.  <span data-ttu-id="e0b5a-177">選択**SequentialNumberGuessWorkflow_du.xaml**、 **FlowchartNumberGuessWorkflow_du.xaml**、および**StateMachineNumberGuessWorkflow_du.xaml** をクリック**追加**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-177">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0b5a-178">複数の項目を同時に選択するには、Ctrl を押しながら各項目をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-178">CTRL+Click to select multiple items at a time.</span></span>  
  
     <span data-ttu-id="e0b5a-179">この手順により、更新されたワークフロー定義がプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-179">This step adds the updated versions of the workflow definitions to the project.</span></span>  
  
9. <span data-ttu-id="e0b5a-180">Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-180">Press CTRL+SHIFT+B to build the project.</span></span>  
  
10. <span data-ttu-id="e0b5a-181">選択**ソリューションを閉じる**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-181">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="e0b5a-182">ソリューション ファイルのプロジェクトが必要ですが、これをクリックして**いいえ**を閉じる[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]ソリューション ファイルを保存せずします。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-182">A solution file for the project is not required, so click **No** to close [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] without saving a solution file.</span></span> <span data-ttu-id="e0b5a-183">選択**終了**から、**ファイル**メニューを閉じます[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-183">Choose **Exit** from the **File** menu to close [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)].</span></span>  
  
11. <span data-ttu-id="e0b5a-184">Windows エクスプ ローラーを開きに移動、 **numberguessworkflowactivities_du \bin\debug**フォルダー (または**bin \release**プロジェクトの設定によって)。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-184">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>  
  
12. <span data-ttu-id="e0b5a-185">名前を変更**NumberGuessWorkflowActivities.dll**に**NumberGuessWorkflowActivities_v15.dll**にコピーし、 **PreviousVersions** で作成したフォルダー[する方法: ホストの複数のバージョン、ワークフロー サイド バイ サイドの](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-185">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
###  <span data-ttu-id="e0b5a-186"><a name="BKMK_UpdateWorkflowVersionMap"></a>新しいバージョンで WorkflowVersionMap を更新するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-186"><a name="BKMK_UpdateWorkflowVersionMap"></a> To update WorkflowVersionMap with the new versions</span></span>  
  
1.  <span data-ttu-id="e0b5a-187">[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] の最初のインスタンスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-187">Switch back to the initial instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="e0b5a-188">ダブルクリックして**WorkflowVersionMap.cs** (または**WorkflowVersionMap.vb**) 下にある、 **NumberGuessWorkflowHost**プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-188">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
3.  <span data-ttu-id="e0b5a-189">既存の 6 つのワークフロー ID 宣言の直後に、新しいワークフロー ID を 3 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-189">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="e0b5a-190">このチュートリアルでは、`1.5.0.0` は動的更新 ID の `WorkflowIdentity.Version` として使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-190">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="e0b5a-191">これらの新しい `v15` ワークフロー ID は、動的に更新される永続化されたワークフロー インスタンスに適切なワークフロー定義を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-191">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
    'v1.5 (Dynamimc Update) identities.  
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity  
    ```  
  
    ```csharp  
    // Current version identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity;  
    static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
    // v1 identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
  
    // v1.5 (Dynamic Update) identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;  
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;  
    ```  
  
4.  <span data-ttu-id="e0b5a-192">コンストラクターの末尾に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-192">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="e0b5a-193">このコードでは、動的更新ワークフロー ID を初期化し、対応するワークフロー定義を読み込み、これらをワークフロー バージョン ディクショナリに追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-193">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>  
  
    ```vb  
    'Initialize the dynamic update workflow identities.  
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "StateMachineNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "FlowchartNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "SequentialNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    'Add the dynamic update workflow identities to the dictionary along with  
    'the corresponding workflow definitions loaded from the v15 assembly.  
    'Assembly.LoadFile requires an absolute path so convert this relative path  
    'to an absolute path.  
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"  
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)  
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)  
  
    map.Add(StateMachineNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
    map.Add(SequentialNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
    map.Add(FlowchartNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
    ```  
  
    ```csharp  
    // Initialize the dynamic update workflow identities.  
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "StateMachineNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "FlowchartNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "SequentialNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    // Add the dynamic update workflow identities to the dictionary along with  
    // the corresponding workflow definitions loaded from the v15 assembly.  
    // Assembly.LoadFile requires an absolute path so convert this relative path  
    // to an absolute path.  
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";  
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);  
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);  
  
    map.Add(StateMachineNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
    map.Add(SequentialNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
    map.Add(FlowchartNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
    ```  
  
     <span data-ttu-id="e0b5a-194">完成した `WorkflowVersionMap` クラスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-194">The following example is the completed `WorkflowVersionMap` class.</span></span>  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        'v1 identities.  
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
        'v1.5 (Dynamimc Update) identities.  
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
  
            'Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            'Add the previous version workflow identities to the dictionary along with  
            'the corresponding workflow definitions loaded from the v1 assembly.  
            'Assembly.LoadFile requires an absolute path so convert this relative path  
            'to an absolute path.  
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)  
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
  
            'Initialize the dynamic update workflow identities.  
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            'Add the dynamic update workflow identities to the dictionary along with  
            'the corresponding workflow definitions loaded from the v15 assembly.  
            'Assembly.LoadFile requires an absolute path so convert this relative path  
            'to an absolute path.  
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"  
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)  
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)  
  
            map.Add(StateMachineNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
            map.Add(SequentialNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
            map.Add(FlowchartNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        // v1 identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
  
        // v1.5 (Dynamic Update) identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;  
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
  
            // Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            // Add the previous version workflow identities to the dictionary along with  
            // the corresponding workflow definitions loaded from the v1 assembly.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);  
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
  
            // Initialize the dynamic update workflow identities.  
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            // Add the dynamic update workflow identities to the dictionary along with  
            // the corresponding workflow definitions loaded from the v15 assembly.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";  
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);  
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);  
  
            map.Add(StateMachineNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
            map.Add(SequentialNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
            map.Add(FlowchartNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {  
            return identity.ToString();  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="e0b5a-195">Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-195">Press CTRL+SHIFT+B to build the project.</span></span>  
  
###  <span data-ttu-id="e0b5a-196"><a name="BKMK_ApplyUpdate"></a>動的更新を適用するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-196"><a name="BKMK_ApplyUpdate"></a> To apply the dynamic updates</span></span>  
  
1.  <span data-ttu-id="e0b5a-197">右クリック**WF45GettingStartedTutorial**で**ソリューション エクスプ ローラー**選択**追加**、**新しいプロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-197">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="e0b5a-198">**インストール**ノード、 **Visual c#**、 **Windows** (または**Visual Basic**、 **Windows**)。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-198">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0b5a-199">Visual Studio で第一言語として設定されているプログラミング言語に応じて、 **[インストール済み]** ノードの **[他の言語]** ノードの下に、 **[Visual C#]** ノードまたは **[Visual Basic]** ノードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-199">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="e0b5a-200">.NET Framework バージョンのドロップダウン リストで **[.NET Framework 4.5]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-200">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="e0b5a-201">選択**コンソール アプリケーション**から、 **Windows**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-201">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="e0b5a-202">型**ApplyDynamicUpdate**に、**名前**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-202">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="e0b5a-203">右クリック**ApplyDynamicUpdate**で**ソリューション エクスプ ローラー**選択**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-203">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="e0b5a-204">をクリックして**ソリューション**、このチェック ボックスを横に**NumberGuessWorkflowHost**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-204">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="e0b5a-205">この参照は、`ApplyDynamicUpdate` で `NumberGuessWorkflowHost.WorkflowVersionMap` クラスを使用できるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-205">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>  
  
5.  <span data-ttu-id="e0b5a-206">選択**Framework**から、**アセンブリ**内のノード、**参照の追加** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-206">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="e0b5a-207">型**System.Activities**に、**アセンブリの検索**ボックス。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-207">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="e0b5a-208">これにより、アセンブリがフィルター処理され、目的の参照が選択しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-208">This will filter the assemblies and make the desired references easier to select.</span></span>  
  
6.  <span data-ttu-id="e0b5a-209">横にあるチェック ボックスをオン**System.Activities**から、**検索結果** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-209">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="e0b5a-210">型**シリアル化**に、**アセンブリの検索**ボックスし、チェック ボックスの横にある**System.Runtime.Serialization**から、**検索結果**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-210">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="e0b5a-211">型**DurableInstancing**に、**アセンブリの検索**ボックスし、チェック ボックスの横にある**お**と**System.Runtime.DurableInstancing**から、**検索結果** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-211">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>  
  
9. <span data-ttu-id="e0b5a-212">をクリックして**OK**を閉じる**参照マネージャー**参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-212">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
10. <span data-ttu-id="e0b5a-213">右クリック**ApplyDynamicUpdate**ソリューション エクスプ ローラーで選択および**追加**、**クラス**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-213">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="e0b5a-214">型`DynamicUpdateInfo`に、**名前**ボックスし、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-214">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>  
  
11. <span data-ttu-id="e0b5a-215">`DynamicUpdateInfo` クラスに次の 2 つのメンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-215">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="e0b5a-216">完成した `DynamicUpdateInfo` クラスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-216">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="e0b5a-217">このクラスには、ワークフロー インスタンスの更新時に使用された更新マップと新しいワークフロー ID に関する情報が格納されています。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-217">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>  
  
    ```vb  
    Public Class DynamicUpdateInfo  
        Public updateMap As DynamicUpdateMap  
        Public newIdentity As WorkflowIdentity  
    End Class  
    ```  
  
    ```csharp  
    class DynamicUpdateInfo  
    {  
        public DynamicUpdateMap updateMap;  
        public WorkflowIdentity newIdentity;  
    }  
    ```  
  
12. <span data-ttu-id="e0b5a-218">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.DynamicUpdate  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    ```  
  
13. <span data-ttu-id="e0b5a-219">ダブルクリックして**Program.cs** (または**Module1.vb**) ソリューション エクスプ ローラーでします。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-219">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>  
  
14. <span data-ttu-id="e0b5a-220">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-220">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowHost  
    Imports System.Data.SqlClient  
    Imports System.Activities.DynamicUpdate  
    Imports System.IO  
    Imports System.Runtime.Serialization  
    Imports System.Activities  
    Imports System.Activities.DurableInstancing  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowHost;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    using System.IO;  
    using System.Runtime.Serialization;  
    using System.Activities.DurableInstancing;  
    ```  
  
15. <span data-ttu-id="e0b5a-221">`Program` クラス (または `Module1`) に次の接続文字列メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-221">Add the following connection string member to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e0b5a-222">使用している SQL Server のエディションによって、接続文字列のサーバー名は異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-222">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
16. <span data-ttu-id="e0b5a-223">`GetIDs` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-223">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e0b5a-224">このメソッドは、永続化されたワークフロー インスタンス ID の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-224">This method returns a list of persisted workflow instance ids.</span></span>  
  
    ```vb  
    Function GetIds() As IList(Of Guid)  
        Dim Ids As New List(Of Guid)  
        Dim localCmd = _  
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")  
        Using localCon = New SqlConnection(connectionString)  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
                While reader.Read()  
                    'Get the InstanceId of the persisted Workflow  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
  
                    'Add it to the list.  
                    Ids.Add(id)  
                End While  
            End Using  
        End Using  
  
        Return Ids  
    End Function  
    ```  
  
    ```csharp  
    static IList<Guid> GetIds()  
    {  
        List<Guid> Ids = new List<Guid>();  
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");  
        using (SqlConnection localCon = new SqlConnection(connectionString))  
        {  
            SqlCommand cmd = localCon.CreateCommand();  
            cmd.CommandText = localCmd;  
            localCon.Open();  
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
            {  
                while (reader.Read())  
                {  
                    // Get the InstanceId of the persisted Workflow  
                    Guid id = Guid.Parse(reader[0].ToString());  
  
                    // Add it to the list.  
                    Ids.Add(id);  
                }  
            }  
        }  
  
        return Ids;  
    }  
    ```  
  
17. <span data-ttu-id="e0b5a-225">`LoadMap` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-225">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e0b5a-226">このメソッドは、更新マップに `v1` ワークフロー ID をマップするディクショナリと、対応する永続化されたワークフロー インスタンスの更新に使用される新しいワークフロー ID を作成します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-226">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>  
  
    ```vb  
    Function LoadMap(mapName As String) As DynamicUpdateMap  
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)  
  
        Dim map As DynamicUpdateMap  
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)  
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))  
            Dim updateMap = serializer.ReadObject(fs)  
            If updateMap Is Nothing Then  
                Throw New ApplicationException("DynamicUpdateMap is null.")  
            End If  
  
            map = updateMap  
        End Using  
  
        Return map  
    End Function  
    ```  
  
    ```csharp  
    static DynamicUpdateMap LoadMap(string mapName)  
    {  
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);  
  
        DynamicUpdateMap map;  
        using (FileStream fs = File.Open(path, FileMode.Open))  
        {  
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
            object updateMap = serializer.ReadObject(fs);  
            if (updateMap == null)  
            {  
                throw new ApplicationException("DynamicUpdateMap is null.");  
            }  
  
            map = updateMap as DynamicUpdateMap;  
        }  
  
        return map;  
    }  
    ```  
  
18. <span data-ttu-id="e0b5a-227">`LoadMaps` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-227">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e0b5a-228">このメソッドは、3 つの更新マップを読み込み、更新マップに `v1` ワークフロー ID をマップするディクショナリを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-228">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>  
  
    ```vb  
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)  
        'There are 3 update maps to describe the changes to update v1 workflows,  
        'one for reach of the 3 workflow types in the tutorial.  
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()  
  
        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")  
        Dim sequentialInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = sequentialMap,  
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)  
  
        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")  
        Dim stateInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = stateMap,  
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)  
  
        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")  
        Dim flowchartInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = flowchartMap,  
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)  
  
        Return maps  
    End Function  
    ```  
  
    ```csharp  
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()  
    {  
        // There are 3 update maps to describe the changes to update v1 workflows,  
        // one for reach of the 3 workflow types in the tutorial.  
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =  
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();  
  
        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");  
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo  
        {  
            updateMap = sequentialMap,  
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);  
  
        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");  
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo  
        {  
            updateMap = stateMap,  
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);  
  
        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");  
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo  
        {  
            updateMap = flowchartMap,  
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);  
  
        return maps;              
    }  
    ```  
  
19. <span data-ttu-id="e0b5a-229">`Main` に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-229">Add the following code to `Main`.</span></span> <span data-ttu-id="e0b5a-230">このコードでは、永続化されたワークフロー インスタンスを反復処理し、それぞれの `WorkflowIdentity` を調べます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-230">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="e0b5a-231">`WorkflowIdentity` が `v1` ワークフロー インスタンスにマップされると、`WorkflowApplication` は、更新されたワークフロー定義と更新されたワークフロー ID を使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-231">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="e0b5a-232">次に、`WorkflowApplication.Load` がそのインスタンスと更新マップを使用して呼び出され、動的更新マップが適用されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-232">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="e0b5a-233">更新が適用されると、更新されたインスタンスは `Unload` の呼び出しによって永続化されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-233">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>  
  
    ```vb  
    Dim store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()  
  
    For Each id As Guid In GetIds()  
        'Get a proxy to the instance.   
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)  
  
        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)  
  
        'Only update v1 workflows.  
        If Not instance.DefinitionIdentity Is Nothing AndAlso _  
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then  
  
            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)  
  
            'Associate the persisted WorkflowApplicationInstance with  
            'a WorkflowApplication that is configured with the updated  
            'definition and updated WorkflowIdentity.  
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)  
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)  
  
            'Apply the Dynamic Update.               
            wfApp.Load(instance, info.updateMap)  
  
            'Persist the updated instance.  
            wfApp.Unload()  
  
            Console.WriteLine("Updated to: {0}", info.newIdentity)  
        Else  
            'Not updating this instance, so unload it.  
            instance.Abandon()  
        End If  
    Next  
    ```  
  
    ```csharp  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();  
  
    foreach (Guid id in GetIds())  
    {  
        // Get a proxy to the instance.   
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(id, store);  
  
        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);  
  
        // Only update v1 workflows.  
        if (instance.DefinitionIdentity != null &&  
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))  
        {  
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];  
  
            // Associate the persisted WorkflowApplicationInstance with  
            // a WorkflowApplication that is configured with the updated  
            // definition and updated WorkflowIdentity.  
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);  
            WorkflowApplication wfApp =  
                new WorkflowApplication(wf, info.newIdentity);  
  
            // Apply the Dynamic Update.               
            wfApp.Load(instance, info.updateMap);  
  
            // Persist the updated instance.  
            wfApp.Unload();  
  
            Console.WriteLine("Updated to: {0}", info.newIdentity);  
        }  
        else  
        {  
            // Not updating this instance, so unload it.  
            instance.Abandon();  
        }  
    }  
    ```  
  
20. <span data-ttu-id="e0b5a-234">右クリック**ApplyDynamicUpdate**で**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-234">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
21. <span data-ttu-id="e0b5a-235">Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押して `ApplyDynamicUpdate` アプリケーションを実行して、永続化されたワークフロー インスタンスを更新します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-235">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="e0b5a-236">表示される出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-236">You should see output similar to the following.</span></span> <span data-ttu-id="e0b5a-237">バージョン 1.0.0.0 のワークフローはバージョン 1.5.0.0 に更新されますが、バージョン 2.0.0.0 のワークフローは更新されません。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-237">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>  
  
 <span data-ttu-id="e0b5a-238">**StateMachineNumberGuessWorkflow の検査: です。バージョン 1.0.0.0 を =**</span><span class="sxs-lookup"><span data-stu-id="e0b5a-238">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>  
<span data-ttu-id="e0b5a-239">**よう更新されました: StateMachineNumberGuessWorkflow です。バージョン 1.5.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-239">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e0b5a-240">**StateMachineNumberGuessWorkflow の検査: です。バージョン 1.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-240">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-241">**よう更新されました: StateMachineNumberGuessWorkflow です。バージョン 1.5.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-241">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e0b5a-242">**FlowchartNumberGuessWorkflow の検査: です。バージョン 1.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-242">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-243">**よう更新されました: FlowchartNumberGuessWorkflow です。バージョン 1.5.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-243">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e0b5a-244">**FlowchartNumberGuessWorkflow の検査: です。バージョン 1.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-244">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-245">**よう更新されました: FlowchartNumberGuessWorkflow です。バージョン 1.5.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-245">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e0b5a-246">**SequentialNumberGuessWorkflow の検査: です。バージョン 1.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-246">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-247">**よう更新されました: SequentialNumberGuessWorkflow です。バージョン 1.5.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-247">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e0b5a-248">**SequentialNumberGuessWorkflow の検査: です。バージョン 1.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-248">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-249">**よう更新されました: SequentialNumberGuessWorkflow です。バージョン 1.5.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-249">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e0b5a-250">**SequentialNumberGuessWorkflow の検査: です。バージョン 1.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-250">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-251">**よう更新されました: SequentialNumberGuessWorkflow です。バージョン 1.5.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-251">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e0b5a-252">**StateMachineNumberGuessWorkflow の検査: です。バージョン 1.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-252">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-253">**よう更新されました: StateMachineNumberGuessWorkflow です。バージョン 1.5.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-253">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e0b5a-254">**FlowchartNumberGuessWorkflow の検査: です。バージョン 1.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-254">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-255">**よう更新されました: FlowchartNumberGuessWorkflow です。バージョン 1.5.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-255">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e0b5a-256">**StateMachineNumberGuessWorkflow の検査: です。バージョン 2.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-257">**StateMachineNumberGuessWorkflow の検査: です。バージョン 2.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-257">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-258">**FlowchartNumberGuessWorkflow の検査: です。バージョン 2.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-259">**FlowchartNumberGuessWorkflow の検査: です。バージョン 2.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-259">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-260">**SequentialNumberGuessWorkflow の検査: です。バージョン 2.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-261">**SequentialNumberGuessWorkflow の検査: です。バージョン 2.0.0.0 を =** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-261">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e0b5a-262">**任意のキーを押して続行してください.**</span><span class="sxs-lookup"><span data-stu-id="e0b5a-262">**Press any key to continue . . .**</span></span>  
  
###  <span data-ttu-id="e0b5a-263"><a name="BKMK_BuildAndRun"></a>更新されたワークフローを含むアプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-263"><a name="BKMK_BuildAndRun"></a> To run the application with the updated workflows</span></span>  
  
1.  <span data-ttu-id="e0b5a-264">右クリック**NumberGuessWorkflowHost**で**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-264">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="e0b5a-265">Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-265">Press CTRL+F5 to run the application.</span></span>  
  
3.  <span data-ttu-id="e0b5a-266">をクリックして**新しいゲーム**を新しいワークフローを開始し、以下のバージョン情報は、ワークフローを示すステータス ウィンドウに注意してください、`v2`ワークフローです。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-266">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>  
  
4.  <span data-ttu-id="e0b5a-267">いずれかを選択、`v1`の先頭から開始されたワークフロー、[する方法: 複数のバージョンのホストはワークフロー サイド バイ サイドの](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-267">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="e0b5a-268">ステータス ウィンドウの下のバージョン情報が、ワークフローのバージョンであることを示すことに注意してください**1.5.0.0**ワークフローです。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-268">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="e0b5a-269">前の推定値については、その値が大きすぎるか小さすぎるかという点以外の情報はありません。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-269">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>  
  
 <span data-ttu-id="e0b5a-270">**1 ~ 10 の間の数値を入力してください。**</span><span class="sxs-lookup"><span data-stu-id="e0b5a-270">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e0b5a-271">**推定値が小さすぎます。**</span><span class="sxs-lookup"><span data-stu-id="e0b5a-271">**Your guess is too low.**</span></span>  
  
5.  <span data-ttu-id="e0b5a-272">`InstanceId` を書き留めておき、ワークフローが完了するまで推定値を入力します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-272">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="e0b5a-273">ステータス ウィンドウには、`WriteLine` アクティビティが動的更新によって更新されたため、推測の内容に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-273">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>  
  
 <span data-ttu-id="e0b5a-274">**1 ~ 10 の間の数値を入力してください。**</span><span class="sxs-lookup"><span data-stu-id="e0b5a-274">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e0b5a-275">**推定値が小さすぎます。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-275">**Your guess is too low.** </span></span>  
<span data-ttu-id="e0b5a-276">**1 ~ 10 の間の数値を入力してください。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-276">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e0b5a-277">**5 が小さすぎます。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-277">**5 is too low.** </span></span>  
<span data-ttu-id="e0b5a-278">**1 ~ 10 の間の数値を入力してください。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-278">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e0b5a-279">**7 が高すぎます。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-279">**7 is too high.** </span></span>  
<span data-ttu-id="e0b5a-280">**1 ~ 10 の間の数値を入力してください。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-280">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e0b5a-281">**これで 4 交替で数値を推測します。**</span><span class="sxs-lookup"><span data-stu-id="e0b5a-281">**Congratulations, you guessed the number in 4 turns.**</span></span>  
  
6.  <span data-ttu-id="e0b5a-282">Windows エクスプ ローラーを開きに移動、 **numberguessworkflowhost \bin\debug**フォルダー (または**bin \release**プロジェクトの設定によって) し、対応するメモ帳を使用して追跡ファイルを開く完了したワークフローです。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-282">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="e0b5a-283">メモ行っていない場合、`InstanceId`を使用して正しい追跡ファイルを識別できる場合があります、**に変更された日付**Windows エクスプ ローラー内の情報です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-283">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="e0b5a-284">追跡情報の最後の行には、新しく追加した `WriteLine` アクティビティの出力が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-284">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>  
  
 <span data-ttu-id="e0b5a-285">**1 ~ 10 の間の数値を入力してください。**</span><span class="sxs-lookup"><span data-stu-id="e0b5a-285">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e0b5a-286">**推定値が小さすぎます。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-286">**Your guess is too low.** </span></span>  
<span data-ttu-id="e0b5a-287">**1 ~ 10 の間の数値を入力してください。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-287">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e0b5a-288">**5 が小さすぎます。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-288">**5 is too low.** </span></span>  
<span data-ttu-id="e0b5a-289">**1 ~ 10 の間の数値を入力してください。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-289">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e0b5a-290">**7 が高すぎます。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-290">**7 is too high.** </span></span>  
<span data-ttu-id="e0b5a-291">**1 ~ 10 の間の数値を入力してください。** </span><span class="sxs-lookup"><span data-stu-id="e0b5a-291">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e0b5a-292">**6 は正しいです。4 のターンのようにします。**</span><span class="sxs-lookup"><span data-stu-id="e0b5a-292">**6 is correct. You guessed it in 4 turns.**</span></span>  
  
###  <span data-ttu-id="e0b5a-293"><a name="BKMK_StartPreviousVersions"></a>ワークフローの以前のバージョンを開始できるようにするには</span><span class="sxs-lookup"><span data-stu-id="e0b5a-293"><a name="BKMK_StartPreviousVersions"></a> To enable starting previous versions of the workflows</span></span>  
 <span data-ttu-id="e0b5a-294">更新するワークフローがなくなったら、ワークフローの以前のバージョンを開始できるように `NumberGuessWorkflowHost` アプリケーションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-294">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>  
  
1.  <span data-ttu-id="e0b5a-295">ダブルクリックして**WorkflowHostForm**で**ソリューション エクスプ ローラー**を選択し、 **WorkflowType**コンボ ボックス。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-295">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>  
  
2.  <span data-ttu-id="e0b5a-296">**プロパティ**ウィンドウで、**項目**プロパティと、省略記号が編集するボタンをクリックして、**項目**コレクション。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-296">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>  
  
3.  <span data-ttu-id="e0b5a-297">コレクションに次の 3 つの項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-297">Add the following three items to the collection.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
     <span data-ttu-id="e0b5a-298">完成した `Items` コレクションには 6 個の項目があります。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-298">The completed `Items` collection will have six items.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow  
    FlowchartNumberGuessWorkflow  
    SequentialNumberGuessWorkflow  
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
4.  <span data-ttu-id="e0b5a-299">ダブルクリックして**WorkflowHostForm**で**ソリューション エクスプ ローラー**を選択して**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-299">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="e0b5a-300">次の 3 つの新しいケースを追加、 `switch` (または`Select Case`) 内のステートメント、`NewGame_Click`ハンドラーの新しい項目をマップする、 **WorkflowType**ワークフロー id を照合するコンボ ボックス。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-300">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>  
  
    ```vb  
    Case "SequentialNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1  
  
    Case "StateMachineNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1  
  
    Case "FlowchartNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1  
    ```  
  
    ```csharp  
    case "SequentialNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;  
        break;  
  
    case "StateMachineNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;  
        break;  
  
    case "FlowchartNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;  
        break;  
    ```  
  
     <span data-ttu-id="e0b5a-301">完成した `switch` (または `Select Case`) ステートメントを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-301">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>  
  
    ```vb  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
  
        Case "SequentialNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1  
  
        Case "StateMachineNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1  
  
        Case "FlowchartNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1  
    End Select  
    ```  
  
    ```csharp  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
  
        case "SequentialNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;  
            break;  
  
        case "StateMachineNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;  
            break;  
  
        case "FlowchartNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;  
            break;  
    };  
    ```  
  
6.  <span data-ttu-id="e0b5a-302">Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-302">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="e0b5a-303">これで、ワークフローの現在のバージョンに加え、`v1` バージョンを開始できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-303">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="e0b5a-304">これらの新しいインスタンスを動的に更新するには、実行、 **ApplyDynamicUpdate**アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="e0b5a-304">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>
