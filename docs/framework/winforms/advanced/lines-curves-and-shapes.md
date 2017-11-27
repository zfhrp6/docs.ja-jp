---
title: "直線、曲線、および図形"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [Windows Forms], filling
- splines [Windows Forms], drawing
- shapes. drawing
- lines [Windows Forms], drawing
- curves [Windows Forms], drawing
ms.assetid: ace6e8d4-4e94-486b-9681-758a6667dc7f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2caa77285ebe327adc690b26baeb58aa800627fb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="lines-curves-and-shapes"></a><span data-ttu-id="35bd5-102">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="35bd5-102">Lines, Curves, and Shapes</span></span>
<span data-ttu-id="35bd5-103">ベクター グラフィックス部分[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、直線、曲線、および描画とする図形を塗りつぶすために使用します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-103">The vector graphics portion of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is used to draw lines, draw curves, and to draw and fill shapes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35bd5-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="35bd5-104">In This Section</span></span>  
 [<span data-ttu-id="35bd5-105">ベクター グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="35bd5-105">Vector Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)  
 <span data-ttu-id="35bd5-106">ベクター グラフィックスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-106">Discusses vector graphics.</span></span>  
  
 [<span data-ttu-id="35bd5-107">GDI+ でのペン、直線、および四角形</span><span class="sxs-lookup"><span data-stu-id="35bd5-107">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 <span data-ttu-id="35bd5-108">線や四角形を描画について説明します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-108">Discusses drawing lines and rectangles.</span></span>  
  
 [<span data-ttu-id="35bd5-109">GDI+ での楕円および円弧</span><span class="sxs-lookup"><span data-stu-id="35bd5-109">Ellipses and Arcs in GDI+</span></span>](../../../../docs/framework/winforms/advanced/ellipses-and-arcs-in-gdi.md)  
 <span data-ttu-id="35bd5-110">円弧と楕円を定義し、これらを描画するために必要なクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-110">Defines arcs and ellipses and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="35bd5-111">GDI+ での多角形</span><span class="sxs-lookup"><span data-stu-id="35bd5-111">Polygons in GDI+</span></span>](../../../../docs/framework/winforms/advanced/polygons-in-gdi.md)  
 <span data-ttu-id="35bd5-112">多角形を定義し、これらを描画するために必要なクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-112">Defines polygons and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="35bd5-113">GDI+ でのカーディナル スプライン</span><span class="sxs-lookup"><span data-stu-id="35bd5-113">Cardinal Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cardinal-splines-in-gdi.md)  
 <span data-ttu-id="35bd5-114">カーディナル スプラインを定義し、これらを描画するために必要なクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-114">Defines cardinal splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="35bd5-115">GDI+ でのベジエ スプライン</span><span class="sxs-lookup"><span data-stu-id="35bd5-115">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 <span data-ttu-id="35bd5-116">ベジエ スプラインを定義し、これらを描画するために必要なクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-116">Defines Bezier splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="35bd5-117">GDI+ でのグラフィックス パス</span><span class="sxs-lookup"><span data-stu-id="35bd5-117">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)  
 <span data-ttu-id="35bd5-118">パスと作成し、それらを描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-118">Describes paths and how to create and draw them.</span></span>  
  
 [<span data-ttu-id="35bd5-119">GDI+ でのブラシと塗りつぶされた図形</span><span class="sxs-lookup"><span data-stu-id="35bd5-119">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 <span data-ttu-id="35bd5-120">ブラシの種類とその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-120">Describes brush types and how to use them.</span></span>  
  
 [<span data-ttu-id="35bd5-121">GDI+ での開いた曲線と閉じた曲線</span><span class="sxs-lookup"><span data-stu-id="35bd5-121">Open and Closed Curves in GDI+</span></span>](../../../../docs/framework/winforms/advanced/open-and-closed-curves-in-gdi.md)  
 <span data-ttu-id="35bd5-122">開いた曲線と閉じた曲線と描画して、情報を入力する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-122">Defines open and closed curves and how to draw and fill them.</span></span>  
  
 [<span data-ttu-id="35bd5-123">GDI+ での領域</span><span class="sxs-lookup"><span data-stu-id="35bd5-123">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 <span data-ttu-id="35bd5-124">領域に関連付けられたメソッドをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-124">Describes the methods associated with regions.</span></span>  
  
 [<span data-ttu-id="35bd5-125">GDI+ での描画サーフェイスの制限</span><span class="sxs-lookup"><span data-stu-id="35bd5-125">Restricting the Drawing Surface in GDI+</span></span>](../../../../docs/framework/winforms/advanced/restricting-the-drawing-surface-in-gdi.md)  
 <span data-ttu-id="35bd5-126">クリッピングとその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-126">Describes clipping and how to use it.</span></span>  
  
 [<span data-ttu-id="35bd5-127">直線と曲線のアンチエイリアシング</span><span class="sxs-lookup"><span data-stu-id="35bd5-127">Antialiasing with Lines and Curves</span></span>](../../../../docs/framework/winforms/advanced/antialiasing-with-lines-and-curves.md)  
 <span data-ttu-id="35bd5-128">アンチエイリアシングとどのように描画するときに使用するアンチエイリアシング直線し、曲線を定義します。</span><span class="sxs-lookup"><span data-stu-id="35bd5-128">Defines antialiasing and how use antialiasing when drawing lines and curves.</span></span>
