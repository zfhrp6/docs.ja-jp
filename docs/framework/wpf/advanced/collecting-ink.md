---
title: インクの収集
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f3effe358ba2d7accf1b0eea3493f63cfea6598
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="collecting-ink"></a><span data-ttu-id="9e866-102">インクの収集</span><span class="sxs-lookup"><span data-stu-id="9e866-102">Collecting Ink</span></span>
<span data-ttu-id="9e866-103">[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) プラットフォームでは、その機能の中核としてデジタル インクが収集されます。</span><span class="sxs-lookup"><span data-stu-id="9e866-103">The [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="9e866-104">このトピックでは、インク Windows Presentation Foundation (WPF) のコレクションの方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="9e866-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9e866-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9e866-105">Prerequisites</span></span>  
 <span data-ttu-id="9e866-106">以降に示す例を使用するには、まず、[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] と [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e866-106">To use the following examples, you must first install [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="9e866-107">また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対応するアプリケーションの作成方法も理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e866-107">You should also understand how to write applications for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="9e866-108">概要の詳細については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください[チュートリアル: 最初の WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e866-108">For more information about getting started with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="using-the-inkcanvas-element"></a><span data-ttu-id="9e866-109">InkCanvas 要素の使用</span><span class="sxs-lookup"><span data-stu-id="9e866-109">Using the InkCanvas Element</span></span>  
 <span data-ttu-id="9e866-110"><xref:System.Windows.Controls.InkCanvas>要素でインクを収集する最も簡単な方法を提供する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9e866-110">The <xref:System.Windows.Controls.InkCanvas> element provides the easiest way to collect ink in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="9e866-111"><xref:System.Windows.Controls.InkCanvas>要素がに似ていますが、 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx)オブジェクトから、[!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)]と以前のバージョン。</span><span class="sxs-lookup"><span data-stu-id="9e866-111">The <xref:System.Windows.Controls.InkCanvas> element is similar to the [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) object from the [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] and earlier versions.</span></span>  
  
 <span data-ttu-id="9e866-112">使用して、<xref:System.Windows.Controls.InkCanvas>要素を受け取り、インク入力を表示します。</span><span class="sxs-lookup"><span data-stu-id="9e866-112">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="9e866-113">インクは一般的に、スタイラスを使用して入力します。スタイラスはデジタイザーとの対話により、インク ストロークを生成します。</span><span class="sxs-lookup"><span data-stu-id="9e866-113">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="9e866-114">また、スタイラスの代わりにマウスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e866-114">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="9e866-115">作成したストロークとして表されます<xref:System.Windows.Ink.Stroke>プログラムとユーザーの両方の入力、オブジェクト、およびそれらを操作できます。</span><span class="sxs-lookup"><span data-stu-id="9e866-115">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="9e866-116"><xref:System.Windows.Controls.InkCanvas>により、ユーザーが選択、変更、削除、既存<xref:System.Windows.Ink.Stroke>です。</span><span class="sxs-lookup"><span data-stu-id="9e866-116">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>  
  
 <span data-ttu-id="9e866-117">XAML を使用して、`InkCanvas` 要素をツリーに追加するだけで簡単にインク収集を設定できます。</span><span class="sxs-lookup"><span data-stu-id="9e866-117">By using XAML, you can set up ink collection as easily as adding an `InkCanvas` element to your tree.</span></span> <span data-ttu-id="9e866-118">次の例では追加、<xref:System.Windows.Controls.InkCanvas>既定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で作成されたプロジェクト[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9e866-118">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] project created in [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].</span></span>  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 <span data-ttu-id="9e866-119">`InkCanvas` 要素には子要素を含めることもできます。これにより、ほとんどすべての XAML 要素にインク注釈機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="9e866-119">The `InkCanvas` element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="9e866-120">たとえば、機能を追加する場合は、インクをテキスト要素に、単に使用するの子、<xref:System.Windows.Controls.InkCanvas>です。</span><span class="sxs-lookup"><span data-stu-id="9e866-120">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 <span data-ttu-id="9e866-121">インクを使用したイメージのマークアップのサポートも、簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="9e866-121">Adding support for marking up an image with ink is just as easy.</span></span>  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a><span data-ttu-id="9e866-122">InkCollection モード</span><span class="sxs-lookup"><span data-stu-id="9e866-122">InkCollection Modes</span></span>  
 <span data-ttu-id="9e866-123"><xref:System.Windows.Controls.InkCanvas>さまざまな入力モードをサポートしています、<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9e866-123">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>  
  
### <a name="manipulating-ink"></a><span data-ttu-id="9e866-124">インクの操作</span><span class="sxs-lookup"><span data-stu-id="9e866-124">Manipulating Ink</span></span>  
 <span data-ttu-id="9e866-125"><xref:System.Windows.Controls.InkCanvas>多くのインクの編集操作に対するサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="9e866-125">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="9e866-126">たとえば、<xref:System.Windows.Controls.InkCanvas>追加のコードを持たない要素への機能を追加するために必要なサポート ペンの背面を消去します。</span><span class="sxs-lookup"><span data-stu-id="9e866-126">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase with no additional code needed to add the functionality to the element.</span></span>  
  
#### <a name="selection"></a><span data-ttu-id="9e866-127">選択ツール</span><span class="sxs-lookup"><span data-stu-id="9e866-127">Selection</span></span>  
 <span data-ttu-id="9e866-128">選択モードは設定などの単純な<xref:System.Windows.Controls.InkCanvasEditingMode>プロパティを**選択**です。</span><span class="sxs-lookup"><span data-stu-id="9e866-128">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span> <span data-ttu-id="9e866-129">次のコードの値に基づいて編集モードの設定、 <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="9e866-129">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a><span data-ttu-id="9e866-130">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="9e866-130">DrawingAttributes</span></span>  
 <span data-ttu-id="9e866-131">使用して、<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>インク ストロークの外観を変更するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="9e866-131">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="9e866-132">インスタンス、<xref:System.Windows.Ink.DrawingAttributes.Color%2A>のメンバー <xref:System.Windows.Ink.DrawingAttributes> 、表示の色を設定<xref:System.Windows.Ink.Stroke>です。</span><span class="sxs-lookup"><span data-stu-id="9e866-132">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="9e866-133">次の例では、選択されたストロークの色を赤に変更します。</span><span class="sxs-lookup"><span data-stu-id="9e866-133">The following example changes the color of the selected strokes to red.</span></span>  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a><span data-ttu-id="9e866-134">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="9e866-134">DefaultDrawingAttributes</span></span>  
 <span data-ttu-id="9e866-135"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>プロパティは高さ、幅、およびで作成される線の色などのプロパティへのアクセスを提供する<xref:System.Windows.Controls.InkCanvas>です。</span><span class="sxs-lookup"><span data-stu-id="9e866-135">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="9e866-136">変更すると、<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>に入力されたすべての将来のストローク、<xref:System.Windows.Controls.InkCanvas>は、新しいプロパティの値で表示します。</span><span class="sxs-lookup"><span data-stu-id="9e866-136">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>  
  
 <span data-ttu-id="9e866-137">変更だけでなく、<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>を指定するため、XAML 構文を使用する分離コード ファイルで<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9e866-137">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span> <span data-ttu-id="9e866-138">次の XAML コードを設定する方法を示しています、<xref:System.Windows.Ink.DrawingAttributes.Color%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9e866-138">The following XAML code demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="9e866-139">このコードを使用するには、Visual Studio 2005 で "HelloInkCanvas" という新しい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e866-139">To use this code, create a new [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] project called "HelloInkCanvas" in Visual Studio 2005.</span></span> <span data-ttu-id="9e866-140">Window1.xaml ファイルのコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9e866-140">Replace the code in the Window1.xaml file with the following code.</span></span>  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="9e866-141">次に、以下のボタン イベント ハンドラーを、分離コード ファイルの Window1 クラス内に追加します。</span><span class="sxs-lookup"><span data-stu-id="9e866-141">Next, add the following button event handlers to the code behind file, inside the Window1 class.</span></span>  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 <span data-ttu-id="9e866-142">このコードのコピー後に、Microsoft Visual Studio 2005 で **F5** キーを押し、デバッガーでプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="9e866-142">After copying this code, press **F5** in Microsoft Visual Studio 2005 to run the program in the debugger.</span></span>  
  
 <span data-ttu-id="9e866-143">通知方法、<xref:System.Windows.Controls.StackPanel>ボタンの上に配置します。、<xref:System.Windows.Controls.InkCanvas>です。</span><span class="sxs-lookup"><span data-stu-id="9e866-143">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="9e866-144">ボタンの上にインクをしようとする場合、<xref:System.Windows.Controls.InkCanvas>を収集し、ボタンの背景にインクをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="9e866-144">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="9e866-145">これは、ボタンがあるため、<xref:System.Windows.Controls.InkCanvas>子とは対照的です。</span><span class="sxs-lookup"><span data-stu-id="9e866-145">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="9e866-146">また、ボタンは z オーダーの上位に位置するため、インクはその背後で描画されます。</span><span class="sxs-lookup"><span data-stu-id="9e866-146">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e866-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e866-147">See Also</span></span>  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
