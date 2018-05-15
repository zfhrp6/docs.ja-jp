---
title: 'チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
ms.openlocfilehash: b87c46b2182884f90b427498b9af696d14acac96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="f4e76-102">チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f4e76-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="f4e76-103">カスタム コントロールを作成するときに、多くの場合、必要な場合が、デザイン時の動作をデバッグします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="f4e76-104">これは、カスタム コントロールのカスタム デザイナーを作成している場合に特に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="f4e76-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="f4e76-105">詳細については、「[チュートリアル:、Windows フォーム コントロール利用の Visual Studio デザイン時の機能を作成する](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="f4e76-106">他の .NET Framework クラスをデバッグする場合と同様に、Visual Studio を使用して、カスタム コントロールをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="f4e76-107">違いは、カスタム コントロールのコードを実行している Visual Studio の別のインスタンスをデバッグすることです。</span><span class="sxs-lookup"><span data-stu-id="f4e76-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="f4e76-108">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="f4e76-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="f4e76-109">カスタム コントロールをホストする Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="f4e76-110">コントロール ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="f4e76-111">カスタム コントロールにプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="f4e76-112">ホスト フォームへのカスタム コントロールの追加</span><span class="sxs-lookup"><span data-stu-id="f4e76-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="f4e76-113">デザイン時デバッグのためのプロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="f4e76-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="f4e76-114">カスタム コントロールをデザイン時のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f4e76-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="f4e76-115">完了したら、カスタム コントロールのデザイン時の動作をデバッグするために必要なタスクについて理解があります。</span><span class="sxs-lookup"><span data-stu-id="f4e76-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4e76-116">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4e76-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f4e76-117">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f4e76-118">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4e76-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f4e76-119">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="f4e76-119">Creating the Project</span></span>  
 <span data-ttu-id="f4e76-120">最初の手順では、アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-120">The first step is to create the application project.</span></span> <span data-ttu-id="f4e76-121">このプロジェクトを使用するカスタム コントロールをホストするアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="f4e76-122">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="f4e76-122">To create the project</span></span>  
  
-   <span data-ttu-id="f4e76-123">"DebuggingExample"と呼ばれる Windows アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-123">Create a Windows Application project called "DebuggingExample".</span></span> <span data-ttu-id="f4e76-124">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4e76-124">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="f4e76-125">コントロール ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-125">Creating a Control Library Project</span></span>  
 <span data-ttu-id="f4e76-126">次の手順では、コントロール ライブラリ プロジェクトを作成し、カスタム コントロールを設定します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-126">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="f4e76-127">コントロール ライブラリ プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="f4e76-127">To create the control library project</span></span>  
  
1.  <span data-ttu-id="f4e76-128">追加、 **Windows コントロール ライブラリ**プロジェクトがソリューションにします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-128">Add a **Windows Control Library** project to the solution.</span></span>  
  
2.  <span data-ttu-id="f4e76-129">新しい**UserControl** DebugControlLibrary プロジェクト項目です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-129">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="f4e76-130">詳細については、「 [NIB: 方法: 新しいプロジェクト項目の追加](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-130">For details, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="f4e76-131">新しいソース ファイルに「タブ」の基本の名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-131">Give the new source file a base name of "DebugControl".</span></span>  
  
3.  <span data-ttu-id="f4e76-132">使用して、**ソリューション エクスプ ローラー**の基本名を持つコード ファイルを削除することによって、プロジェクトの既定のコントロールを削除する"`UserControl1`"です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-132">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="f4e76-133">詳細については、「 [NIB: 方法:: 削除、削除、および項目の除外](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-133">For details, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
4.  <span data-ttu-id="f4e76-134">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-134">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="f4e76-135">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="f4e76-135">Checkpoint</span></span>  
 <span data-ttu-id="f4e76-136">この時点では、ことができますにカスタム コントロールを表示する、**ツールボックス**です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-136">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="f4e76-137">進行状況を確認するには</span><span class="sxs-lookup"><span data-stu-id="f4e76-137">To check your progress</span></span>  
  
-   <span data-ttu-id="f4e76-138">呼ばれる新しいタブを見つける**DebugControlLibrary コンポーネント** をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-138">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="f4e76-139">開くときに、コントロールが表示されます**タブ**その横にある既定のアイコンとします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-139">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="f4e76-140">カスタム コントロールにプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-140">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="f4e76-141">デザイン時にカスタム コントロールのコードが実行されていることを示すためには、プロパティを追加して、プロパティを実装するコードにブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-141">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="f4e76-142">カスタム コントロールにプロパティを追加するには</span><span class="sxs-lookup"><span data-stu-id="f4e76-142">To add a property to your custom control</span></span>  
  
1.  <span data-ttu-id="f4e76-143">開いている**タブ**で、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-143">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="f4e76-144">クラスの定義に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-144">Add the following code to the class definition:</span></span>  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="f4e76-145">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-145">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="f4e76-146">ホスト フォームへのカスタム コントロールの追加</span><span class="sxs-lookup"><span data-stu-id="f4e76-146">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="f4e76-147">カスタム コントロールのデザイン時の動作をデバッグするには、ホストのフォームにカスタム コントロール クラスのインスタンスを配置します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-147">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="f4e76-148">ホストのフォームにカスタム コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="f4e76-148">To add your custom control to the host form</span></span>  
  
1.  <span data-ttu-id="f4e76-149">プロジェクトで、"DebuggingExample"で、Form1 を開き、 **Windows フォーム デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-149">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="f4e76-150">**ツールボックス**を開き、 **DebugControlLibrary コンポーネント** タブ、ドラッグして、**タブ**フォーム上にインスタンス。</span><span class="sxs-lookup"><span data-stu-id="f4e76-150">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3.  <span data-ttu-id="f4e76-151">検索、`DemoString`内のカスタム プロパティ、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="f4e76-151">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="f4e76-152">他のプロパティと同様に、値を変更することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f4e76-152">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="f4e76-153">場合にも注意してください、`DemoString`プロパティが選択されている場合、プロパティの説明文字列がの下に表示される、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="f4e76-153">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="f4e76-154">デザイン時デバッグのためのプロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="f4e76-154">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="f4e76-155">カスタム コントロールのデザイン時の動作をデバッグするには、カスタム コントロールのコードを実行している Visual Studio の別のインスタンスをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-155">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="f4e76-156">デザイン時デバッグ用のプロジェクトを設定するには</span><span class="sxs-lookup"><span data-stu-id="f4e76-156">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="f4e76-157">右クリックし、 **DebugControlLibrary**プロジェクトで、**ソリューション エクスプ ローラー**選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-157">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f4e76-158">**DebugControlLibrary**プロパティ シートで、**デバッグ**タブです。</span><span class="sxs-lookup"><span data-stu-id="f4e76-158">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="f4e76-159">**開始動作**セクションで、**外部プログラムの開始**です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-159">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="f4e76-160">できます、省略記号ボタンをクリックして、Visual Studio の別のインスタンスをデバッグ (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を Visual Studio IDE の参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-160">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="f4e76-161">実行可能ファイルの名前は**devenv.exe**、され、パスは %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe で既定の場所にインストールした場合。</span><span class="sxs-lookup"><span data-stu-id="f4e76-161">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3.  <span data-ttu-id="f4e76-162">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-162">Click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="f4e76-163">右クリックし、 **DebugControlLibrary**プロジェクトし、選択**スタートアップ プロジェクトとして設定**このデバッグ構成を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-163">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="f4e76-164">カスタム コントロールをデザイン時のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f4e76-164">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="f4e76-165">デザイン モードで実行するときに、カスタム コントロールをデバッグする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="f4e76-165">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="f4e76-166">デバッグ セッションを開始して Visual Studio の新しいインスタンスを作成、ソリューションを読み込み、"DebuggingExample"を使用します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-166">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="f4e76-167">Form1 を開いたとき、**フォーム デザイナー**、カスタム コントロールのインスタンスが作成され、実行が開始されます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-167">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="f4e76-168">デザイン時にカスタム コントロールをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="f4e76-168">To debug your custom control at design time</span></span>  
  
1.  <span data-ttu-id="f4e76-169">開く、**タブ**内のソース ファイル、**コード エディター**にブレークポイントを配置し、`Set`のアクセサー、`DemoString`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f4e76-169">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2.  <span data-ttu-id="f4e76-170">F5 キーを押してデバッグ セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="f4e76-170">Press F5 to start the debugging session.</span></span> <span data-ttu-id="f4e76-171">Visual Studio の新しいインスタンスを作成することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f4e76-171">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="f4e76-172">2 つの方法でインスタンスを区別することができます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-172">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="f4e76-173">デバッグのインスタンスには、word**を実行している**のタイトル バーに</span><span class="sxs-lookup"><span data-stu-id="f4e76-173">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="f4e76-174">デバッグ インスタンスが、**開始**のボタンではその**デバッグ**ツールバーを無効になっています</span><span class="sxs-lookup"><span data-stu-id="f4e76-174">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="f4e76-175">ブレークポイントは、デバッグのインスタンスで設定されます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-175">Your breakpoint is set in the debugging instance.</span></span>  
  
3.  <span data-ttu-id="f4e76-176">Visual Studio の新しいインスタンスの"DebuggingExample"ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-176">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="f4e76-177">選択して、ソリューションを簡単に見つけることができます**最近使ったプロジェクト**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="f4e76-177">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="f4e76-178">最近使用したファイル、"DebuggingExample.sln"ソリューション ファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-178">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="f4e76-179">Form1 を開き、**フォーム デザイナー**を選択し、**タブ**コントロール。</span><span class="sxs-lookup"><span data-stu-id="f4e76-179">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5.  <span data-ttu-id="f4e76-180">値を変更、`DemoString`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f4e76-180">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="f4e76-181">変更をコミットする場合、Visual Studio のデバッグのインスタンスがフォーカスを取得し、ブレークポイントで実行が停止に注意してください。</span><span class="sxs-lookup"><span data-stu-id="f4e76-181">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="f4e76-182">プロパティ アクセサーを 1 ステップを作成することができますと同様に、その他のコードはします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-182">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6.  <span data-ttu-id="f4e76-183">Visual Studio のホスト インスタンスを閉じるかをクリックして終了する、デバッグ セッションがしたら、**デバッグの停止**デバッグ インスタンスでボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4e76-183">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f4e76-184">次の手順</span><span class="sxs-lookup"><span data-stu-id="f4e76-184">Next Steps</span></span>  
 <span data-ttu-id="f4e76-185">これで、カスタム コントロールをデバッグするにはデザイン時に、Visual Studio IDE を使用して、コントロールの相互作用の拡張のさまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="f4e76-185">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="f4e76-186">使用することができます、<xref:System.ComponentModel.Component.DesignMode%2A>のプロパティ、<xref:System.ComponentModel.Component>デザイン時にのみ実行されるコードを記述するクラス。</span><span class="sxs-lookup"><span data-stu-id="f4e76-186">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="f4e76-187">詳細については、「<xref:System.ComponentModel.Component.DesignMode%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4e76-187">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="f4e76-188">いくつかの属性をデザイナーにカスタム コントロールの相互作用を操作するコントロールのプロパティに適用することができます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-188">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="f4e76-189">これらの属性を見つけることができます、<xref:System.ComponentModel?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="f4e76-189">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="f4e76-190">カスタム コントロールのカスタム デザイナーを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-190">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="f4e76-191">Visual Studio によって公開される拡張可能なデザイナー インフラストラクチャを使用してデザイン環境を完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="f4e76-191">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="f4e76-192">詳細については、「[チュートリアル:、Windows フォーム コントロール利用の Visual Studio デザイン時の機能を作成する](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4e76-192">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e76-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4e76-193">See Also</span></span>  
 [<span data-ttu-id="f4e76-194">チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="f4e76-194">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [<span data-ttu-id="f4e76-195">方法: デザイン時のサービスにアクセス</span><span class="sxs-lookup"><span data-stu-id="f4e76-195">How to: Access Design-Time Services</span></span>](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [<span data-ttu-id="f4e76-196">方法: Windows フォームでデザイン時サポートにアクセスする</span><span class="sxs-lookup"><span data-stu-id="f4e76-196">How to: Access Design-Time Support in Windows Forms</span></span>](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
