---
title: "方法 : ライン キャップを使用した直線を描画する"
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
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e2d5a5aba4a7634e0ea8480aa9744a5a7b9721d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="c8616-102">方法 : ライン キャップを使用した直線を描画する</span><span class="sxs-lookup"><span data-stu-id="c8616-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="c8616-103">ライン キャップと呼ばれるいくつかの図形のいずれかでは、開始または行の末尾を描画できます。</span><span class="sxs-lookup"><span data-stu-id="c8616-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c8616-104">いくつかの線端、ラウンド、正方形、ひし形の矢印などをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c8616-104"> supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8616-105">例</span><span class="sxs-lookup"><span data-stu-id="c8616-105">Example</span></span>  
 <span data-ttu-id="c8616-106">ライン キャップ (start cap) の行、行 (end cap) の末尾または破線の破線 (dash cap) の開始を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c8616-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="c8616-107">次の例では、一方の端にある矢印ともう一方の端、ラウンド線端直線を描画します。</span><span class="sxs-lookup"><span data-stu-id="c8616-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="c8616-108">図は、結果として得られる行を示しています。</span><span class="sxs-lookup"><span data-stu-id="c8616-108">The illustration shows the resulting line:</span></span>  
  
 <span data-ttu-id="c8616-109">![ペン](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span><span class="sxs-lookup"><span data-stu-id="c8616-109">![Pens](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c8616-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c8616-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="c8616-111">Windows フォームを作成し、処理、フォームの<xref:System.Windows.Forms.Control.Paint>イベント。</span><span class="sxs-lookup"><span data-stu-id="c8616-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="c8616-112">コード例を貼り付け、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラーを渡す`e`として<xref:System.Windows.Forms.PaintEventArgs>です。</span><span class="sxs-lookup"><span data-stu-id="c8616-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8616-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8616-113">See Also</span></span>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [<span data-ttu-id="c8616-114">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="c8616-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="c8616-115">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="c8616-115">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
