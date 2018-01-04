---
title: "GDI+ でのカーディナル スプライン"
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
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b7653e05fff241f05836624ff02273fb8c24ef6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cardinal-splines-in-gdi"></a><span data-ttu-id="7e0f2-102">GDI+ でのカーディナル スプライン</span><span class="sxs-lookup"><span data-stu-id="7e0f2-102">Cardinal Splines in GDI+</span></span>
<span data-ttu-id="7e0f2-103">カーディナル スプラインは、大規模な曲線を形成に参加している個々 の曲線のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-103">A cardinal spline is a sequence of individual curves joined to form a larger curve.</span></span> <span data-ttu-id="7e0f2-104">スプラインは、ポイントおよびテンション パラメーターの配列を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-104">The spline is specified by an array of points and a tension parameter.</span></span> <span data-ttu-id="7e0f2-105">配列内の各ポイントを通過するカーディナル スプラインがスムーズに通過します。ありませんとがった角と曲線のテンションの急激な変化があります。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-105">A cardinal spline passes smoothly through each point in the array; there are no sharp corners and no abrupt changes in the tightness of the curve.</span></span> <span data-ttu-id="7e0f2-106">次の図は、一連のポイントと、セット内の各ポイントを通過するカーディナル スプラインを示します。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-106">The following illustration shows a set of points and a cardinal spline that passes through each point in the set.</span></span>  
  
 <span data-ttu-id="7e0f2-107">![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")</span><span class="sxs-lookup"><span data-stu-id="7e0f2-107">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")</span></span>  
  
## <a name="physical-and-mathematical-splines"></a><span data-ttu-id="7e0f2-108">物理および数学スプライン</span><span class="sxs-lookup"><span data-stu-id="7e0f2-108">Physical and Mathematical Splines</span></span>  
 <span data-ttu-id="7e0f2-109">シン木材やその他の柔軟な資料の物理的なスプラインです。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-109">A physical spline is a thin piece of wood or other flexible material.</span></span> <span data-ttu-id="7e0f2-110">数学的なスプラインの出現により、前に、デザイナーは、物理的なスプラインを曲線の描画に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-110">Before the advent of mathematical splines, designers used physical splines to draw curves.</span></span> <span data-ttu-id="7e0f2-111">デザイナーはスプライン枚の用紙に置き、特定の点のセットに固定します。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-111">A designer would place the spline on a piece of paper and anchor it to a given set of points.</span></span> <span data-ttu-id="7e0f2-112">デザイナーは、曲線をペンや鉛筆とスプラインに沿って描画で作成し、でした。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-112">The designer could then create a curve by drawing along the spline with a pen or pencil.</span></span> <span data-ttu-id="7e0f2-113">指定された一連のポイントは、さまざまな物理スプラインのプロパティによって、曲線を起動できませんでした。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-113">A given set of points could yield a variety of curves, depending on the properties of the physical spline.</span></span> <span data-ttu-id="7e0f2-114">たとえば、曲げに対する抵抗力が強いスプラインでは、非常に柔軟なスプラインよりも異なる曲線と生成されます。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-114">For example, a spline with a high resistance to bending would produce a different curve than an extremely flexible spline.</span></span>  
  
 <span data-ttu-id="7e0f2-115">数学的なスプラインによって生成される、曲線、物理的なスプラインによって生成された 1 回、曲線に似ていますので、数学的なスプライン数式は柔軟な棒プロパティに基づきます。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-115">The formulas for mathematical splines are based on the properties of flexible rods, so the curves produced by mathematical splines are similar to the curves that were once produced by physical splines.</span></span> <span data-ttu-id="7e0f2-116">異なるテンションの物理的なスプライン ポイントの指定されたセットを別の曲線が生成されます、同様テンション パラメーターの値が異なる数学スプラインによって別の曲線ポイントの指定されたセットを通じてが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-116">Just as physical splines of different tension will produce different curves through a given set of points, mathematical splines with different values for the tension parameter will produce different curves through a given set of points.</span></span> <span data-ttu-id="7e0f2-117">次の図は、同じ点のセットに渡される 4 つのカーディナル スプラインを示します。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-117">The following illustration shows four cardinal splines passing through the same set of points.</span></span> <span data-ttu-id="7e0f2-118">各スプラインのテンションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-118">The tension is shown for each spline.</span></span> <span data-ttu-id="7e0f2-119">曲線のポイントの間の最短方法 (直線) を実行するように強制無限の物理的テンション テンション 0 の値が対応しています。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-119">A tension of 0 corresponds to infinite physical tension, forcing the curve to take the shortest way (straight lines) between points.</span></span> <span data-ttu-id="7e0f2-120">1 のテンションは曲げの合計が最低のパスを取得するスプラインをできるように、物理ありませんテンションに対応します。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-120">A tension of 1 corresponds to no physical tension, allowing the spline to take the path of least total bend.</span></span> <span data-ttu-id="7e0f2-121">張力値が 1 より大きい、曲線のように動作圧縮のスプリングより長いパスを取得するプッシュします。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-121">With tension values greater than 1, the curve behaves like a compressed spring, pushed to take a longer path.</span></span>  
  
 <span data-ttu-id="7e0f2-122">![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")</span><span class="sxs-lookup"><span data-stu-id="7e0f2-122">![Cardinal Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")</span></span>  
  
 <span data-ttu-id="7e0f2-123">前の図に 4 つのスプラインは、開始位置に同じ正接回線を共有します。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-123">The four splines in the preceding illustration share the same tangent line at the starting point.</span></span> <span data-ttu-id="7e0f2-124">タンジェントとは、開始点と曲線に沿って次の点を結ぶ線です。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-124">The tangent is the line drawn from the starting point to the next point along the curve.</span></span> <span data-ttu-id="7e0f2-125">同様に、終了位置で共有正接とは、曲線の終点から過去の時点に描画される直線。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-125">Likewise, the shared tangent at the ending point is the line drawn from the ending point to the previous point on the curve.</span></span>  
  
 <span data-ttu-id="7e0f2-126">インスタンスを通過するカーディナル スプラインを描画する必要、<xref:System.Drawing.Graphics>クラス、 <xref:System.Drawing.Pen>、および配列の<xref:System.Drawing.Point>オブジェクトのインスタンス、<xref:System.Drawing.Graphics>クラスを提供、<xref:System.Drawing.Graphics.DrawCurve%2A>スプラインを描画するメソッドと<xref:System.Drawing.Pen>スプライン、線の幅、色などの属性を格納します。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-126">To draw a cardinal spline, you need an instance of the <xref:System.Drawing.Graphics> class, a <xref:System.Drawing.Pen>, and an array of <xref:System.Drawing.Point> objects The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawCurve%2A> method, which draws the spline, and the <xref:System.Drawing.Pen> stores attributes of the spline, such as line width and color.</span></span> <span data-ttu-id="7e0f2-127">配列<xref:System.Drawing.Point>曲線を通じて渡されるポイントがオブジェクトに格納します。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-127">The array of <xref:System.Drawing.Point> objects stores the points that the curve will pass through.</span></span> <span data-ttu-id="7e0f2-128">次のコード例は、内のポイントを通過するカーディナル スプラインを描画する方法を示しています。`myPointArray`です。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-128">The following code example shows how to draw a cardinal spline that passes through the points in `myPointArray`.</span></span> <span data-ttu-id="7e0f2-129">3 番目のパラメーターは、テンションです。</span><span class="sxs-lookup"><span data-stu-id="7e0f2-129">The third parameter is the tension.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="7e0f2-130">参照</span><span class="sxs-lookup"><span data-stu-id="7e0f2-130">See Also</span></span>  
 [<span data-ttu-id="7e0f2-131">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="7e0f2-131">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="7e0f2-132">曲線の作成と描画</span><span class="sxs-lookup"><span data-stu-id="7e0f2-132">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
