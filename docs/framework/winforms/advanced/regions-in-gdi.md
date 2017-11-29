---
title: "GDI+ での領域"
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
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0525e7b58353909d41e5367aa52a17aa56bcd77c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="regions-in-gdi"></a><span data-ttu-id="465b6-102">GDI+ での領域</span><span class="sxs-lookup"><span data-stu-id="465b6-102">Regions in GDI+</span></span>
<span data-ttu-id="465b6-103">領域は、出力デバイスの表示領域の一部です。</span><span class="sxs-lookup"><span data-stu-id="465b6-103">A region is a portion of the display area of an output device.</span></span> <span data-ttu-id="465b6-104">領域には、単純な (1 つの四角形) または複合型 (多角形と閉じた曲線の組み合わせ) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="465b6-104">Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves).</span></span> <span data-ttu-id="465b6-105">次の図は、2 つの領域を示します: 四角形は、1 つ構築され、パスから構築されました。</span><span class="sxs-lookup"><span data-stu-id="465b6-105">The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.</span></span>  
  
 <span data-ttu-id="465b6-106">![地域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span><span class="sxs-lookup"><span data-stu-id="465b6-106">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span></span>  
  
## <a name="using-regions"></a><span data-ttu-id="465b6-107">領域の使用</span><span class="sxs-lookup"><span data-stu-id="465b6-107">Using Regions</span></span>  
 <span data-ttu-id="465b6-108">クリッピング頻繁に使用され、ヒット テスト領域にします。</span><span class="sxs-lookup"><span data-stu-id="465b6-108">Regions are often used for clipping and hit testing.</span></span> <span data-ttu-id="465b6-109">クリッピングでは、更新する必要がある部分では通常、表示領域の特定の領域に描画を制限します。</span><span class="sxs-lookup"><span data-stu-id="465b6-109">Clipping involves restricting drawing to a certain region of the display area, usually the portion that needs to be updated.</span></span> <span data-ttu-id="465b6-110">ヒット テストするには、マウス ボタンが押されたときにカーソルが、画面の特定の領域にするかどうかを判断するチェックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="465b6-110">Hit testing involves checking to determine whether the cursor is in a certain region of the screen when a mouse button is pressed.</span></span>  
  
 <span data-ttu-id="465b6-111">四角形またはパスから地域を構築できます。</span><span class="sxs-lookup"><span data-stu-id="465b6-111">You can construct a region from a rectangle or a path.</span></span> <span data-ttu-id="465b6-112">既存の領域を組み合わせることによって、複雑な領域を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="465b6-112">You can also create complex regions by combining existing regions.</span></span> <span data-ttu-id="465b6-113"><xref:System.Drawing.Region>クラスは領域を結合するための次のメソッドを提供します。 <xref:System.Drawing.Region.Intersect%2A>、 <xref:System.Drawing.Region.Union%2A>、 <xref:System.Drawing.Region.Xor%2A>、 <xref:System.Drawing.Region.Exclude%2A>、および<xref:System.Drawing.Region.Complement%2A>です。</span><span class="sxs-lookup"><span data-stu-id="465b6-113">The <xref:System.Drawing.Region> class provides the following methods for combining regions: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, and <xref:System.Drawing.Region.Complement%2A>.</span></span>  
  
 <span data-ttu-id="465b6-114">2 つのリージョンの積集合は、両方の地域に属しているすべての点のセットです。</span><span class="sxs-lookup"><span data-stu-id="465b6-114">The intersection of two regions is the set of all points belonging to both regions.</span></span> <span data-ttu-id="465b6-115">共用体は、1 つまたはもう一方または両方の地域に属しているすべての点のセットです。</span><span class="sxs-lookup"><span data-stu-id="465b6-115">The union is the set of all points belonging to one or the other or both regions.</span></span> <span data-ttu-id="465b6-116">領域の補完は、すべてのポイントの領域に含まれていないセットです。</span><span class="sxs-lookup"><span data-stu-id="465b6-116">The complement of a region is the set of all points that are not in the region.</span></span> <span data-ttu-id="465b6-117">次の図は、積集合と前の図に示すように 2 つのリージョンの和集合を示します。</span><span class="sxs-lookup"><span data-stu-id="465b6-117">The following illustration shows the intersection and union of the two regions shown in the preceding illustration.</span></span>  
  
 <span data-ttu-id="465b6-118">![地域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span><span class="sxs-lookup"><span data-stu-id="465b6-118">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span></span>  
  
 <span data-ttu-id="465b6-119"><xref:System.Drawing.Region.Xor%2A>地域のペアに適用される方法に属する 1 つの領域、または両方が、他のすべてのポイントを格納する領域を生成します。</span><span class="sxs-lookup"><span data-stu-id="465b6-119">The <xref:System.Drawing.Region.Xor%2A> method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both.</span></span> <span data-ttu-id="465b6-120"><xref:System.Drawing.Region.Exclude%2A>地域のペアに適用される方法は 2 つ目の領域に含まれていない最初の領域内のすべてのポイントを含む領域を生成します。</span><span class="sxs-lookup"><span data-stu-id="465b6-120">The <xref:System.Drawing.Region.Exclude%2A> method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region.</span></span> <span data-ttu-id="465b6-121">次の図に、適用することに起因する地域、<xref:System.Drawing.Region.Xor%2A>と<xref:System.Drawing.Region.Exclude%2A>メソッドをこのトピックの冒頭に示した 2 つの領域。</span><span class="sxs-lookup"><span data-stu-id="465b6-121">The following illustration shows the regions that result from applying the <xref:System.Drawing.Region.Xor%2A> and <xref:System.Drawing.Region.Exclude%2A> methods to the two regions shown at the beginning of this topic.</span></span>  
  
 <span data-ttu-id="465b6-122">![地域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span><span class="sxs-lookup"><span data-stu-id="465b6-122">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span></span>  
  
 <span data-ttu-id="465b6-123">領域を塗りつぶす必要があります、<xref:System.Drawing.Graphics>オブジェクト、<xref:System.Drawing.Brush>オブジェクト、および<xref:System.Drawing.Region>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="465b6-123">To fill a region, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Brush> object, and a <xref:System.Drawing.Region> object.</span></span> <span data-ttu-id="465b6-124"><xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.FillRegion%2A>メソッド、および<xref:System.Drawing.Brush>オブジェクトは、塗りつぶし、色やパターンなどの属性を格納します。</span><span class="sxs-lookup"><span data-stu-id="465b6-124">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.FillRegion%2A> method, and the <xref:System.Drawing.Brush> object stores attributes of the fill, such as color or pattern.</span></span> <span data-ttu-id="465b6-125">次の例では、純色で領域を塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="465b6-125">The following example fills a region with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="465b6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="465b6-126">See Also</span></span>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="465b6-127">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="465b6-127">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="465b6-128">領域の使用</span><span class="sxs-lookup"><span data-stu-id="465b6-128">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
