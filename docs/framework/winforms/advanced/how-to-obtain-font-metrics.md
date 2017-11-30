---
title: "方法 : フォント メトリックを取得する"
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
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b45f3f903c02d056fc457b652b01fb7b59413a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-font-metrics"></a><span data-ttu-id="5b5ca-102">方法 : フォント メトリックを取得する</span><span class="sxs-lookup"><span data-stu-id="5b5ca-102">How to: Obtain Font Metrics</span></span>
<span data-ttu-id="5b5ca-103"><xref:System.Drawing.FontFamily>クラスがファミリ/スタイルの特定の組み合わせに対するさまざまなメトリックを取得する次のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-103">The <xref:System.Drawing.FontFamily> class provides the following methods that retrieve various metrics for a particular family/style combination:</span></span>  
  
-   <span data-ttu-id="5b5ca-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="5b5ca-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="5b5ca-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="5b5ca-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="5b5ca-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="5b5ca-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="5b5ca-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="5b5ca-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span></span>  
  
 <span data-ttu-id="5b5ca-108">これらのメソッドによって返される数値をフォント デザイン単位でのサイズと、特定のユニットの独立したに<xref:System.Drawing.Font>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-108">The numbers returned by these methods are in font design units, so they are independent of the size and units of a particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="5b5ca-109">次の図は、さまざまな指標を示します。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-109">The following illustration shows the various metrics.</span></span>  
  
 <span data-ttu-id="5b5ca-110">![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span><span class="sxs-lookup"><span data-stu-id="5b5ca-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b5ca-111">例</span><span class="sxs-lookup"><span data-stu-id="5b5ca-111">Example</span></span>  
 <span data-ttu-id="5b5ca-112">次の例では、Arial フォント ファミリの標準のスタイルのメトリックを表示します。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-112">The following example displays the metrics for the regular style of the Arial font family.</span></span> <span data-ttu-id="5b5ca-113">コードでも作成、 <xref:System.Drawing.Font> 16 ピクセルのサイズと、その特定のピクセル単位のメトリックが表示されます (Arial ファミリに基づく) オブジェクト<xref:System.Drawing.Font>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-113">The code also creates a <xref:System.Drawing.Font> object (based on the Arial family) with size 16 pixels and displays the metrics (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="5b5ca-114">次の図は、コード例の出力を示します。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-114">The following illustration shows the output of the example code.</span></span>  
  
 <span data-ttu-id="5b5ca-115">![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span><span class="sxs-lookup"><span data-stu-id="5b5ca-115">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span></span>  
  
 <span data-ttu-id="5b5ca-116">前の図では出力の最初の 2 つの行に注意してください。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-116">Note the first two lines of output in the preceding illustration.</span></span> <span data-ttu-id="5b5ca-117"><xref:System.Drawing.Font>オブジェクトは、16 のサイズを返しますと<xref:System.Drawing.FontFamily>オブジェクトは、em 高の 2,048 を返します。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-117">The <xref:System.Drawing.Font> object returns a size of 16, and the <xref:System.Drawing.FontFamily> object returns an em height of 2,048.</span></span> <span data-ttu-id="5b5ca-118">これら 2 つの数値 (16 と 2,048) は、キーをフォント デザイン単位と、単位 (この場合はピクセル) の間の変換、<xref:System.Drawing.Font>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-118">These two numbers (16 and 2,048) are the key to converting between font design units and the units (in this case pixels) of the <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="5b5ca-119">たとえば、次のようにアセントをデザイン単位からピクセルに変換できます。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-119">For example, you can convert the ascent from design units to pixels as follows:</span></span>  
  
 <span data-ttu-id="5b5ca-120">![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span><span class="sxs-lookup"><span data-stu-id="5b5ca-120">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span></span>  
  
 <span data-ttu-id="5b5ca-121">次のコードを配置テキスト垂直方向に設定して、<xref:System.Drawing.PointF.Y%2A>のデータ メンバー、<xref:System.Drawing.PointF>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-121">The following code positions text vertically by setting the <xref:System.Drawing.PointF.Y%2A> data member of a <xref:System.Drawing.PointF> object.</span></span> <span data-ttu-id="5b5ca-122">Y 座標が増加して`font.Height`テキストの改行します。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-122">The y-coordinate is increased by `font.Height` for each new line of text.</span></span> <span data-ttu-id="5b5ca-123"><xref:System.Drawing.Font.Height%2A>のプロパティ、<xref:System.Drawing.Font>オブジェクトは、その特定の行間 (ピクセル単位) でを返します<xref:System.Drawing.Font>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-123">The <xref:System.Drawing.Font.Height%2A> property of a <xref:System.Drawing.Font> object returns the line spacing (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="5b5ca-124">この例では、によって返される数<xref:System.Drawing.Font.Height%2A>は 19 です。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-124">In this example, the number returned by <xref:System.Drawing.Font.Height%2A> is 19.</span></span> <span data-ttu-id="5b5ca-125">これが行間隔をピクセル単位に変換することによって得られる数値 (整数に切り上げられます) と同じであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-125">Note that this is the same as the number (rounded up to an integer) obtained by converting the line-spacing metric to pixels.</span></span>  
  
 <span data-ttu-id="5b5ca-126">Em 高 (サイズまたは em サイズとも呼ばれます) がアセントと降下の合計ではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-126">Note that the em height (also called size or em size) is not the sum of the ascent and the descent.</span></span> <span data-ttu-id="5b5ca-127">アセントと降下の合計には、セルの高さが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-127">The sum of the ascent and the descent is called the cell height.</span></span> <span data-ttu-id="5b5ca-128">内部の先頭から引いたセルの高さは、em の高さと同じです。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-128">The cell height minus the internal leading is equal to the em height.</span></span> <span data-ttu-id="5b5ca-129">セルの高さと外部の先頭には、線の間隔と同じです。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-129">The cell height plus the external leading is equal to the line spacing.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5b5ca-130">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="5b5ca-130">Compiling the Code</span></span>  
 <span data-ttu-id="5b5ca-131">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="5b5ca-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5ca-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b5ca-132">See Also</span></span>  
 [<span data-ttu-id="5b5ca-133">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="5b5ca-133">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="5b5ca-134">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="5b5ca-134">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
