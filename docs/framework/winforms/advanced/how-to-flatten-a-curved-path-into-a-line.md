---
title: "方法 : 曲線のパスを直線に平坦化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 334fc0fee7166f8f8c5c1db61d3b9e370da72f87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="86228-102">方法 : 曲線のパスを直線に平坦化する</span><span class="sxs-lookup"><span data-stu-id="86228-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="86228-103">A<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトは、一連の行とベジエ スプラインを格納します。</span><span class="sxs-lookup"><span data-stu-id="86228-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="86228-104">パスをいくつかの種類の曲線 (省略記号ボタン、円弧をカーディナル スプライン) を追加できますが、パスに保存する前に、各曲線がベジエ スプラインに変換されます。</span><span class="sxs-lookup"><span data-stu-id="86228-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="86228-105">パスのフラット化は、パス内の各ベジエ スプラインを一連の直線に変換するので構成されます。</span><span class="sxs-lookup"><span data-stu-id="86228-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="86228-106">次の図は前に、と後のフラット化されたパスを示します。</span><span class="sxs-lookup"><span data-stu-id="86228-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="86228-107">![直線と曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="86228-107">![Straight Lines and Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="86228-108">パスを平坦化します。</span><span class="sxs-lookup"><span data-stu-id="86228-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="86228-109">呼び出す、<xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>のメソッド、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="86228-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="86228-110"><xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>メソッドは、フラット化されたパスと、元のパスの間で最大距離を指定する、平坦度引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="86228-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86228-111">参照</span><span class="sxs-lookup"><span data-stu-id="86228-111">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [<span data-ttu-id="86228-112">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="86228-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="86228-113">パスの作成および描画</span><span class="sxs-lookup"><span data-stu-id="86228-113">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
