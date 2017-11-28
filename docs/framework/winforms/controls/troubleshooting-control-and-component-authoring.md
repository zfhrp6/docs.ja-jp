---
title: "コントロールとコンポーネントの作成時のトラブルシューティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e027a5b60e066a8d38db530c37a394227f2e892
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="1df80-102">コントロールとコンポーネントの作成時のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1df80-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="1df80-103">このトピックでは、コンポーネントとコントロールの開発時に発生する次の一般的な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="1df80-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="1df80-104">詳細については、「[コンポーネントによるプログラミング](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1df80-104">For more information, see [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
-   <span data-ttu-id="1df80-105">ツールボックスにコントロールを追加できない</span><span class="sxs-lookup"><span data-stu-id="1df80-105">Cannot Add Control to Toolbox</span></span>  
  
-   <span data-ttu-id="1df80-106">Windows フォームのユーザー コントロールまたはコンポーネントをデバッグできない</span><span class="sxs-lookup"><span data-stu-id="1df80-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
-   <span data-ttu-id="1df80-107">継承されたコントロールまたはコンポーネントでイベントが 2 回発生する</span><span class="sxs-lookup"><span data-stu-id="1df80-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
-   <span data-ttu-id="1df80-108">デザイン時エラー: "コンポーネント '*コンポーネント名*' を生成できませんでした"</span><span class="sxs-lookup"><span data-stu-id="1df80-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
-   <span data-ttu-id="1df80-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="1df80-109">STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="1df80-110">ツールボックスにコンポーネント アイコンが表示されない</span><span class="sxs-lookup"><span data-stu-id="1df80-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="1df80-111">ツールボックスにコントロールを追加できない</span><span class="sxs-lookup"><span data-stu-id="1df80-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="1df80-112">別のプロジェクトで作成したカスタム コントロールまたはサード パーティ製コントロールを**ツールボックス**に追加する場合は、手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1df80-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="1df80-113">現在のプロジェクトにコントロールまたはコンポーネントが含まれている場合は、**ツールボックス**に自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1df80-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="1df80-114">詳細については、「[チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1df80-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="1df80-115">ツールボックスにコントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="1df80-115">To add a control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="1df80-116">**[ツールボックス]** を右クリックし、ショートカット メニューの **[アイテムの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1df80-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2.  <span data-ttu-id="1df80-117">**[ツールボックス アイテムの選択]** ダイアログ ボックスで、コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1df80-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    -   <span data-ttu-id="1df80-118">.NET Framework コンポーネントまたはコントロールを追加する場合は、**[.NET Framework コンポーネント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1df80-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="1df80-119">または</span><span class="sxs-lookup"><span data-stu-id="1df80-119">– or –</span></span>  
  
    -   <span data-ttu-id="1df80-120">COM コンポーネントまたは ActiveX コントロールを追加する場合は、**[COM コンポーネント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1df80-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3.  <span data-ttu-id="1df80-121">ダイアログ ボックスにコントロールが表示されている場合は、コントロールが選択されていることを確認し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1df80-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1df80-122">コントロールが**ツールボックス**に追加されます。</span><span class="sxs-lookup"><span data-stu-id="1df80-122">The control is added to the **Toolbox**.</span></span>  
  
4.  <span data-ttu-id="1df80-123">ダイアログ ボックスにコントロールが表示されていない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1df80-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="1df80-124">**[参照]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1df80-124">Click the **Browse** button.</span></span>  
  
    2.  <span data-ttu-id="1df80-125">コントロールが含まれた .dll ファイルがあるフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="1df80-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3.  <span data-ttu-id="1df80-126">.dll ファイルを選択し、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1df80-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="1df80-127">ダイアログ ボックスにコントロールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1df80-127">Your control appears in the dialog box.</span></span>  
  
    4.  <span data-ttu-id="1df80-128">コントロールが選択されていることを確認し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1df80-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="1df80-129">コントロールが**ツールボックス**に追加されます。</span><span class="sxs-lookup"><span data-stu-id="1df80-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="1df80-130">Windows フォームのユーザー コントロールまたはコンポーネントをデバッグできない</span><span class="sxs-lookup"><span data-stu-id="1df80-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="1df80-131">コントロールがから派生している場合、<xref:System.Windows.Forms.UserControl>クラス、テスト コンテナーで実行時の動作をデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="1df80-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="1df80-132">詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1df80-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="1df80-133">他のカスタム コントロールやカスタム コンポーネントはスタンドアロン プロジェクトではありません。</span><span class="sxs-lookup"><span data-stu-id="1df80-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="1df80-134">そのため、Windows フォーム プロジェクトなどのアプリケーションでホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1df80-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="1df80-135">コントロールまたはコンポーネントをデバッグするには、Windows フォーム プロジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1df80-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="1df80-136">コントロールまたはコンポーネントをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="1df80-136">To debug a control or component</span></span>  
  
1.  <span data-ttu-id="1df80-137">**[ビルド]** メニューの **[ソリューションのビルド]** をクリックして、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="1df80-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2.  <span data-ttu-id="1df80-138">**[ファイル]** メニューの **[追加]** をクリックし、**[新しいプロジェクト]** をクリックして、アプリケーションにテスト プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="1df80-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3.  <span data-ttu-id="1df80-139">**[新しいプロジェクトの追加]** ダイアログ ボックスで、プロジェクトの種類として **[Windows アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1df80-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4.  <span data-ttu-id="1df80-140">**ソリューション エクスプローラー**で、新しいプロジェクトの **[参照設定]** ノードを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="1df80-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="1df80-141">ショートカット メニューの **[参照の追加]** をクリックして、コントロールまたはコンポーネントを含むプロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="1df80-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5.  <span data-ttu-id="1df80-142">テスト プロジェクトにコントロールまたはコンポーネントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1df80-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="1df80-143">コンポーネントが**ツールボックス**に表示されている場合は、デザイナー画面にドラッグできます。または、次のコード例に示すように、インスタンスをプログラムで作成できます。</span><span class="sxs-lookup"><span data-stu-id="1df80-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="1df80-144">これで、コントロールまたはコンポーネントを通常どおりデバッグできるようになります。</span><span class="sxs-lookup"><span data-stu-id="1df80-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="1df80-145">デバッグの詳細については、「[Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)」および「[チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1df80-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="1df80-146">継承されたコントロールまたはコンポーネントでイベントが 2 回発生する</span><span class="sxs-lookup"><span data-stu-id="1df80-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="1df80-147">`Handles` 句が重複していることが原因と考えられます。</span><span class="sxs-lookup"><span data-stu-id="1df80-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="1df80-148">詳細については、「[Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1df80-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="1df80-149">デザイン時エラー: "コンポーネント 'コンポーネント名' を生成できませんでした"</span><span class="sxs-lookup"><span data-stu-id="1df80-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="1df80-150">コンポーネントまたはコントロールは、パラメーターなしで既定のコンストラクターを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1df80-150">Your component or control must provide a default constructor with no parameters.</span></span> <span data-ttu-id="1df80-151">デザイン環境では、コンポーネントまたはコントロールのインスタンスを作成するときに、パラメーターを受け取るコンストラクター オーバーロードにパラメーターを提供しません。</span><span class="sxs-lookup"><span data-stu-id="1df80-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="1df80-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="1df80-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="1df80-153"><xref:System.STAThreadAttribute> Windows フォームがシングル スレッド アパートメント モデルを使用する共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="1df80-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="1df80-154">この属性を Windows フォーム アプリケーションの `Main` メソッドに適用していない場合、意図しない動作が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="1df80-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="1df80-155">たとえば、背景画像されない可能性がありますなどのコントロールに対して<xref:System.Windows.Forms.ListView>です。</span><span class="sxs-lookup"><span data-stu-id="1df80-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="1df80-156">また、一部のコントロールでは、オートコンプリートやドラッグ アンド ドロップの動作を正常に行うためにこの属性が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="1df80-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="1df80-157">ツールボックスにコンポーネント アイコンが表示されない</span><span class="sxs-lookup"><span data-stu-id="1df80-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="1df80-158">使用すると<xref:System.Drawing.ToolboxBitmapAttribute>にカスタム コンポーネントにアイコンを関連付けるには、ビットマップは自動生成されたコンポーネントをツールボックスに表示されません。</span><span class="sxs-lookup"><span data-stu-id="1df80-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="1df80-159">ビットマップを表示するには、**[ツールボックス アイテムの選択]** ダイアログ ボックスを使用してコントロールを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="1df80-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="1df80-160">詳細については、「[方法 : コントロールにツールボックス ビットマップを指定する](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1df80-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df80-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="1df80-161">See Also</span></span>  
 [<span data-ttu-id="1df80-162">デザイン時の Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="1df80-162">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="1df80-163">チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定</span><span class="sxs-lookup"><span data-stu-id="1df80-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="1df80-164">方法: UserControl の実行時の動作をテストする</span><span class="sxs-lookup"><span data-stu-id="1df80-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [<span data-ttu-id="1df80-165">チュートリアル: カスタム Windows フォーム コントロールのデザイン時のデバッグ</span><span class="sxs-lookup"><span data-stu-id="1df80-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="1df80-166">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="1df80-166">Component Authoring</span></span>](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [<span data-ttu-id="1df80-167">デザイン時の開発のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1df80-167">Troubleshooting Design-Time Development</span></span>](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="1df80-168">コンポーネントによるプログラミング</span><span class="sxs-lookup"><span data-stu-id="1df80-168">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
