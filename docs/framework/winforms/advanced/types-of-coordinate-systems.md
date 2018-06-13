---
title: 座標系の種類
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: ff53942cb90721d5411f99b261f90366d039e151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529754"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="d2a13-102">座標系の種類</span><span class="sxs-lookup"><span data-stu-id="d2a13-102">Types of Coordinate Systems</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="d2a13-103"> 次の 3 つの座標空間を使用して: world、ページ、およびデバイス。</span><span class="sxs-lookup"><span data-stu-id="d2a13-103"> uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="d2a13-104">ワールド座標特定グラフィック世界をモデル化するために使用する座標、.NET Framework のメソッドに渡す座標。</span><span class="sxs-lookup"><span data-stu-id="d2a13-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="d2a13-105">ページ座標は、フォームやコントロールなどの描画サーフェイスで使用される座標系を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a13-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="d2a13-106">デバイスの座標は、画面や枚の用紙など、描画されている物理デバイスで使用される座標です。</span><span class="sxs-lookup"><span data-stu-id="d2a13-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="d2a13-107">呼び出しを行うとき`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`、渡された点、<xref:System.Drawing.Graphics.DrawLine%2A>メソッド —`(0, 0)`と`(160, 80)`— 世界の座標空間にします。</span><span class="sxs-lookup"><span data-stu-id="d2a13-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="d2a13-108">前に[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]画面に線を描画することができます、座標は、変換のシーケンスを通過します。</span><span class="sxs-lookup"><span data-stu-id="d2a13-108">Before [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="d2a13-109">ワールド変換と呼ばれる 1 つの変換は、ページ座標にワールド座標を変換し、ページ変換と呼ばれる別の変換は、ページ座標をデバイス座標に変換します。</span><span class="sxs-lookup"><span data-stu-id="d2a13-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="d2a13-110">座標系と変換</span><span class="sxs-lookup"><span data-stu-id="d2a13-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="d2a13-111">左上隅ではなく、クライアント領域の本体の原点をある座標システムを使用するとします。</span><span class="sxs-lookup"><span data-stu-id="d2a13-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="d2a13-112">たとえば、原点とするクライアント領域の上部から 50 ピクセルとクライアント領域の左端から 100 ピクセルにすることです。</span><span class="sxs-lookup"><span data-stu-id="d2a13-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="d2a13-113">次の図は、このような座標系を示します。</span><span class="sxs-lookup"><span data-stu-id="d2a13-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="d2a13-114">![座標系](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="d2a13-114">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="d2a13-115">呼び出しを行うとき`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`、次の図に示すように行を取得します。</span><span class="sxs-lookup"><span data-stu-id="d2a13-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="d2a13-116">![座標系](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="d2a13-116">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="d2a13-117">3 つの座標空間、行の端点の座標は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d2a13-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2a13-118">世界</span><span class="sxs-lookup"><span data-stu-id="d2a13-118">World</span></span>|<span data-ttu-id="d2a13-119">(0, 0) に (160、80)</span><span class="sxs-lookup"><span data-stu-id="d2a13-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="d2a13-120">ページ</span><span class="sxs-lookup"><span data-stu-id="d2a13-120">Page</span></span>|<span data-ttu-id="d2a13-121">(100, 50) に (260、130)</span><span class="sxs-lookup"><span data-stu-id="d2a13-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="d2a13-122">デバイス</span><span class="sxs-lookup"><span data-stu-id="d2a13-122">Device</span></span>|<span data-ttu-id="d2a13-123">(100, 50) に (260、130)</span><span class="sxs-lookup"><span data-stu-id="d2a13-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="d2a13-124">ページの座標空間にあるクライアント領域の左上隅に原点に注意してください。これは、大文字と小文字を常になります。</span><span class="sxs-lookup"><span data-stu-id="d2a13-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="d2a13-125">測定単位はピクセルであるため、デバイス座標があるページ座標と同じにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="d2a13-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="d2a13-126">ピクセル (たとえば、インチ) 以外に測定単位を設定した場合、デバイスの座標はページ座標から異なるされます。</span><span class="sxs-lookup"><span data-stu-id="d2a13-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="d2a13-127">ワールド変換は、ページ座標にワールド座標をマップに保持されている、<xref:System.Drawing.Graphics.Transform%2A>のプロパティ、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d2a13-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="d2a13-128">前の例では、ワールド変換は、x 軸方向の平行移動 100 単位および y 方向の 50 個のユニットです。</span><span class="sxs-lookup"><span data-stu-id="d2a13-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="d2a13-129">次の例のワールド変換の設定、<xref:System.Drawing.Graphics>オブジェクトを使用している<xref:System.Drawing.Graphics>前の図に示すように線を描画するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d2a13-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="d2a13-130">ページ変換は、デバイスの座標にページ座標をマップします。</span><span class="sxs-lookup"><span data-stu-id="d2a13-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="d2a13-131"><xref:System.Drawing.Graphics>クラスを提供、<xref:System.Drawing.Graphics.PageUnit%2A>と<xref:System.Drawing.Graphics.PageScale%2A>ページ変換を操作するためのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d2a13-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="d2a13-132"><xref:System.Drawing.Graphics>クラスは、2 つの読み取り専用のプロパティも用意されています。<xref:System.Drawing.Graphics.DpiX%2A>と<xref:System.Drawing.Graphics.DpiY%2A>、ディスプレイ デバイスのインチあたりのドット数水平および垂直方向を確認するためです。</span><span class="sxs-lookup"><span data-stu-id="d2a13-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="d2a13-133">使用することができます、<xref:System.Drawing.Graphics.PageUnit%2A>のプロパティ、<xref:System.Drawing.Graphics>ピクセル以外のメジャーの単位を指定するクラス。</span><span class="sxs-lookup"><span data-stu-id="d2a13-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2a13-134">設定することはできません、<xref:System.Drawing.Graphics.PageUnit%2A>プロパティを<xref:System.Drawing.GraphicsUnit.World>、物理的な単位ではないになり、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="d2a13-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="d2a13-135">次の例から行を描画する (0, 0) に (2, 1)、場所、ポイント (2, 1) が 2 インチ右側に、ポイント (0, 0) から 1 インチ下。</span><span class="sxs-lookup"><span data-stu-id="d2a13-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="d2a13-136">ペンを構築するときに、ペンの幅を指定しない、前の例は 1 インチの線を描画します。</span><span class="sxs-lookup"><span data-stu-id="d2a13-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="d2a13-137">2 番目の引数でペンの幅を指定できます、<xref:System.Drawing.Pen>コンス トラクター。</span><span class="sxs-lookup"><span data-stu-id="d2a13-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="d2a13-138">仮定すると、表示デバイスが 96 ドット/インチで水平方向および垂直方向のインチあたりのドット数 96 を持っている、前の例では行の端点座標にある、次は 3 つの座標空間内。</span><span class="sxs-lookup"><span data-stu-id="d2a13-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2a13-139">世界</span><span class="sxs-lookup"><span data-stu-id="d2a13-139">World</span></span>|<span data-ttu-id="d2a13-140">(0, 0) に (2, 1)</span><span class="sxs-lookup"><span data-stu-id="d2a13-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="d2a13-141">ページ</span><span class="sxs-lookup"><span data-stu-id="d2a13-141">Page</span></span>|<span data-ttu-id="d2a13-142">(0, 0) に (2, 1)</span><span class="sxs-lookup"><span data-stu-id="d2a13-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="d2a13-143">デバイス</span><span class="sxs-lookup"><span data-stu-id="d2a13-143">Device</span></span>|<span data-ttu-id="d2a13-144">(0, 0, に (192、96)</span><span class="sxs-lookup"><span data-stu-id="d2a13-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="d2a13-145">世界の座標空間の原点がクライアント領域の左上隅にあるため、ページ座標は、世界の座標と同じに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d2a13-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="d2a13-146">さまざまな効果を実現するために、world とページ変換を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="d2a13-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="d2a13-147">たとえば、メジャーの単位として (インチ) を使用して、クライアント領域とクライアント領域の上端からの 1/2 インチの左端からの 2 インチ、座標系の原点です。</span><span class="sxs-lookup"><span data-stu-id="d2a13-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="d2a13-148">次の例は、ワールド変換とページ変換の<xref:System.Drawing.Graphics>オブジェクトおよびから線を描画し、(0, 0) に (2, 1)。</span><span class="sxs-lookup"><span data-stu-id="d2a13-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="d2a13-149">次の図は、行と座標系を示します。</span><span class="sxs-lookup"><span data-stu-id="d2a13-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="d2a13-150">![座標系](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="d2a13-150">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="d2a13-151">仮定すると、表示デバイスが 96 ドット/インチで水平方向および垂直方向のインチあたりのドット数 96 を持っている、前の例では行の端点座標にある、次は 3 つの座標空間内。</span><span class="sxs-lookup"><span data-stu-id="d2a13-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2a13-152">世界</span><span class="sxs-lookup"><span data-stu-id="d2a13-152">World</span></span>|<span data-ttu-id="d2a13-153">(0, 0) に (2, 1)</span><span class="sxs-lookup"><span data-stu-id="d2a13-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="d2a13-154">ページ</span><span class="sxs-lookup"><span data-stu-id="d2a13-154">Page</span></span>|<span data-ttu-id="d2a13-155">(2, 0.5) に (4, 1.5)</span><span class="sxs-lookup"><span data-stu-id="d2a13-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="d2a13-156">デバイス</span><span class="sxs-lookup"><span data-stu-id="d2a13-156">Device</span></span>|<span data-ttu-id="d2a13-157">(192, 48) に (384, 144)</span><span class="sxs-lookup"><span data-stu-id="d2a13-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2a13-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2a13-158">See Also</span></span>  
 [<span data-ttu-id="d2a13-159">座標系と変換</span><span class="sxs-lookup"><span data-stu-id="d2a13-159">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="d2a13-160">変換の行列表現</span><span class="sxs-lookup"><span data-stu-id="d2a13-160">Matrix Representation of Transformations</span></span>](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
