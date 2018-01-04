---
title: "チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75dee4b230c790e5f1abf6bf7e77af106da0e7f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="5a4fb-102">チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て</span><span class="sxs-lookup"><span data-stu-id="5a4fb-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="5a4fb-103">このチュートリアルでは、フォームに表示する Windows Presentation Foundation (WPF) コントロール型を選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="5a4fb-104">プロジェクトに含まれている WPF コントロール型であれば、どれでも選択できます。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-104">You can select any WPF control types which are included in your project.</span></span>  
  
 <span data-ttu-id="5a4fb-105">このチュートリアルでは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="5a4fb-106">プロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-106">Create the project.</span></span>  
  
-   <span data-ttu-id="5a4fb-107">WPF コントロール型を作成する。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-107">Create the WPF control types.</span></span>  
  
-   <span data-ttu-id="5a4fb-108">WPF コントロールを選択する。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-108">Select WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a4fb-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5a4fb-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5a4fb-111">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5a4fb-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5a4fb-112">Prerequisites</span></span>  
 <span data-ttu-id="5a4fb-113">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="5a4fb-114">。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="5a4fb-115">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="5a4fb-115">Creating the Project</span></span>  
 <span data-ttu-id="5a4fb-116">まず、Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a4fb-117">WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="5a4fb-118">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="5a4fb-118">To create the project</span></span>  
  
-   <span data-ttu-id="5a4fb-119">Visual Basic または Visual c# のという名前で新しい Windows フォーム アプリケーション プロジェクトを作成`SelectingWpfContent`です。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="5a4fb-120">WPF コントロール型の作成</span><span class="sxs-lookup"><span data-stu-id="5a4fb-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="5a4fb-121">プロジェクトに追加した WPF コントロール型は、さまざまな <xref:System.Windows.Forms.Integration.ElementHost> コントロール内でホストできます。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="5a4fb-122">WPF コントロール型を作成するには</span><span class="sxs-lookup"><span data-stu-id="5a4fb-122">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="5a4fb-123">新しい WPF <xref:System.Windows.Controls.UserControl> プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="5a4fb-124">コントロール型の既定の名前である `UserControl1.xaml` を使用します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="5a4fb-125">詳細については、次を参照してください。[チュートリアル: 新しい WPF コンテンツの作成デザイン時に Windows フォームで](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="5a4fb-126">デザイン ビューで `UserControl1` が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="5a4fb-127">詳細については、次を参照してください。[する方法: Select およびデザイン サーフェイス上の要素の移動](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474)です。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-127">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="5a4fb-128">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`です。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="5a4fb-129">追加、<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>コントロールを<xref:System.Windows.Controls.UserControl>の値を設定し、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティを**ホストするコンテンツの**します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5.  <span data-ttu-id="5a4fb-130">WPF <xref:System.Windows.Controls.UserControl> をプロジェクトにもう 1 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="5a4fb-131">コントロール型の既定の名前である `UserControl2.xaml` を使用します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6.  <span data-ttu-id="5a4fb-132">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`です。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7.  <span data-ttu-id="5a4fb-133">追加、<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>コントロールを<xref:System.Windows.Controls.UserControl>の値を設定し、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティを**Hosted Content 2**です。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="5a4fb-134">**注**一般より高度な WPF コンテンツをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="5a4fb-135">ここでは、説明する目的でのみ <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> コントロールを使用しています。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1.  <span data-ttu-id="5a4fb-136">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="5a4fb-137">WPF コントロールの選択</span><span class="sxs-lookup"><span data-stu-id="5a4fb-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="5a4fb-138">既にコンテンツをホストしている <xref:System.Windows.Forms.Integration.ElementHost> コントロールに異なる WPF コンテンツを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="5a4fb-139">WPF コントロールを選択するには</span><span class="sxs-lookup"><span data-stu-id="5a4fb-139">To select WPF controls</span></span>  
  
1.  <span data-ttu-id="5a4fb-140">Windows フォーム デザイナーで `Form1` を開きます。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="5a4fb-141">**ツールボックス**をダブルクリックして`UserControl1`のインスタンスを作成する`UserControl1`フォームにします。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="5a4fb-142">`UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="5a4fb-143">スマート タグ パネルで`elementHost1`を開き、 **ホストするコンテンツ**ドロップダウン リスト。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4.  <span data-ttu-id="5a4fb-144">選択**[usercontrol2]**ドロップダウン リスト ボックスからです。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="5a4fb-145">これで、`elementHost1` コントロールが `UserControl2` 型のインスタンスをホストするようになりました。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5.  <span data-ttu-id="5a4fb-146">**プロパティ**ウィンドウ、いることを確認、<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>プロパティに設定されている**[usercontrol2]**です。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6.  <span data-ttu-id="5a4fb-147">**ツールボックス**で、 **WPF 相互運用性**グループで、ドラッグ、<xref:System.Windows.Forms.Integration.ElementHost>コントロールをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="5a4fb-148">新しい名前として、このコントロールの既定である `elementHost2` を使用します。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-148">The default name for the new control is `elementHost2`.</span></span>  
  
7.  <span data-ttu-id="5a4fb-149">スマート タグ パネルで`elementHost2`を開き、 **ホストするコンテンツ**ドロップダウン リスト。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8.  <span data-ttu-id="5a4fb-150">選択**UserControl1**ドロップダウン リストからです。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="5a4fb-151">これで、`elementHost2` コントロールが `UserControl1` 型のインスタンスをホストするようになりました。</span><span class="sxs-lookup"><span data-stu-id="5a4fb-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4fb-152">参照</span><span class="sxs-lookup"><span data-stu-id="5a4fb-152">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="5a4fb-153">移行と相互運用性</span><span class="sxs-lookup"><span data-stu-id="5a4fb-153">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="5a4fb-154">WPF コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="5a4fb-154">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="5a4fb-155">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="5a4fb-155">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
