---
title: "方法 : 線形グラデーションを作成する"
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
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbf3b1657a5a6b91ba88a0968b6b92d4e4bdbf0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="f4b96-102">方法 : 線形グラデーションを作成する</span><span class="sxs-lookup"><span data-stu-id="f4b96-102">How to: Create a Linear Gradient</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="f4b96-103">水平方向、垂直方向、および対角線方向の線形グラデーションを提供します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-103"> provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="f4b96-104">既定では、線形グラデーションの色を一様に変更します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="f4b96-105">ただし、色が一様でない方法で変更されるように、線形グラデーションをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="f4b96-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  
  
 <span data-ttu-id="f4b96-106">次の例では、行、楕円、および水平方向の線形グラデーション ブラシを含む四角形を格納します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-106">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
 <span data-ttu-id="f4b96-107"><xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>コンス トラクターは、4 つの引数を受け取ります。 2 つのポイントと 2 つの色。</span><span class="sxs-lookup"><span data-stu-id="f4b96-107">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="f4b96-108">最初のポイント (0, 10) は最初の色 (赤) に関連付けられ、(200, 10) は、2 番目のポイントが 2 番目の色 (青) と関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="f4b96-108">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="f4b96-109">想定されるようから描画される線で、(0, 10) に (200, 10) 徐々 に赤から青に変更します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-109">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="f4b96-110">ポイント (50, 10) と (200, 10) の 10 件が重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="f4b96-110">The 10s in the points (50, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="f4b96-111">2 つの点が同じ 2 つ目の座標にあることが重要なは、それらを結ぶ線は横方向です。</span><span class="sxs-lookup"><span data-stu-id="f4b96-111">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="f4b96-112">楕円および四角形も段階的に変化を 200 に水平方向の座標が 0 から出ると、青、赤です。</span><span class="sxs-lookup"><span data-stu-id="f4b96-112">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="f4b96-113">次の図は、行、楕円、および四角形を示します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-113">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="f4b96-114">色のグラデーション繰り返される自体水平方向の座標が 200 を超えるよう注意してください。</span><span class="sxs-lookup"><span data-stu-id="f4b96-114">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 <span data-ttu-id="f4b96-115">![線形グラデーション](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")</span><span class="sxs-lookup"><span data-stu-id="f4b96-115">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")</span></span>  
  
### <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="f4b96-116">水平方向の線形グラデーションを使用するには</span><span class="sxs-lookup"><span data-stu-id="f4b96-116">To use horizontal linear gradients</span></span>  
  
-   <span data-ttu-id="f4b96-117">3 番目および 4 番目の引数として、それぞれ赤と不透明な青色の不透明なを渡します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-117">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="f4b96-118">色の要素は前の例では 200 の水平方向の座標に水平方向の座標は 0 から移動すると直線的に変更します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-118">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="f4b96-119">たとえば、最初の座標が 0 ~ 200 の範囲の中間に位置ポイントは、0 ~ 255 の範囲の中間に位置が青の要素があります。</span><span class="sxs-lookup"><span data-stu-id="f4b96-119">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="f4b96-120">グラデーションの 1 つの辺によって色が異なるため、他の方法を調整できます。</span><span class="sxs-lookup"><span data-stu-id="f4b96-120"> allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="f4b96-121">黒から次の表に従って赤に変更するグラデーション ブラシを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="f4b96-121">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="f4b96-122">水平方向の座標</span><span class="sxs-lookup"><span data-stu-id="f4b96-122">Horizontal coordinate</span></span>|<span data-ttu-id="f4b96-123">RGB コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f4b96-123">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="f4b96-124">0</span><span class="sxs-lookup"><span data-stu-id="f4b96-124">0</span></span>|<span data-ttu-id="f4b96-125">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="f4b96-125">(0, 0, 0)</span></span>|  
|<span data-ttu-id="f4b96-126">40</span><span class="sxs-lookup"><span data-stu-id="f4b96-126">40</span></span>|<span data-ttu-id="f4b96-127">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="f4b96-127">(128, 0, 0)</span></span>|  
|<span data-ttu-id="f4b96-128">200</span><span class="sxs-lookup"><span data-stu-id="f4b96-128">200</span></span>|<span data-ttu-id="f4b96-129">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="f4b96-129">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="f4b96-130">赤の要素が半分の強さで水平方向の座標が 0 からように、200 の 20% のみである場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="f4b96-130">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="f4b96-131">次の例のセット、<xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A>のプロパティ、<xref:System.Drawing.Drawing2D.LinearGradientBrush>に 3 つの相対強度を 3 つの相対的な位置に関連付けるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f4b96-131">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> property of a <xref:System.Drawing.Drawing2D.LinearGradientBrush> object to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="f4b96-132">前の表のようには、0.5 の相対強度は、0.2 の相対的な位置に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="f4b96-132">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="f4b96-133">コードでは、楕円およびグラデーション ブラシを含む四角形を格納します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-133">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="f4b96-134">次の図は、結果として得られる楕円および四角形を示します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-134">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 <span data-ttu-id="f4b96-135">![線形グラデーション](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")</span><span class="sxs-lookup"><span data-stu-id="f4b96-135">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")</span></span>  
  
### <a name="to-customize-linear-gradients"></a><span data-ttu-id="f4b96-136">線形グラデーションをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="f4b96-136">To customize linear gradients</span></span>  
  
-   <span data-ttu-id="f4b96-137">3 番目および 4 番目の引数として、それぞれ不透明な黒と不透明な赤いを渡します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-137">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="f4b96-138">グラデーション前の例では、水平; されています。色は、水平線のいずれかに沿った移動すると、徐々 に変更します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-138">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="f4b96-139">垂直グラデーションや対角線のグラデーションを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="f4b96-139">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="f4b96-140">次の例に、ポイント (0, 0) と (200, 100) を渡します、<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="f4b96-140">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="f4b96-141">青に関連付けられている (0, 0) に関連付けられている色の緑 (200, 100)。</span><span class="sxs-lookup"><span data-stu-id="f4b96-141">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="f4b96-142">(ペンの幅が 10) を使用した直線と楕円は、線形グラデーション ブラシで埋められます。</span><span class="sxs-lookup"><span data-stu-id="f4b96-142">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="f4b96-143">次の図は、行は、し、省略記号を示します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-143">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="f4b96-144">楕円の色、徐々 にに沿って移動すると行のメモに並列に渡される行には (0, 0) と (200, 100)。</span><span class="sxs-lookup"><span data-stu-id="f4b96-144">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 <span data-ttu-id="f4b96-145">![線形グラデーション](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")</span><span class="sxs-lookup"><span data-stu-id="f4b96-145">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")</span></span>  
  
### <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="f4b96-146">対角線方向の線形グラデーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="f4b96-146">To create diagonal linear gradients</span></span>  
  
-   <span data-ttu-id="f4b96-147">3 番目および 4 番目の引数として、それぞれ不透明青と不透明緑を渡します。</span><span class="sxs-lookup"><span data-stu-id="f4b96-147">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="f4b96-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4b96-148">See Also</span></span>  
 [<span data-ttu-id="f4b96-149">グラデーション ブラシを使用した図形の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="f4b96-149">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [<span data-ttu-id="f4b96-150">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="f4b96-150">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
