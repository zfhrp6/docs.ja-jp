---
title: GDI+ でのブラシと塗りつぶされた図形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 9475518a5f0422e0eac1ec521088071bb4d1c885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="65410-102">GDI+ でのブラシと塗りつぶされた図形</span><span class="sxs-lookup"><span data-stu-id="65410-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="65410-103">四角形や楕円など、閉じた図形は、概要と、内部で構成されます。</span><span class="sxs-lookup"><span data-stu-id="65410-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="65410-104">ペンを使用して、アウトラインが描画され、内部はブラシと塗りつぶされます。</span><span class="sxs-lookup"><span data-stu-id="65410-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="65410-105"> 閉じた図形の内部を塗りつぶすときのいくつかのブラシ クラスを提供します。 <xref:System.Drawing.SolidBrush>、 <xref:System.Drawing.Drawing2D.HatchBrush>、 <xref:System.Drawing.TextureBrush>、 <xref:System.Drawing.Drawing2D.LinearGradientBrush>、および<xref:System.Drawing.Drawing2D.PathGradientBrush>です。</span><span class="sxs-lookup"><span data-stu-id="65410-105"> provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="65410-106">継承するすべてのクラス、<xref:System.Drawing.Brush>クラスです。</span><span class="sxs-lookup"><span data-stu-id="65410-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="65410-107">次の図は、四角形とソリッド ブラシ、ハッチ ブラシを使用して塗りつぶした楕円を示します。</span><span class="sxs-lookup"><span data-stu-id="65410-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="65410-108">![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="65410-108">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="65410-109">ソリッド ブラシ</span><span class="sxs-lookup"><span data-stu-id="65410-109">Solid Brushes</span></span>  
 <span data-ttu-id="65410-110">閉じた図形を塗りつぶす必要がありますのインスタンス、<xref:System.Drawing.Graphics>クラスおよび<xref:System.Drawing.Brush>です。</span><span class="sxs-lookup"><span data-stu-id="65410-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="65410-111">インスタンス、<xref:System.Drawing.Graphics>クラスなど、メソッドを提供<xref:System.Drawing.Graphics.FillRectangle%2A>と<xref:System.Drawing.Graphics.FillEllipse%2A>、および<xref:System.Drawing.Brush>の色やパターンなど、塗りつぶしの属性を格納します。</span><span class="sxs-lookup"><span data-stu-id="65410-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="65410-112"><xref:System.Drawing.Brush> Fill メソッドに引数の 1 つとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="65410-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="65410-113">次のコード例では、楕円を純色の赤に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="65410-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  <span data-ttu-id="65410-114">前の例では、ブラシが型で<xref:System.Drawing.SolidBrush>から継承される<xref:System.Drawing.Brush>です。</span><span class="sxs-lookup"><span data-stu-id="65410-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="65410-115">ハッチ ブラシ</span><span class="sxs-lookup"><span data-stu-id="65410-115">Hatch Brushes</span></span>  
 <span data-ttu-id="65410-116">ハッチ ブラシを使用して図形を塗りつぶすときは、前景の色、背景色と陰影のスタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="65410-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="65410-117">前景色、陰影の色であります。</span><span class="sxs-lookup"><span data-stu-id="65410-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="65410-118"> 50 以上の陰影のスタイル; は、します。次の図に示すように 3 つのスタイルが<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>、 <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>、および<xref:System.Drawing.Drawing2D.HatchStyle.Cross>です。</span><span class="sxs-lookup"><span data-stu-id="65410-118"> provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="65410-119">![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="65410-119">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="65410-120">テクスチャ ブラシ</span><span class="sxs-lookup"><span data-stu-id="65410-120">Texture Brushes</span></span>  
 <span data-ttu-id="65410-121">テクスチャ ブラシを使用して、ビットマップに格納されているパターンで図形を塗りつぶすことができます。</span><span class="sxs-lookup"><span data-stu-id="65410-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="65410-122">たとえば、次の図は、というディスク ファイルに格納されている`MyTexture.bmp`です。</span><span class="sxs-lookup"><span data-stu-id="65410-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="65410-123">![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="65410-123">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="65410-124">次のコード例に格納されている画像の繰り返しで、省略記号を入力する方法を示しています。`MyTexture.bmp`です。</span><span class="sxs-lookup"><span data-stu-id="65410-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="65410-125">次の図は、塗りつぶされた楕円を示します。</span><span class="sxs-lookup"><span data-stu-id="65410-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="65410-126">![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="65410-126">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="65410-127">グラデーション ブラシ</span><span class="sxs-lookup"><span data-stu-id="65410-127">Gradient Brushes</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="65410-128"> グラデーション ブラシの 2 種類の説明: 線形とパス。</span><span class="sxs-lookup"><span data-stu-id="65410-128"> provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="65410-129">線形グラデーション ブラシを使用して、図形を塗りつぶす色が徐々 に水平、垂直方向には、図形間で移動すると、または対角線方向に変化することができます。</span><span class="sxs-lookup"><span data-stu-id="65410-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="65410-130">次のコード例では、楕円の左端から右端に移動すると、青から緑色に変化する水平グラデーション ブラシで楕円を塗りつぶす方法を示します。</span><span class="sxs-lookup"><span data-stu-id="65410-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="65410-131">次の図は、塗りつぶされた楕円を示します。</span><span class="sxs-lookup"><span data-stu-id="65410-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="65410-132">![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="65410-132">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="65410-133">端に図形の中心から移動すると、色を変更するのには、パス グラデーション ブラシを構成できます。</span><span class="sxs-lookup"><span data-stu-id="65410-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="65410-134">![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="65410-134">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="65410-135">パス グラデーション ブラシは非常に柔軟なです。</span><span class="sxs-lookup"><span data-stu-id="65410-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="65410-136">グラデーション ブラシ、次の図は徐々 に中央の赤からに変更の頂点で 3 つの異なる色の三角形の塗りつぶしに使用します。</span><span class="sxs-lookup"><span data-stu-id="65410-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="65410-137">![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="65410-137">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65410-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="65410-138">See Also</span></span>  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [<span data-ttu-id="65410-139">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="65410-139">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="65410-140">方法: Windows フォームに塗りつぶした四角形を描画する</span><span class="sxs-lookup"><span data-stu-id="65410-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [<span data-ttu-id="65410-141">方法: Windows フォームに塗りつぶした楕円を描画する</span><span class="sxs-lookup"><span data-stu-id="65410-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
