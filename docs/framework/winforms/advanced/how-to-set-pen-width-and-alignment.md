---
title: "方法 : ペンの幅と配置を設定する"
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
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e5858da25174c8bc1de18d534023b57b58253e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="c66e6-102">方法 : ペンの幅と配置を設定する</span><span class="sxs-lookup"><span data-stu-id="c66e6-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="c66e6-103">作成するときに、 <xref:System.Drawing.Pen>、コンス トラクターに引数の 1 つとして、ペンの幅を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c66e6-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="c66e6-104">ペンの幅を変更することも、<xref:System.Drawing.Pen.Width%2A>のプロパティ、<xref:System.Drawing.Pen>クラスです。</span><span class="sxs-lookup"><span data-stu-id="c66e6-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="c66e6-105">理論上の線が 0 の幅を持ちます。</span><span class="sxs-lookup"><span data-stu-id="c66e6-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="c66e6-106">1 ピクセル幅の広い線を描画するときは、理論上の線のピクセルが中央揃えされます。</span><span class="sxs-lookup"><span data-stu-id="c66e6-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="c66e6-107">1 つ以上のピクセル幅の広い線を描画する場合ピクセルは理論上の線の中央揃えで配置するか、または、理論上の線の片側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c66e6-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="c66e6-108">ペンの配置プロパティを設定することができます、<xref:System.Drawing.Pen>理論上の行に対する相対をペンで描画されるピクセルを配置する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="c66e6-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="c66e6-109">値<xref:System.Drawing.Drawing2D.PenAlignment.Center>、 <xref:System.Drawing.Drawing2D.PenAlignment.Outset>、および<xref:System.Drawing.Drawing2D.PenAlignment.Inset>次に表示されるコードの例のメンバーである、<xref:System.Drawing.Drawing2D.PenAlignment>列挙します。</span><span class="sxs-lookup"><span data-stu-id="c66e6-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="c66e6-110">次のコード例では直線を 2 回を描画します。 黒のペンの幅が 1 のが 1 回と緑のペンの幅が 10 のです。</span><span class="sxs-lookup"><span data-stu-id="c66e6-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="c66e6-111">ペンの幅を変更するには</span><span class="sxs-lookup"><span data-stu-id="c66e6-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="c66e6-112">値を設定、<xref:System.Drawing.Pen.Alignment%2A>プロパティを<xref:System.Drawing.Drawing2D.PenAlignment.Center>(既定値) を緑のペンで描画されるピクセルの中央を理論的な行に指定します。</span><span class="sxs-lookup"><span data-stu-id="c66e6-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="c66e6-113">次の図は、結果として得られる行を示しています。</span><span class="sxs-lookup"><span data-stu-id="c66e6-113">The following illustration shows the resulting line.</span></span>  
  
     <span data-ttu-id="c66e6-114">![ペン](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span><span class="sxs-lookup"><span data-stu-id="c66e6-114">![Pens](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span></span>  
  
     <span data-ttu-id="c66e6-115">次のコード例は 2 回四角形を描画します。 黒のペンの幅が 1 のが 1 回と緑のペンの幅が 10 のです。</span><span class="sxs-lookup"><span data-stu-id="c66e6-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="c66e6-116">ペンのアラインメントを変更するには</span><span class="sxs-lookup"><span data-stu-id="c66e6-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="c66e6-117">値を設定、<xref:System.Drawing.Pen.Alignment%2A>プロパティを<xref:System.Drawing.Drawing2D.PenAlignment.Center>緑のペンで描画されるピクセルの中央を四角形の境界を指定します。</span><span class="sxs-lookup"><span data-stu-id="c66e6-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="c66e6-118">次の図は、結果として得られる四角形を示します。</span><span class="sxs-lookup"><span data-stu-id="c66e6-118">The following illustration shows the resulting rectangle.</span></span>  
  
     <span data-ttu-id="c66e6-119">![ペン](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span><span class="sxs-lookup"><span data-stu-id="c66e6-119">![Pens](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="c66e6-120">ペンを作成するには</span><span class="sxs-lookup"><span data-stu-id="c66e6-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="c66e6-121">前のコード例では、3 番目のステートメントを次のように変更することによって、緑のペンの配置を変更します。</span><span class="sxs-lookup"><span data-stu-id="c66e6-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="c66e6-122">これで、次の図に示すようには、四角形の内側のワイド緑の線のピクセルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c66e6-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="c66e6-123">![ペン](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span><span class="sxs-lookup"><span data-stu-id="c66e6-123">![Pens](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66e6-124">参照</span><span class="sxs-lookup"><span data-stu-id="c66e6-124">See Also</span></span>  
 [<span data-ttu-id="c66e6-125">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="c66e6-125">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="c66e6-126">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="c66e6-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
