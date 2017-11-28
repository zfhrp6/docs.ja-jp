---
title: "チュートリアル : WindowsFormsHost 要素を使用したプロパティの割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f566d41ff1ffa07a2f52641ba05e48dfa604cfc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="60327-102">チュートリアル : WindowsFormsHost 要素を使用したプロパティの割り当て</span><span class="sxs-lookup"><span data-stu-id="60327-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>
<span data-ttu-id="60327-103">このチュートリアルで使用する方法、<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>プロパティにマップする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="60327-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
 <span data-ttu-id="60327-104">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="60327-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="60327-105">プロジェクトの作成。</span><span class="sxs-lookup"><span data-stu-id="60327-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="60327-106">アプリケーションのレイアウトを定義します。</span><span class="sxs-lookup"><span data-stu-id="60327-106">Defining the application layout.</span></span>  
  
-   <span data-ttu-id="60327-107">新しいプロパティ マッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="60327-107">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="60327-108">プロパティの既定のマッピングを削除しています。</span><span class="sxs-lookup"><span data-stu-id="60327-108">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="60327-109">プロパティの既定のマッピングを置換します。</span><span class="sxs-lookup"><span data-stu-id="60327-109">Replacing a default property mapping.</span></span>  
  
-   <span data-ttu-id="60327-110">プロパティの既定のマッピングを拡張します。</span><span class="sxs-lookup"><span data-stu-id="60327-110">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="60327-111">このチュートリアルでタスクの完全なコードについては、次を参照してください。 [WindowsFormsHost 要素のサンプルを使用してプロパティをマッピング](http://go.microsoft.com/fwlink/?LinkID=160019)です。</span><span class="sxs-lookup"><span data-stu-id="60327-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](http://go.microsoft.com/fwlink/?LinkID=160019).</span></span>  
  
 <span data-ttu-id="60327-112">完了したらにマップできる、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="60327-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="60327-113">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="60327-113">Prerequisites</span></span>  
 <span data-ttu-id="60327-114">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="60327-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="60327-115">。</span><span class="sxs-lookup"><span data-stu-id="60327-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="60327-116">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="60327-116">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="60327-117">プロジェクトを作成し、設定するには</span><span class="sxs-lookup"><span data-stu-id="60327-117">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="60327-118">という名前の WPF アプリケーション プロジェクトを作成する`PropertyMappingWithWfhSample`です。</span><span class="sxs-lookup"><span data-stu-id="60327-118">Create a WPF Application project named `PropertyMappingWithWfhSample`.</span></span>  
  
2.  <span data-ttu-id="60327-119">ソリューション エクスプ ローラーで、WindowsFormsIntegration.dll と呼ばれる WindowsFormsIntegration アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="60327-119">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="60327-120">ソリューション エクスプ ローラーで、System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="60327-120">In Solution Explorer, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="defining-the-application-layout"></a><span data-ttu-id="60327-121">アプリケーションのレイアウトを定義します。</span><span class="sxs-lookup"><span data-stu-id="60327-121">Defining the Application Layout</span></span>  
 <span data-ttu-id="60327-122">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションで使用する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストへの要素、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="60327-122">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-define-the-application-layout"></a><span data-ttu-id="60327-123">アプリケーションのレイアウトを定義するには</span><span class="sxs-lookup"><span data-stu-id="60327-123">To define the application layout</span></span>  
  
1.  <span data-ttu-id="60327-124">Window1.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="60327-124">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="60327-125">既存のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="60327-125">Replace the existing code with the following code.</span></span>  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  <span data-ttu-id="60327-126">Window1.xaml.cs の名前をコード エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="60327-126">Open Window1.xaml.cs in the Code Editor.</span></span>  
  
4.  <span data-ttu-id="60327-127">ファイルの先頭には、次の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="60327-127">At the top of the file, import the following namespaces.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="60327-128">新しいプロパティ マッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="60327-128">Defining a New Property Mapping</span></span>  
 <span data-ttu-id="60327-129"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がいくつかの既定のプロパティ マッピングを用意されています。</span><span class="sxs-lookup"><span data-stu-id="60327-129">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="60327-130">呼び出して新しいプロパティ マッピングを追加する、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。</span><span class="sxs-lookup"><span data-stu-id="60327-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="60327-131">新しいプロパティ マッピングを定義するには</span><span class="sxs-lookup"><span data-stu-id="60327-131">To define a new property mapping</span></span>  
  
-   <span data-ttu-id="60327-132">定義に次のコードをコピー、`Window1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="60327-132">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     <span data-ttu-id="60327-133">`AddClipMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.UIElement.Clip%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="60327-133">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="60327-134">`OnClipChange`メソッドは、変換、<xref:System.Windows.UIElement.Clip%2A>プロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="60327-134">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="60327-135">`Window1_SizeChanged`メソッドを処理ウィンドウの<xref:System.Windows.FrameworkElement.SizeChanged>イベントと、アプリケーション ウィンドウに合わせてクリッピング領域のサイズします。</span><span class="sxs-lookup"><span data-stu-id="60327-135">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="60327-136">プロパティの既定のマッピングを削除します。</span><span class="sxs-lookup"><span data-stu-id="60327-136">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="60327-137">プロパティの既定のマッピングを削除する、<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。</span><span class="sxs-lookup"><span data-stu-id="60327-137">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="60327-138">プロパティの既定のマッピングを削除するには</span><span class="sxs-lookup"><span data-stu-id="60327-138">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="60327-139">定義に次のコードをコピー、`Window1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="60327-139">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     <span data-ttu-id="60327-140">`RemoveCursorMapping`メソッドの既定のマッピングを削除する、<xref:System.Windows.FrameworkElement.Cursor%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="60327-140">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>  
  
## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="60327-141">プロパティの既定のマッピングを置き換える</span><span class="sxs-lookup"><span data-stu-id="60327-141">Replacing a Default Property Mapping</span></span>  
 <span data-ttu-id="60327-142">既定のマッピングと呼び出し元を削除することでプロパティの既定のマッピングを置き換える、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>します。</span><span class="sxs-lookup"><span data-stu-id="60327-142">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="60327-143">プロパティの既定のマッピングを置換するには</span><span class="sxs-lookup"><span data-stu-id="60327-143">To replace a default property mapping</span></span>  
  
-   <span data-ttu-id="60327-144">定義に次のコードをコピー、`Window1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="60327-144">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     <span data-ttu-id="60327-145">`ReplaceFlowDirectionMapping`メソッドの既定のマッピングに置き換えて、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="60327-145">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>  
  
     <span data-ttu-id="60327-146">`OnFlowDirectionChange`メソッドは、変換、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="60327-146">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>  
  
     <span data-ttu-id="60327-147">`cb_CheckedChanged`メソッド ハンドル、<xref:System.Windows.Forms.CheckBox.CheckedChanged>でイベントを<xref:System.Windows.Forms.CheckBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="60327-147">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="60327-148">割り当てます、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティの値に基づきます、<xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティ</span><span class="sxs-lookup"><span data-stu-id="60327-148">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="60327-149">プロパティの既定のマッピングを拡張します。</span><span class="sxs-lookup"><span data-stu-id="60327-149">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="60327-150">プロパティの既定のマッピングを使用しても、独自のマッピングに付加して拡張できます。</span><span class="sxs-lookup"><span data-stu-id="60327-150">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="60327-151">プロパティの既定のマッピングを拡張するには</span><span class="sxs-lookup"><span data-stu-id="60327-151">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="60327-152">定義に次のコードをコピー、`Window1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="60327-152">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     <span data-ttu-id="60327-153">`ExtendBackgroundMapping`メソッドでは、カスタム プロパティ トランスレーターを追加すると、既存<xref:System.Windows.Controls.Control.Background%2A>プロパティ マッピングします。</span><span class="sxs-lookup"><span data-stu-id="60327-153">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>  
  
     <span data-ttu-id="60327-154">`OnBackgroundChange`メソッドは、ホストされるコントロールの特定のイメージを割り当てます<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="60327-154">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="60327-155">`OnBackgroundChange`既定のプロパティ マッピングが適用された後にメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60327-155">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="60327-156">プロパティ マッピングの初期化</span><span class="sxs-lookup"><span data-stu-id="60327-156">Initializing Your Property Mappings</span></span>  
 <span data-ttu-id="60327-157">プロパティ マッピングで既に説明したメソッドを呼び出して設定、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="60327-157">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="60327-158">プロパティ マッピングを初期化するには</span><span class="sxs-lookup"><span data-stu-id="60327-158">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="60327-159">定義に次のコードをコピー、`Window1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="60327-159">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     <span data-ttu-id="60327-160">`WindowLoaded`メソッド ハンドル、<xref:System.Windows.FrameworkElement.Loaded>イベントと、次の初期化を実行します。</span><span class="sxs-lookup"><span data-stu-id="60327-160">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="60327-161">作成、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="60327-161">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>  
  
    -   <span data-ttu-id="60327-162">プロパティ マッピングをセットアップするチュートリアルの前半で定義されているメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="60327-162">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="60327-163">マップされているプロパティに初期値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="60327-163">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="60327-164">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="60327-164">Press F5 to build and run the application.</span></span> <span data-ttu-id="60327-165">効果を確認するチェック ボックスをクリックして、<xref:System.Windows.FrameworkElement.FlowDirection%2A>マッピングします。</span><span class="sxs-lookup"><span data-stu-id="60327-165">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="60327-166">チェック ボックスをクリックすると、レイアウトは左から右方向を反転させます。</span><span class="sxs-lookup"><span data-stu-id="60327-166">When you click the check box, the layout reverses its left-right orientation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60327-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="60327-167">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="60327-168">Windows フォームと WPF プロパティの割り当て</span><span class="sxs-lookup"><span data-stu-id="60327-168">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="60327-169">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="60327-169">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="60327-170">チュートリアル: WPF での Windows フォーム コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="60327-170">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
