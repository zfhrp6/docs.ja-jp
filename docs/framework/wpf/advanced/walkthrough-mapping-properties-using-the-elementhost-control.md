---
title: "チュートリアル : ElementHost コントロールを使用したプロパティの割り当て"
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
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0db7b9677b5c8c415b6d0b3f49bd149c06843a33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="f78a5-102">チュートリアル : ElementHost コントロールを使用したプロパティの割り当て</span><span class="sxs-lookup"><span data-stu-id="f78a5-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>
<span data-ttu-id="f78a5-103">このチュートリアルで使用する方法、<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>プロパティにマップする[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]、ホスト型に対応するプロパティをプロパティ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素。</span><span class="sxs-lookup"><span data-stu-id="f78a5-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>  
  
 <span data-ttu-id="f78a5-104">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="f78a5-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="f78a5-105">プロジェクトの作成。</span><span class="sxs-lookup"><span data-stu-id="f78a5-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="f78a5-106">新しいプロパティ マッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-106">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="f78a5-107">プロパティの既定のマッピングを削除しています。</span><span class="sxs-lookup"><span data-stu-id="f78a5-107">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="f78a5-108">プロパティの既定のマッピングを拡張します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-108">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="f78a5-109">このチュートリアルでタスクの完全なコードについては、次を参照してください。 [ElementHost コントロールのサンプルを使用してプロパティをマッピング](http://go.microsoft.com/fwlink/?LinkID=160018)です。</span><span class="sxs-lookup"><span data-stu-id="f78a5-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](http://go.microsoft.com/fwlink/?LinkID=160018).</span></span>  
  
 <span data-ttu-id="f78a5-110">完了したらにマップできる、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]を対応するプロパティ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストされている要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f78a5-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f78a5-111">Prerequisites</span></span>  
 <span data-ttu-id="f78a5-112">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="f78a5-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="f78a5-113">。</span><span class="sxs-lookup"><span data-stu-id="f78a5-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f78a5-114">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="f78a5-114">Creating the Project</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="f78a5-115">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="f78a5-115">To create the project</span></span>  
  
1.  <span data-ttu-id="f78a5-116">作成、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]という名前のアプリケーション プロジェクト`PropertyMappingWithElementHost`です。</span><span class="sxs-lookup"><span data-stu-id="f78a5-116">Create a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project named `PropertyMappingWithElementHost`.</span></span> <span data-ttu-id="f78a5-117">詳細については、「 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f78a5-117">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="f78a5-118">ソリューション エクスプ ローラーで、次の参照を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="f78a5-118">In Solution Explorer, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>  
  
    -   <span data-ttu-id="f78a5-119">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="f78a5-119">PresentationCore</span></span>  
  
    -   <span data-ttu-id="f78a5-120">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="f78a5-120">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="f78a5-121">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="f78a5-121">WindowsBase</span></span>  
  
    -   <span data-ttu-id="f78a5-122">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="f78a5-122">WindowsFormsIntegration</span></span>  
  
3.  <span data-ttu-id="f78a5-123">先頭に次のコードをコピー、`Form1`コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="f78a5-123">Copy the following code into the top of the `Form1` code file.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="f78a5-124">Windows フォーム デザイナーで `Form1` を開きます。</span><span class="sxs-lookup"><span data-stu-id="f78a5-124">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="f78a5-125">イベント ハンドラーの追加フォームをダブルクリックして、<xref:System.Windows.Forms.Form.Load>イベント。</span><span class="sxs-lookup"><span data-stu-id="f78a5-125">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
5.  <span data-ttu-id="f78a5-126">Windows フォーム デザイナーに戻るし、フォームのイベント ハンドラーを追加<xref:System.Windows.Forms.Control.Resize>イベント。</span><span class="sxs-lookup"><span data-stu-id="f78a5-126">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="f78a5-127">詳細については、次を参照してください。[する方法: イベント ハンドラーを使用して作成デザイナー](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2)です。</span><span class="sxs-lookup"><span data-stu-id="f78a5-127">For more information, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
6.  <span data-ttu-id="f78a5-128">宣言、<xref:System.Windows.Forms.Integration.ElementHost>フィールドで、`Form1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-128">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a><span data-ttu-id="f78a5-129">新しいプロパティのマッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-129">Defining New Property Mappings</span></span>  
 <span data-ttu-id="f78a5-130"><xref:System.Windows.Forms.Integration.ElementHost>コントロールにより、いくつかの既定値がプロパティのマッピングを提供します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-130">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="f78a5-131">呼び出して新しいプロパティ マッピングを追加する、<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>メソッドを<xref:System.Windows.Forms.Integration.ElementHost>コントロールの<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-131">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-new-property-mappings"></a><span data-ttu-id="f78a5-132">新しいプロパティのマッピングを定義するには</span><span class="sxs-lookup"><span data-stu-id="f78a5-132">To define new property mappings</span></span>  
  
1.  <span data-ttu-id="f78a5-133">定義に次のコードをコピー、`Form1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-133">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     <span data-ttu-id="f78a5-134">`AddMarginMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.Forms.Control.Margin%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-134">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>  
  
     <span data-ttu-id="f78a5-135">`OnMarginChange`メソッドは、変換、<xref:System.Windows.Forms.Control.Margin%2A>プロパティを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.FrameworkElement.Margin%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-135">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>  
  
2.  <span data-ttu-id="f78a5-136">定義に次のコードをコピー、`Form1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-136">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     <span data-ttu-id="f78a5-137">`AddRegionMapping`メソッドは、新しいマッピングを追加、<xref:System.Windows.Forms.Control.Region%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-137">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="f78a5-138">`OnRegionChange`メソッドは、変換、<xref:System.Windows.Forms.Control.Region%2A>プロパティを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.UIElement.Clip%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-138">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="f78a5-139">`Form1_Resize`メソッドは、処理、フォームの<xref:System.Windows.Forms.Control.Resize>イベントし、ホストされている要素に合わせてクリッピング領域のサイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-139">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="f78a5-140">プロパティの既定のマッピングを削除します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-140">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="f78a5-141">プロパティの既定のマッピングを削除する、<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>メソッドを<xref:System.Windows.Forms.Integration.ElementHost>コントロールの<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-141">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="f78a5-142">プロパティの既定のマッピングを削除するには</span><span class="sxs-lookup"><span data-stu-id="f78a5-142">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="f78a5-143">定義に次のコードをコピー、`Form1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-143">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     <span data-ttu-id="f78a5-144">`RemoveCursorMapping`メソッドの既定のマッピングを削除する、<xref:System.Windows.Forms.Control.Cursor%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-144">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="f78a5-145">プロパティの既定のマッピングを拡張します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-145">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="f78a5-146">プロパティの既定のマッピングを使用しても、独自のマッピングに付加して拡張できます。</span><span class="sxs-lookup"><span data-stu-id="f78a5-146">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="f78a5-147">プロパティの既定のマッピングを拡張するには</span><span class="sxs-lookup"><span data-stu-id="f78a5-147">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="f78a5-148">定義に次のコードをコピー、`Form1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-148">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     <span data-ttu-id="f78a5-149">`ExtendBackColorMapping`メソッドでは、カスタム プロパティ トランスレーターを追加すると、既存<xref:System.Windows.Forms.Control.BackColor%2A>プロパティ マッピングします。</span><span class="sxs-lookup"><span data-stu-id="f78a5-149">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>  
  
     <span data-ttu-id="f78a5-150">`OnBackColorChange`メソッドは、ホストされるコントロールの特定のイメージを割り当てます<xref:System.Windows.Controls.Control.Background%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-150">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="f78a5-151">`OnBackColorChange`既定のプロパティ マッピングが適用された後にメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f78a5-151">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="f78a5-152">プロパティ マッピングの初期化</span><span class="sxs-lookup"><span data-stu-id="f78a5-152">Initializing Your Property Mappings</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="f78a5-153">プロパティ マッピングを初期化するには</span><span class="sxs-lookup"><span data-stu-id="f78a5-153">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="f78a5-154">定義に次のコードをコピー、`Form1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="f78a5-154">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     <span data-ttu-id="f78a5-155">`Form1_Load`メソッド ハンドル、<xref:System.Windows.Forms.Form.Load>イベントと、次の初期化を実行します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-155">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="f78a5-156">作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>要素。</span><span class="sxs-lookup"><span data-stu-id="f78a5-156">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>  
  
    -   <span data-ttu-id="f78a5-157">プロパティ マッピングをセットアップするチュートリアルの前半で定義されているメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-157">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="f78a5-158">マップされているプロパティに初期値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f78a5-158">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="f78a5-159">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="f78a5-159">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f78a5-160">参照</span><span class="sxs-lookup"><span data-stu-id="f78a5-160">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="f78a5-161">Windows フォームと WPF プロパティの割り当て</span><span class="sxs-lookup"><span data-stu-id="f78a5-161">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="f78a5-162">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="f78a5-162">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="f78a5-163">チュートリアル: Windows フォームでの WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="f78a5-163">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
