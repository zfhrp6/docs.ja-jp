---
title: "直線と曲線のアンチエイリアシング"
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
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8552f185a93b688555dbcfab3da9d28d9bfde6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="92f0d-102">直線と曲線のアンチエイリアシング</span><span class="sxs-lookup"><span data-stu-id="92f0d-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="92f0d-103">使用すると[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]線を描画するには、開始点と、1 行の終了点を提供するが、行に個々 のピクセルに関する情報を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="92f0d-103">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="92f0d-104">どのピクセルはオンにする特定のディスプレイ デバイスで、行の表示を決定するディスプレイ ドライバー ソフトウェアと連携して動作します。</span><span class="sxs-lookup"><span data-stu-id="92f0d-104"> works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="92f0d-105">エイリアス</span><span class="sxs-lookup"><span data-stu-id="92f0d-105">Aliasing</span></span>  
 <span data-ttu-id="92f0d-106">(4, 2) のポイントからは点 (16, 10) に移動するまっすぐ赤い線を検討してください。</span><span class="sxs-lookup"><span data-stu-id="92f0d-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="92f0d-107">座標系では、左上隅の原点とメジャーの単位がピクセルであることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="92f0d-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="92f0d-108">X 軸がダウンして、右、y 軸を指していると想定されます。</span><span class="sxs-lookup"><span data-stu-id="92f0d-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="92f0d-109">次の図は、色付きの背景に描画される赤色の線の拡大表示を示します。</span><span class="sxs-lookup"><span data-stu-id="92f0d-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="92f0d-110">![行、(アンチエイリアシングなし)](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="92f0d-110">![Line, no antialiasing](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="92f0d-111">行を表示するために使用される赤いピクセルは不透明です。</span><span class="sxs-lookup"><span data-stu-id="92f0d-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="92f0d-112">行には、部分的に透明はありません。</span><span class="sxs-lookup"><span data-stu-id="92f0d-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="92f0d-113">この種類の行の表示は、行、ギザギザと行では、階段します。</span><span class="sxs-lookup"><span data-stu-id="92f0d-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="92f0d-114">この手法を表す線、階段のエイリアスと呼びます階段は、理論上の行のエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="92f0d-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="92f0d-115">アンチエイリアシング</span><span class="sxs-lookup"><span data-stu-id="92f0d-115">Antialiasing</span></span>  
 <span data-ttu-id="92f0d-116">不透明なピクセルおよび半透明なピクセルを使用して行を表示するためのより高度な手法が含まれます。</span><span class="sxs-lookup"><span data-stu-id="92f0d-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="92f0d-117">ピクセルが、純粋な赤に設定または赤の背景色をブレンド、閉じる方法によっては行にします。</span><span class="sxs-lookup"><span data-stu-id="92f0d-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="92f0d-118">この種類のレンダリングのアンチエイリアシングと人間の目がより滑らかとして認識するための行の結果します。</span><span class="sxs-lookup"><span data-stu-id="92f0d-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="92f0d-119">次の図は、アンチ エイリアス処理された行を生成するためにバック グラウンドで特定のピクセルを統合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="92f0d-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="92f0d-120">![アンチエイリアシング線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="92f0d-120">![Antialiasing a Line](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="92f0d-121">スムージングとも呼ばれます (アンチエイリアシング) は、曲線にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="92f0d-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="92f0d-122">次の図は、平滑化された楕円の拡大表示を示します。</span><span class="sxs-lookup"><span data-stu-id="92f0d-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="92f0d-123">![アンチエイリアシング曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="92f0d-123">![Antialiasing Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="92f0d-124">次の図は、実際のサイズ、1 回 (アンチエイリアシング) と 1 回 (アンチエイリアシング) で同じ楕円を示します。</span><span class="sxs-lookup"><span data-stu-id="92f0d-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="92f0d-125">![アンチエイリアシング例](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="92f0d-125">![Antialiasing example](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="92f0d-126">直線と曲線のアンチエイリアシングの使用を描画するには、インスタンスを作成する、<xref:System.Drawing.Graphics>クラスし、設定、<xref:System.Drawing.Graphics.SmoothingMode%2A>プロパティを<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>または<xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>です。</span><span class="sxs-lookup"><span data-stu-id="92f0d-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="92f0d-127">描画メソッドの 1 つを同じに呼び出して<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="92f0d-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="92f0d-128">参照</span><span class="sxs-lookup"><span data-stu-id="92f0d-128">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [<span data-ttu-id="92f0d-129">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="92f0d-129">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="92f0d-130">方法: テキストでのアンチエイリアシングの使用</span><span class="sxs-lookup"><span data-stu-id="92f0d-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
