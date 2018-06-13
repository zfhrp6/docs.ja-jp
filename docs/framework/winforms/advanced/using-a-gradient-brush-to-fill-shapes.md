---
title: グラデーション ブラシを使用した図形の塗りつぶし
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 857a9276a731ae5e69b3caa1a639d1315aba9901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525035"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="a6bb9-102">グラデーション ブラシを使用した図形の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="a6bb9-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="a6bb9-103">グラデーション ブラシを使用して、図形を塗りつぶす色が徐々 に変化させることができます。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="a6bb9-104">たとえば、色、形状の左端から右端に移動する段階的に変化するように図形を塗りつぶすに水平方向のグラデーションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="a6bb9-105">黒を左の端で四角形を想像してください (0, 0, 0 は、赤、緑、および青のコンポーネントによって表されます)、右端が赤 (255, 0, 0) とします。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="a6bb9-106">四角形が 256 ピクセルである場合は、いずれかの左側にあるピクセルの赤の要素より大きい値を特定のピクセルの赤の要素になります。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="a6bb9-107">行の左端のピクセルの色要素 (0, 0, 0)、2 番目のピクセルが (1, 0, 0)、3 番目のピクセルが (2, 0, 0)、し、右端のピクセルの色要素 (255, 0, 0) に達するまでします。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="a6bb9-108">これらの色の補間値は、色のグラデーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="a6bb9-109">線形グラデーションは、水平、垂直方向に移動または並列斜めの指定した行に色を変更します。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="a6bb9-110">パス グラデーションは、内側およびパスの境界を移動すると、色を変更します。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="a6bb9-111">さまざまな効果を実現するためにパス グラデーションをカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="a6bb9-112">次の図は、四角形が線形グラデーション ブラシで塗りつぶされパス グラデーション ブラシで塗りつぶした楕円を示します。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush.</span></span>  
  
 <span data-ttu-id="a6bb9-113">![グラデーション](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span><span class="sxs-lookup"><span data-stu-id="a6bb9-113">![Gradient](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6bb9-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a6bb9-114">In This Section</span></span>  
 [<span data-ttu-id="a6bb9-115">方法: 線形グラデーションを作成する</span><span class="sxs-lookup"><span data-stu-id="a6bb9-115">How to: Create a Linear Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="a6bb9-116">線形グラデーションを使用して、作成する方法を示しています、<xref:System.Drawing.Drawing2D.LinearGradientBrush>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="a6bb9-117">方法: パス グラデーションを作成する</span><span class="sxs-lookup"><span data-stu-id="a6bb9-117">How to: Create a Path Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 <span data-ttu-id="a6bb9-118">パス グラデーションを使用して、作成する方法について説明します、<xref:System.Drawing.Drawing2D.PathGradientBrush>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="a6bb9-119">方法: グラデーションに対してガンマ補正を適用する</span><span class="sxs-lookup"><span data-stu-id="a6bb9-119">How to: Apply Gamma Correction to a Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="a6bb9-120">グラデーション ブラシでガンマ補正を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a6bb9-121">参照</span><span class="sxs-lookup"><span data-stu-id="a6bb9-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="a6bb9-122">このクラスの説明を表すし、そのすべてのメンバーへのリンクがあります。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="a6bb9-123">このクラスの説明を表すし、そのすべてのメンバーへのリンクがあります。</span><span class="sxs-lookup"><span data-stu-id="a6bb9-123">Contains a description of this class and has links to all of its members.</span></span>
