---
title: 曲線の作成と描画
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: d9a790060fdf0f0c2a739d99aba1b36cf0323f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520618"
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="e0da9-102">曲線の作成と描画</span><span class="sxs-lookup"><span data-stu-id="e0da9-102">Constructing and Drawing Curves</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="e0da9-103"> 曲線のいくつかの種類をサポートします。 省略記号ボタン、円弧をカーディナル スプラインおよびベジエ スプラインです。</span><span class="sxs-lookup"><span data-stu-id="e0da9-103"> supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="e0da9-104">楕円がの外接する四角形によって定義されています。円弧は、開始角度および掃引角度がによって定義される楕円の一部です。</span><span class="sxs-lookup"><span data-stu-id="e0da9-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="e0da9-105">ポイントおよびテンション パラメーターの配列を通過するカーディナル スプラインを定義-曲線は、配列内の各ポイントをスムーズに通過し、テンション曲線曲がる方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="e0da9-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="e0da9-106">ベジエ スプラインが 2 つのエンドポイントとの制御点を通過しません曲線 2 つの制御点によって定義されますが、コントロール ポイントの方向に影響を与えるおよび曲線がもう一方の 1 つのエンドポイントから出ると、します。</span><span class="sxs-lookup"><span data-stu-id="e0da9-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0da9-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e0da9-107">In This Section</span></span>  
 [<span data-ttu-id="e0da9-108">方法: カーディナル スプラインを描画する</span><span class="sxs-lookup"><span data-stu-id="e0da9-108">How to: Draw Cardinal Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="e0da9-109">カーディナル スプラインを描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0da9-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="e0da9-110">方法: 1 本のベジエ スプラインを描画する</span><span class="sxs-lookup"><span data-stu-id="e0da9-110">How to: Draw a Single Bézier Spline</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="e0da9-111">ベジエ スプラインと 1 つを描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0da9-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="e0da9-112">方法: 一連のベジエ スプラインを描画する</span><span class="sxs-lookup"><span data-stu-id="e0da9-112">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="e0da9-113">シーケンスに複数のベジエ スプラインを描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0da9-113">Explains how to draw several Bézier splines in sequence.</span></span>
