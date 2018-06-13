---
title: グローバル変換とローカル変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: a5a8201f0adb44347bdd42081e0263176d179321
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523160"
---
# <a name="global-and-local-transformations"></a><span data-ttu-id="c0615-102">グローバル変換とローカル変換</span><span class="sxs-lookup"><span data-stu-id="c0615-102">Global and Local Transformations</span></span>
<span data-ttu-id="c0615-103">グローバル変換によって描画されたすべての項目に適用される変換とは、指定された<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c0615-103">A global transformation is a transformation that applies to every item drawn by a given <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c0615-104">これに対し、ローカルの変換は、描画する特定の項目に適用される変換です。</span><span class="sxs-lookup"><span data-stu-id="c0615-104">In contrast, a local transformation is a transformation that applies to a specific item to be drawn.</span></span>  
  
## <a name="global-transformations"></a><span data-ttu-id="c0615-105">グローバル変換</span><span class="sxs-lookup"><span data-stu-id="c0615-105">Global Transformations</span></span>  
 <span data-ttu-id="c0615-106">グローバル変換を作成するには、構築、<xref:System.Drawing.Graphics>オブジェクト、および操作し、その<xref:System.Drawing.Graphics.Transform%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c0615-106">To create a global transformation, construct a <xref:System.Drawing.Graphics> object, and then manipulate its <xref:System.Drawing.Graphics.Transform%2A> property.</span></span> <span data-ttu-id="c0615-107"><xref:System.Drawing.Graphics.Transform%2A>プロパティは、<xref:System.Drawing.Drawing2D.Matrix>オブジェクト、アフィン変換の任意のシーケンスを保持できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c0615-107">The <xref:System.Drawing.Graphics.Transform%2A> property is a <xref:System.Drawing.Drawing2D.Matrix> object, so it can hold any sequence of affine transformations.</span></span> <span data-ttu-id="c0615-108">格納されている、変換、<xref:System.Drawing.Graphics.Transform%2A>プロパティはワールド変換と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c0615-108">The transformation stored in the <xref:System.Drawing.Graphics.Transform%2A> property is called the world transformation.</span></span> <span data-ttu-id="c0615-109"><xref:System.Drawing.Graphics>クラス複合のワールド変換を作成するためのいくつかのメソッドを提供します。 <xref:System.Drawing.Graphics.MultiplyTransform%2A>、 <xref:System.Drawing.Graphics.RotateTransform%2A>、 <xref:System.Drawing.Graphics.ScaleTransform%2A>、および<xref:System.Drawing.Graphics.TranslateTransform%2A>です。</span><span class="sxs-lookup"><span data-stu-id="c0615-109">The <xref:System.Drawing.Graphics> class provides several methods for building up a composite world transformation: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, and <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span></span> <span data-ttu-id="c0615-110">次の例は 2 回楕円を描画: ワールド変換と後に 1 回作成する前に一度だけです。</span><span class="sxs-lookup"><span data-stu-id="c0615-110">The following example draws an ellipse twice: once before creating a world transformation and once after.</span></span> <span data-ttu-id="c0615-111">変換は 0.5 の y 方向のスケーリング 50 単位の x 方向の平行移動し、30 度を回転します。</span><span class="sxs-lookup"><span data-stu-id="c0615-111">The transformation first scales by a factor of 0.5 in the y direction, then translates 50 units in the x direction, and then rotates 30 degrees.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 <span data-ttu-id="c0615-112">次の図は、変換に関係する、マトリックスを示します。</span><span class="sxs-lookup"><span data-stu-id="c0615-112">The following illustration shows the matrices involved in the transformation.</span></span>  
  
 <span data-ttu-id="c0615-113">![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span><span class="sxs-lookup"><span data-stu-id="c0615-113">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0615-114">上記の例では、クライアント領域の左上隅にある座標系の原点を基点楕円を回転します。</span><span class="sxs-lookup"><span data-stu-id="c0615-114">In the preceding example, the ellipse is rotated about the origin of the coordinate system, which is at the upper-left corner of the client area.</span></span> <span data-ttu-id="c0615-115">これには、回転の中心楕円異なる結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c0615-115">This produces a different result than rotating the ellipse about its own center.</span></span>  
  
## <a name="local-transformations"></a><span data-ttu-id="c0615-116">ローカル変換</span><span class="sxs-lookup"><span data-stu-id="c0615-116">Local Transformations</span></span>  
 <span data-ttu-id="c0615-117">描画する特定の項目にローカルの変換が適用されます。</span><span class="sxs-lookup"><span data-stu-id="c0615-117">A local transformation applies to a specific item to be drawn.</span></span> <span data-ttu-id="c0615-118">たとえば、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトには、<xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A>メソッドを使用すると、そのパスのデータ ポイントに変換します。</span><span class="sxs-lookup"><span data-stu-id="c0615-118">For example, a <xref:System.Drawing.Drawing2D.GraphicsPath> object has a <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> method that allows you to transform the data points of that path.</span></span> <span data-ttu-id="c0615-119">次の例では、変換なしを含む四角形と回転変換を使用したパスを描画します。</span><span class="sxs-lookup"><span data-stu-id="c0615-119">The following example draws a rectangle with no transformation and a path with a rotation transformation.</span></span> <span data-ttu-id="c0615-120">(ワールド変換がないことを想定)。</span><span class="sxs-lookup"><span data-stu-id="c0615-120">(Assume that there is no world transformation.)</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 <span data-ttu-id="c0615-121">ワールド変換と、さまざまな結果を実現するためにローカルの変換を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="c0615-121">You can combine the world transformation with local transformations to achieve a variety of results.</span></span> <span data-ttu-id="c0615-122">たとえば、座標系を変更して、ローカルの変換を使用して回転新しい座標系で描画されるオブジェクトを拡大/縮小するワールド変換を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c0615-122">For example, you can use the world transformation to revise the coordinate system and use local transformations to rotate and scale objects drawn on the new coordinate system.</span></span>  
  
 <span data-ttu-id="c0615-123">クライアント領域の左端から配信元の 200 ピクセルとクライアント領域の上部から 150 ピクセルを持つ座標系たいとします。</span><span class="sxs-lookup"><span data-stu-id="c0615-123">Suppose you want a coordinate system that has its origin 200 pixels from the left edge of the client area and 150 pixels from the top of the client area.</span></span> <span data-ttu-id="c0615-124">さらに、ピクセル、権限、および上向きの y 軸を指している x 軸に単位にすることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="c0615-124">Furthermore, assume that you want the unit of measure to be the pixel, with the x-axis pointing to the right and the y-axis pointing up.</span></span> <span data-ttu-id="c0615-125">既定の座標システムでは、水平軸に沿って、リフレクションを実行する必要があります、下向き、y 軸があります。</span><span class="sxs-lookup"><span data-stu-id="c0615-125">The default coordinate system has the y-axis pointing down, so you need to perform a reflection across the horizontal axis.</span></span> <span data-ttu-id="c0615-126">次の図は、このようなリフレクションのマトリックスを示します。</span><span class="sxs-lookup"><span data-stu-id="c0615-126">The following illustration shows the matrix of such a reflection.</span></span>  
  
 <span data-ttu-id="c0615-127">![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span><span class="sxs-lookup"><span data-stu-id="c0615-127">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span></span>  
  
 <span data-ttu-id="c0615-128">次に、右側に翻訳 200 単位と 150 の単位を実行する必要があると仮定します。</span><span class="sxs-lookup"><span data-stu-id="c0615-128">Next, assume you need to perform a translation 200 units to the right and 150 units down.</span></span>  
  
 <span data-ttu-id="c0615-129">次の例は、上記で説明したのワールド変換を設定して、座標系を確立、<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c0615-129">The following example establishes the coordinate system just described by setting the world transformation of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 <span data-ttu-id="c0615-130">(前の例の最後に配置)、次のコードでは、新しい座標系の原点の左下隅で 1 つの四角形で構成されるパスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c0615-130">The following code (placed at the end of the preceding example) creates a path that consists of a single rectangle with its lower-left corner at the origin of the new coordinate system.</span></span> <span data-ttu-id="c0615-131">四角形は、ローカルの変換なしで 1 回、および変換をローカルに 1 回入力されます。</span><span class="sxs-lookup"><span data-stu-id="c0615-131">The rectangle is filled once with no local transformation and once with a local transformation.</span></span> <span data-ttu-id="c0615-132">ローカルの変換係数 30 ° 回転を続けて 2 で水平方向のスケーリングで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c0615-132">The local transformation consists of a horizontal scaling by a factor of 2 followed by a 30-degree rotation.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 <span data-ttu-id="c0615-133">次の図は、新しい座標系と 2 つの四角形を示します。</span><span class="sxs-lookup"><span data-stu-id="c0615-133">The following illustration shows the new coordinate system and the two rectangles.</span></span>  
  
 <span data-ttu-id="c0615-134">![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span><span class="sxs-lookup"><span data-stu-id="c0615-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0615-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0615-135">See Also</span></span>  
 [<span data-ttu-id="c0615-136">座標系と変換</span><span class="sxs-lookup"><span data-stu-id="c0615-136">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="c0615-137">マネージ GDI+ での変換の使用</span><span class="sxs-lookup"><span data-stu-id="c0615-137">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
