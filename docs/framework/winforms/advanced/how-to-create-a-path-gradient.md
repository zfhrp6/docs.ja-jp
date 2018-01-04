---
title: "方法 : パス グラデーションを作成する"
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
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47a70e55d0f5b6197dc7c77b9e95f2279b814737
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-path-gradient"></a><span data-ttu-id="b37b5-102">方法 : パス グラデーションを作成する</span><span class="sxs-lookup"><span data-stu-id="b37b5-102">How to: Create a Path Gradient</span></span>
<span data-ttu-id="b37b5-103"><xref:System.Drawing.Drawing2D.PathGradientBrush>クラスでは、徐々 に変化する色に図形を塗りつぶす方法をカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="b37b5-103">The <xref:System.Drawing.Drawing2D.PathGradientBrush> class allows you to customize the way you fill a shape with gradually changing colors.</span></span> <span data-ttu-id="b37b5-104">たとえば、パスの中央の 1 つの色とパスの境界に別の色を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b37b5-104">For example, you can specify one color for the center of a path and another color for the boundary of a path.</span></span> <span data-ttu-id="b37b5-105">別の色は、各パスの境界上にある点も指定できます。</span><span class="sxs-lookup"><span data-stu-id="b37b5-105">You can also specify separate colors for each of several points along the boundary of a path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b37b5-106">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、一連の直線と曲線で保持されている場合、パスを<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b37b5-106">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a path is a sequence of lines and curves maintained by a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="b37b5-107">詳細については[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、パスを参照してください[GDI + でのグラフィックス パス](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)と[図面のパスの作成および](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)です。</span><span class="sxs-lookup"><span data-stu-id="b37b5-107">For more information about [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] paths, see [Graphics Paths in GDI+](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md) and [Constructing and Drawing Paths](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md).</span></span>  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a><span data-ttu-id="b37b5-108">パス グラデーションを使用して、省略記号を入力するには</span><span class="sxs-lookup"><span data-stu-id="b37b5-108">To fill an ellipse with a path gradient</span></span>  
  
-   <span data-ttu-id="b37b5-109">次の例では、パス グラデーション ブラシで楕円を塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="b37b5-109">The following example fills an ellipse with a path gradient brush.</span></span> <span data-ttu-id="b37b5-110">中心の色を青に設定され、境界の色がアクアに設定されます。</span><span class="sxs-lookup"><span data-stu-id="b37b5-110">The center color is set to blue and the boundary color is set to aqua.</span></span> <span data-ttu-id="b37b5-111">次の図は、塗りつぶされた楕円を示します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-111">The following illustration shows the filled ellipse.</span></span>  
  
     <span data-ttu-id="b37b5-112">![グラデーション パス](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")</span><span class="sxs-lookup"><span data-stu-id="b37b5-112">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")</span></span>  
  
     <span data-ttu-id="b37b5-113">既定では、パス グラデーション ブラシは、パスの境界の外側には拡張されません。</span><span class="sxs-lookup"><span data-stu-id="b37b5-113">By default, a path gradient brush does not extend outside the boundary of the path.</span></span> <span data-ttu-id="b37b5-114">パスの境界を越える図形を塗りつぶすパス グラデーション ブラシを使用する場合、パスの外側、画面の領域は埋められません。</span><span class="sxs-lookup"><span data-stu-id="b37b5-114">If you use the path gradient brush to fill a figure that extends beyond the boundary of the path, the area of the screen outside the path will not be filled.</span></span>  
  
     <span data-ttu-id="b37b5-115">次の図に変更する場合の対処、<xref:System.Drawing.Graphics.FillEllipse%2A>で次のコードを呼び出す`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`です。</span><span class="sxs-lookup"><span data-stu-id="b37b5-115">The following illustration shows what happens if you change the <xref:System.Drawing.Graphics.FillEllipse%2A> call in the following code to `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`.</span></span>  
  
     <span data-ttu-id="b37b5-116">![グラデーション パス](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")</span><span class="sxs-lookup"><span data-stu-id="b37b5-116">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     <span data-ttu-id="b37b5-117">前のコード例が、Windows フォームで使用するために設計されていて、必要があります、 <xref:System.Windows.Forms.PaintEventArgs> e、これは、パラメーターの<xref:System.Windows.Forms.PaintEventHandler>します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-117">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> e, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
### <a name="to-specify-points-on-the-boundary"></a><span data-ttu-id="b37b5-118">境界でポイントを指定するには</span><span class="sxs-lookup"><span data-stu-id="b37b5-118">To specify points on the boundary</span></span>  
  
-   <span data-ttu-id="b37b5-119">次の例では、星型のパスからパス グラデーション ブラシを構築します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-119">The following example constructs a path gradient brush from a star-shaped path.</span></span> <span data-ttu-id="b37b5-120">コード セット、<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>赤に星の重心で色を設定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="b37b5-120">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> property, which sets the color at the centroid of the star to red.</span></span> <span data-ttu-id="b37b5-121">コードを設定してから、<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>プロパティをさまざまな色を指定する (に格納されている、`colors`配列) 内の個々 の時点で、`points`配列。</span><span class="sxs-lookup"><span data-stu-id="b37b5-121">Then the code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> property to specify various colors (stored in the `colors` array) at the individual points in the `points` array.</span></span> <span data-ttu-id="b37b5-122">最後のコード ステートメントは、パス グラデーション ブラシで星型のパスを設定します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-122">The final code statement fills the star-shaped path with the path gradient brush.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   <span data-ttu-id="b37b5-123">次の例がパス グラデーションなしを描画する<xref:System.Drawing.Drawing2D.GraphicsPath>コード内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b37b5-123">The following example draws a path gradient without a <xref:System.Drawing.Drawing2D.GraphicsPath> object in the code.</span></span> <span data-ttu-id="b37b5-124">特定<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>コンス トラクターの例では、点の配列を受け取りますは必要ありません、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b37b5-124">The particular <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> constructor in the example receives an array of points but does not require a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="b37b5-125">また、<xref:System.Drawing.Drawing2D.PathGradientBrush>パスではなく、四角形の塗りつぶしに使用します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-125">Also, note that the <xref:System.Drawing.Drawing2D.PathGradientBrush> is used to fill a rectangle, not a path.</span></span> <span data-ttu-id="b37b5-126">四角形は、ブラシを定義するブラシで描画四角形の一部がないようにするために使用する閉じたパスよりも大きくなります。</span><span class="sxs-lookup"><span data-stu-id="b37b5-126">The rectangle is larger than the closed path used to define the brush, so some of the rectangle is not painted by the brush.</span></span> <span data-ttu-id="b37b5-127">次の図は、四角形 (点線) およびパス グラデーション ブラシで描画された四角形の部分を示します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-127">The following illustration shows the rectangle (dotted line) and the portion of the rectangle painted by the path gradient brush.</span></span>  
  
     <span data-ttu-id="b37b5-128">![グラデーション](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")</span><span class="sxs-lookup"><span data-stu-id="b37b5-128">![Gradient](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a><span data-ttu-id="b37b5-129">パス グラデーションをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="b37b5-129">To customize a path gradient</span></span>  
  
-   <span data-ttu-id="b37b5-130">パス グラデーション ブラシをカスタマイズする方法の 1 つは設定をその<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b37b5-130">One way to customize a path gradient brush is to set its <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> property.</span></span> <span data-ttu-id="b37b5-131">フォーカス スケールでは、メインのパスの内側にある内部のパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-131">The focus scales specify an inner path that lies inside the main path.</span></span> <span data-ttu-id="b37b5-132">中心点にのみではなく、内部パスの内側、中心の色がどこからでも表示されます。</span><span class="sxs-lookup"><span data-stu-id="b37b5-132">The center color is displayed everywhere inside that inner path rather than only at the center point.</span></span>  
  
     <span data-ttu-id="b37b5-133">次の例では、楕円のパスに基づくパス グラデーション ブラシを作成します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-133">The following example creates a path gradient brush based on an elliptical path.</span></span> <span data-ttu-id="b37b5-134">コードは、境界の色を青を設定、アクア、中心の色に設定し、パス グラデーション ブラシを使用して、楕円のパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-134">The code sets the boundary color to blue, sets the center color to aqua, and then uses the path gradient brush to fill the elliptical path.</span></span>  
  
     <span data-ttu-id="b37b5-135">次に、コードは、パス グラデーション ブラシのフォーカスのスケールを設定します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-135">Next, the code sets the focus scales of the path gradient brush.</span></span> <span data-ttu-id="b37b5-136">0.3、x フォーカス スケールが設定され、0.8 に y フォーカス スケールが設定されています。</span><span class="sxs-lookup"><span data-stu-id="b37b5-136">The x focus scale is set to 0.3, and the y focus scale is set to 0.8.</span></span> <span data-ttu-id="b37b5-137">コードの呼び出し、<xref:System.Drawing.Graphics.TranslateTransform%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクトを後続の呼び出し<xref:System.Drawing.Graphics.FillPath%2A>最初の省略記号の右側に配置される楕円を塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="b37b5-137">The code calls the <xref:System.Drawing.Graphics.TranslateTransform%2A> method of a <xref:System.Drawing.Graphics> object so that the subsequent call to <xref:System.Drawing.Graphics.FillPath%2A> fills an ellipse that sits to the right of the first ellipse.</span></span>  
  
     <span data-ttu-id="b37b5-138">フォーカス スケールの効果を表示するには、メインの省略記号とその中心を共有する小さな楕円を想像してください。</span><span class="sxs-lookup"><span data-stu-id="b37b5-138">To see the effect of the focus scales, imagine a small ellipse that shares its center with the main ellipse.</span></span> <span data-ttu-id="b37b5-139">小さな (内部) 楕円は、メインの楕円 0.3 の要因によって、垂直方向に 0.8 の係数 (その中心) 水平方向に拡張です。</span><span class="sxs-lookup"><span data-stu-id="b37b5-139">The small (inner) ellipse is the main ellipse scaled (about its center) horizontally by a factor of 0.3 and vertically by a factor of 0.8.</span></span> <span data-ttu-id="b37b5-140">外部の楕円の境界から内側の楕円の境界を移動すると、色が徐々 に変化青からアクアにします。</span><span class="sxs-lookup"><span data-stu-id="b37b5-140">As you move from the boundary of the outer ellipse to the boundary of the inner ellipse, the color changes gradually from blue to aqua.</span></span> <span data-ttu-id="b37b5-141">ように内部の楕円の境界から移動するには、共有センター水色の色のままにします。</span><span class="sxs-lookup"><span data-stu-id="b37b5-141">As you move from the boundary of the inner ellipse to the shared center, the color remains aqua.</span></span>  
  
     <span data-ttu-id="b37b5-142">以下のコードの出力を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-142">The following illustration shows the output of the following code.</span></span> <span data-ttu-id="b37b5-143">左側の楕円は、中心点にのみアクアです。</span><span class="sxs-lookup"><span data-stu-id="b37b5-143">The ellipse on the left is aqua only at the center point.</span></span> <span data-ttu-id="b37b5-144">右側の省略記号は、内側のパス内のどこからでもアクアです。</span><span class="sxs-lookup"><span data-stu-id="b37b5-144">The ellipse on the right is aqua everywhere inside the inner path.</span></span>  
  
 <span data-ttu-id="b37b5-145">![グラデーション](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")</span><span class="sxs-lookup"><span data-stu-id="b37b5-145">![Gradient](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a><span data-ttu-id="b37b5-146">補間を使用してカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="b37b5-146">To customize with interpolation</span></span>  
  
-   <span data-ttu-id="b37b5-147">パス グラデーション ブラシをカスタマイズする別の方法では、補間の位置の配列と interpolation 色の配列を指定します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-147">Another way to customize a path gradient brush is to specify an array of interpolation colors and an array of interpolation positions.</span></span>  
  
     <span data-ttu-id="b37b5-148">次の例では、三角形に基づくパス グラデーション ブラシを作成します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-148">The following example creates a path gradient brush based on a triangle.</span></span> <span data-ttu-id="b37b5-149">コード セット、 <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> interpolation 色 (濃い緑、アクア、青) の配列と補間の位置 (0, 0.25, 1) の配列を指定するパス グラデーション ブラシのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="b37b5-149">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> property of the path gradient brush to specify an array of interpolation colors (dark green, aqua, blue) and an array of interpolation positions (0, 0.25, 1).</span></span> <span data-ttu-id="b37b5-150">三角形の境界からの中心点に移動すると、色が徐々 に変化濃い緑から水色に、青にアクアからです。</span><span class="sxs-lookup"><span data-stu-id="b37b5-150">As you move from the boundary of the triangle to the center point, the color changes gradually from dark green to aqua and then from aqua to blue.</span></span> <span data-ttu-id="b37b5-151">青に濃い緑からの距離の 25% で、濃い緑からアクアへの変更が行われます。</span><span class="sxs-lookup"><span data-stu-id="b37b5-151">The change from dark green to aqua happens in 25 percent of the distance from dark green to blue.</span></span>  
  
     <span data-ttu-id="b37b5-152">次の図は、カスタム パス グラデーション ブラシと塗りつぶされた三角形を示します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-152">The following illustration shows the triangle filled with the custom path gradient brush.</span></span>  
  
     <span data-ttu-id="b37b5-153">![グラデーション パス](../../../../docs/framework/winforms/advanced/media/pathgradient4.png "pathgradient4")</span><span class="sxs-lookup"><span data-stu-id="b37b5-153">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient4.png "pathgradient4")</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a><span data-ttu-id="b37b5-154">中心点を設定するには</span><span class="sxs-lookup"><span data-stu-id="b37b5-154">To set the center point</span></span>  
  
-   <span data-ttu-id="b37b5-155">既定では、パス グラデーション ブラシの中心点は、ブラシを構築するために使用されるパスの重心でです。</span><span class="sxs-lookup"><span data-stu-id="b37b5-155">By default, the center point of a path gradient brush is at the centroid of the path used to construct the brush.</span></span> <span data-ttu-id="b37b5-156">中心点の場所を変更するには設定して、<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>のプロパティ、<xref:System.Drawing.Drawing2D.PathGradientBrush>クラスです。</span><span class="sxs-lookup"><span data-stu-id="b37b5-156">You can change the location of the center point by setting the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property of the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
     <span data-ttu-id="b37b5-157">次の例では、楕円に基づくパス グラデーション ブラシを作成します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-157">The following example creates a path gradient brush based on an ellipse.</span></span> <span data-ttu-id="b37b5-158">楕円の中心 (70、35) に設定されているパス グラデーション ブラシの中心点が、(120, 40)。</span><span class="sxs-lookup"><span data-stu-id="b37b5-158">The center of the ellipse is at (70, 35), but the center point of the path gradient brush is set to (120, 40).</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     <span data-ttu-id="b37b5-159">次の図は、塗りつぶされた楕円およびパス グラデーション ブラシの中心点を示します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-159">The following illustration shows the filled ellipse and the center point of the path gradient brush.</span></span>  
  
     <span data-ttu-id="b37b5-160">![グラデーション パス](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")</span><span class="sxs-lookup"><span data-stu-id="b37b5-160">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")</span></span>  
  
-   <span data-ttu-id="b37b5-161">ブラシを構築するために使用されたパスの外側の場所にパス グラデーション ブラシの中心点を設定できます。</span><span class="sxs-lookup"><span data-stu-id="b37b5-161">You can set the center point of a path gradient brush to a location outside the path that was used to construct the brush.</span></span> <span data-ttu-id="b37b5-162">次の例を設定する呼び出しが置き換えられます、<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>前述のコードでのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="b37b5-162">The following example replaces the call to set the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property in the preceding code.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     <span data-ttu-id="b37b5-163">次の図は、この変更により、出力を示します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-163">The following illustration shows the output with this change.</span></span>  
  
     <span data-ttu-id="b37b5-164">![グラデーション パス](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")</span><span class="sxs-lookup"><span data-stu-id="b37b5-164">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")</span></span>  
  
     <span data-ttu-id="b37b5-165">前の図では、楕円の右端にあるポイントは純粋な青 (ただし、これらは非常に類似)</span><span class="sxs-lookup"><span data-stu-id="b37b5-165">In the preceding illustration, the points at the far right of the ellipse are not pure blue (although they are very close).</span></span> <span data-ttu-id="b37b5-166">グラデーションの色は、塗りつぶしの色が純粋な青 (0, 0, 255) をするとポイント (145, 35) に到達してかのように配置されます。</span><span class="sxs-lookup"><span data-stu-id="b37b5-166">The colors in the gradient are positioned as if the fill reached the point (145, 35) where the color would be pure blue (0, 0, 255).</span></span> <span data-ttu-id="b37b5-167">塗りつぶしに到達しないが、(145, 35) ため、そのパス内でのみパス グラデーション ブラシを描画します。</span><span class="sxs-lookup"><span data-stu-id="b37b5-167">But the fill never reaches (145, 35) because a path gradient brush paints only inside its path.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b37b5-168">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b37b5-168">Compiling the Code</span></span>  
 <span data-ttu-id="b37b5-169">前の例は、Windows フォームで使用する用に設計され、必要な<xref:System.Windows.Forms.PaintEventArgs>`e`はのパラメーターである、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="b37b5-169">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b37b5-170">参照</span><span class="sxs-lookup"><span data-stu-id="b37b5-170">See Also</span></span>  
 [<span data-ttu-id="b37b5-171">グラデーション ブラシを使用した図形の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="b37b5-171">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
