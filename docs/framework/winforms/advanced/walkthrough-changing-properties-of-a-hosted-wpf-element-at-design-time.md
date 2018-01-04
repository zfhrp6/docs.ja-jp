---
title: "チュートリアル: デザイン時のホストされている WPF 要素のプロパティの変更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 027fb2efaff5cfdd4d6962798a85923631fa4e9b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a><span data-ttu-id="9d756-102">チュートリアル: デザイン時のホストされている WPF 要素のプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="9d756-102">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>
<span data-ttu-id="9d756-103">このチュートリアルでは、Windows フォームでホストされている Windows Presentation Foundation (WPF) コントロールのプロパティ値を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d756-103">This walkthrough shows you how to change property values of a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="9d756-104">このチュートリアルでは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d756-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="9d756-105">プロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="9d756-105">Create the project.</span></span>  
  
-   <span data-ttu-id="9d756-106">WPF コントロールを作成する。</span><span class="sxs-lookup"><span data-stu-id="9d756-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="9d756-107">Windows フォームで WPF コントロールをホストする。</span><span class="sxs-lookup"><span data-stu-id="9d756-107">Host the WPF controls on a Windows Form.</span></span>  
  
-   <span data-ttu-id="9d756-108">Visual Studio の WPF デザイナーを使用してプロパティの値を変更する。</span><span class="sxs-lookup"><span data-stu-id="9d756-108">Use the WPF Designer for Visual Studio to change property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d756-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9d756-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9d756-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d756-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9d756-111">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d756-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9d756-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9d756-112">Prerequisites</span></span>  
 <span data-ttu-id="9d756-113">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="9d756-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="9d756-114">。</span><span class="sxs-lookup"><span data-stu-id="9d756-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="9d756-115">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="9d756-115">Creating the Project</span></span>  
 <span data-ttu-id="9d756-116">まず、Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d756-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d756-117">WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9d756-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="9d756-118">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="9d756-118">To create the project</span></span>  
  
-   <span data-ttu-id="9d756-119">Visual Basic または Visual c# のという名前で新しい Windows フォーム アプリケーション プロジェクトを作成`WpfHost`です。</span><span class="sxs-lookup"><span data-stu-id="9d756-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `WpfHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="9d756-120">WPF コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="9d756-120">Creating the WPF Control</span></span>  
 <span data-ttu-id="9d756-121">プロジェクトに WPF コントロール型を追加したら、フォーム状に配置できます。</span><span class="sxs-lookup"><span data-stu-id="9d756-121">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="9d756-122">WPF コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="9d756-122">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="9d756-123">新しい WPF <xref:System.Windows.Controls.UserControl> をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="9d756-123">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="9d756-124">コントロール型の既定の名前である `UserControl1.xaml` を使用します。</span><span class="sxs-lookup"><span data-stu-id="9d756-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="9d756-125">詳細については、次を参照してください。[チュートリアル: 新しい WPF コンテンツの作成デザイン時に Windows フォームで](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d756-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="9d756-126">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Controls.Control.Background%2A>プロパティを`Blue`です。</span><span class="sxs-lookup"><span data-stu-id="9d756-126">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
3.  <span data-ttu-id="9d756-127">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="9d756-127">Build the project.</span></span>  
  
## <a name="changing-property-values-on-the-wpf-control"></a><span data-ttu-id="9d756-128">WPF コントロールのプロパティの値を変更する</span><span class="sxs-lookup"><span data-stu-id="9d756-128">Changing Property Values on the WPF Control</span></span>  
 <span data-ttu-id="9d756-129"><xref:System.Windows.Forms.Integration.ElementHost> スマート タグにより、WPF デザイナーを使用して、ホストされている WPF の内容のプロパティを簡単に変更できます。</span><span class="sxs-lookup"><span data-stu-id="9d756-129">The <xref:System.Windows.Forms.Integration.ElementHost> smart tag makes it easy to change properties of hosted WPF content by using the WPF Designer.</span></span>  
  
#### <a name="to-host-a-wpf-control"></a><span data-ttu-id="9d756-130">WPF コントロールをホストするには</span><span class="sxs-lookup"><span data-stu-id="9d756-130">To host a WPF control</span></span>  
  
1.  <span data-ttu-id="9d756-131">Windows フォーム デザイナーで `Form1` を開きます。</span><span class="sxs-lookup"><span data-stu-id="9d756-131">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="9d756-132">**ツールボックス**で、 **WPF ユーザー コントロール** タブをダブルクリックして`UserControl1`のインスタンスを作成する`UserControl1`フォームにします。</span><span class="sxs-lookup"><span data-stu-id="9d756-132">In the **Toolbox**, in the **WPF User Controls** tab, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="9d756-133">`UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。</span><span class="sxs-lookup"><span data-stu-id="9d756-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="9d756-134">**ElementHost タスク**スマート タグ パネルで、**ホストされているコンテンツの編集**です。</span><span class="sxs-lookup"><span data-stu-id="9d756-134">In the **ElementHost Tasks** smart tag panel, select **Edit Hosted Content**.</span></span>  
  
     <span data-ttu-id="9d756-135">UserControl1.xaml が WPF デザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="9d756-135">UserControl1.xaml opens in the WPF Designer.</span></span>  
  
4.  <span data-ttu-id="9d756-136">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Controls.Control.Background%2A>プロパティを`Red`です。</span><span class="sxs-lookup"><span data-stu-id="9d756-136">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Red`.</span></span>  
  
5.  <span data-ttu-id="9d756-137">プロジェクトをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="9d756-137">Rebuild the project.</span></span>  
  
6.  <span data-ttu-id="9d756-138">Windows フォーム デザイナーで `Form1` を開きます。</span><span class="sxs-lookup"><span data-stu-id="9d756-138">Open `Form1` in the Windows Forms Designer.</span></span>  
  
     <span data-ttu-id="9d756-139">`UserControl1` のインスタンスが赤の背景になります。</span><span class="sxs-lookup"><span data-stu-id="9d756-139">The instance of `UserControl1` has a red background.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d756-140">参照</span><span class="sxs-lookup"><span data-stu-id="9d756-140">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="9d756-141">方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="9d756-141">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="9d756-142">方法: デザイン時にフォームの端に合わせてコントロールを配置する</span><span class="sxs-lookup"><span data-stu-id="9d756-142">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="9d756-143">チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="9d756-143">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="9d756-144">移行と相互運用性</span><span class="sxs-lookup"><span data-stu-id="9d756-144">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="9d756-145">WPF コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="9d756-145">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="9d756-146">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="9d756-146">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
