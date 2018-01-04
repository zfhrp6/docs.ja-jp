---
title: "ペンを使用した直線と図形の描画"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35f43316e2535aae6622ccf7952f649cdb92fc81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="2e1e3-102">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="2e1e3-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="2e1e3-103">使用して[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]`Pen`線分、曲線、および図形の輪郭を描画するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="2e1e3-104">このセクションで*行*という意味では直線セグメントのみを指定しない限りは、次のいずれかを参照します。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="2e1e3-105">色、幅、配置、およびそのペンで描画された直線のスタイルを制御するペンのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e1e3-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2e1e3-106">In This Section</span></span>  
 [<span data-ttu-id="2e1e3-107">方法: ペンを使用して線を描画する</span><span class="sxs-lookup"><span data-stu-id="2e1e3-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="2e1e3-108">線を描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="2e1e3-109">方法: ペンを使用して四角形を描画する</span><span class="sxs-lookup"><span data-stu-id="2e1e3-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="2e1e3-110">四角形を描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="2e1e3-111">方法: ペンの幅と配置を設定する</span><span class="sxs-lookup"><span data-stu-id="2e1e3-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="2e1e3-112">幅との配置を変更する方法について説明します、`Pen`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="2e1e3-113">方法: ライン キャップを使用した直線を描画する</span><span class="sxs-lookup"><span data-stu-id="2e1e3-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="2e1e3-114">線を描画するときに、端点キャップを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="2e1e3-115">方法: 直線を接合する</span><span class="sxs-lookup"><span data-stu-id="2e1e3-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="2e1e3-116">2 つの行を結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="2e1e3-117">方法: カスタム破線を描画する</span><span class="sxs-lookup"><span data-stu-id="2e1e3-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="2e1e3-118">破線を描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="2e1e3-119">方法: テクスチャを使用して塗りつぶした直線を描画する</span><span class="sxs-lookup"><span data-stu-id="2e1e3-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="2e1e3-120">テクスチャを塗りつぶした直線を描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2e1e3-121">参照</span><span class="sxs-lookup"><span data-stu-id="2e1e3-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="2e1e3-122">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="2e1e3-122">Describes this class and has links to all its members.</span></span>
