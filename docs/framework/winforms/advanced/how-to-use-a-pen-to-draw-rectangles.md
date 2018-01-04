---
title: "方法 : ペンを使用して四角形を描画する"
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
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7257fa21432ec5d849a257f4a5e412515f474363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="886be-102">方法 : ペンを使用して四角形を描画する</span><span class="sxs-lookup"><span data-stu-id="886be-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="886be-103">四角形を描画する必要があります、<xref:System.Drawing.Graphics>オブジェクトおよび<xref:System.Drawing.Pen>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="886be-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="886be-104"><xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.DrawRectangle%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、線、色、太さなどの機能を格納します。</span><span class="sxs-lookup"><span data-stu-id="886be-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="886be-105">例</span><span class="sxs-lookup"><span data-stu-id="886be-105">Example</span></span>  
 <span data-ttu-id="886be-106">次の例で左上隅を四角形を描画する (10, 10)。</span><span class="sxs-lookup"><span data-stu-id="886be-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="886be-107">四角形には、100 の幅と高さが 50 があります。</span><span class="sxs-lookup"><span data-stu-id="886be-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="886be-108">渡される 2 番目の引数、<xref:System.Drawing.Pen.%23ctor%2A>コンス トラクターの場合、ペンの幅が 5 ピクセルであることを示します。</span><span class="sxs-lookup"><span data-stu-id="886be-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="886be-109">四角形が描画されると、ペンが四角形の境界に中央揃えされます。</span><span class="sxs-lookup"><span data-stu-id="886be-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="886be-110">四角形の辺は描画 5 ピクセル、ペンの幅は 5 であるため、その 1 ピクセルが描画されるワイド、このような内側の境界上、2 のピクセルが描画され、2 ピクセルが外側に描画されます。</span><span class="sxs-lookup"><span data-stu-id="886be-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="886be-111">ペンの配置の詳細については、次を参照してください。[する方法: ペンの幅の設定とアラインメント](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)です。</span><span class="sxs-lookup"><span data-stu-id="886be-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="886be-112">次の図は、結果として得られる四角形を示します。</span><span class="sxs-lookup"><span data-stu-id="886be-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="886be-113">ここで、四角形が描画されるペンの幅が 1 つのピクセルをされていた場合点線表示します。</span><span class="sxs-lookup"><span data-stu-id="886be-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="886be-114">四角形の左上隅を拡大表示では、シック (thick) 黒い線はそれらの点線で中央揃えことを示します。</span><span class="sxs-lookup"><span data-stu-id="886be-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 <span data-ttu-id="886be-115">![ペン](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span><span class="sxs-lookup"><span data-stu-id="886be-115">![Pens](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="886be-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="886be-116">Compiling the Code</span></span>  
 <span data-ttu-id="886be-117">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。</span><span class="sxs-lookup"><span data-stu-id="886be-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886be-118">参照</span><span class="sxs-lookup"><span data-stu-id="886be-118">See Also</span></span>  
 [<span data-ttu-id="886be-119">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="886be-119">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
