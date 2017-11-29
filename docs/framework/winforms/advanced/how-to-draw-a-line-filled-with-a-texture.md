---
title: "方法 :テクスチャを使用して塗りつぶした直線を描画する"
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
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 33374a16e6fee80dd45227acd4c5860d5bfc4545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="0ca10-102">方法 :テクスチャを使用して塗りつぶした直線を描画する</span><span class="sxs-lookup"><span data-stu-id="0ca10-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="0ca10-103">純色で直線を描画するには、代わりに、テクスチャを使用して行を描画できます。</span><span class="sxs-lookup"><span data-stu-id="0ca10-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="0ca10-104">直線と曲線テクスチャを使用して描画するには、作成、<xref:System.Drawing.TextureBrush>オブジェクト、およびを渡す<xref:System.Drawing.TextureBrush>オブジェクトを<xref:System.Drawing.Pen.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="0ca10-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="0ca10-105">テクスチャ ブラシに関連付けられたビットマップは平面 (表示)、並べて表示に使用され、ペンのストロークのテクスチャを並べて表示される特定のピクセルが明らかになったペンでは、直線または曲線が描画されるときにします。</span><span class="sxs-lookup"><span data-stu-id="0ca10-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ca10-106">例</span><span class="sxs-lookup"><span data-stu-id="0ca10-106">Example</span></span>  
 <span data-ttu-id="0ca10-107">次の例を作成、<xref:System.Drawing.Bitmap>ファイルからオブジェクト`Texture1.jpg`です。</span><span class="sxs-lookup"><span data-stu-id="0ca10-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="0ca10-108">そのビットマップが構築するために使用される、<xref:System.Drawing.TextureBrush>オブジェクト、および<xref:System.Drawing.TextureBrush>オブジェクトを構築するために使用、<xref:System.Drawing.Pen>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0ca10-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="0ca10-109">呼び出し<xref:System.Drawing.Graphics.DrawImage%2A>で左上隅をビットマップを描画 (0, 0) です。</span><span class="sxs-lookup"><span data-stu-id="0ca10-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="0ca10-110">呼び出し<xref:System.Drawing.Graphics.DrawEllipse%2A>を使用して、<xref:System.Drawing.Pen>テクスチャ楕円を描画するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0ca10-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="0ca10-111">次の図は、ビットマップ、テクスチャの楕円を示します。</span><span class="sxs-lookup"><span data-stu-id="0ca10-111">The following illustration shows the bitmap and the textured ellipse.</span></span>  
  
 <span data-ttu-id="0ca10-112">![ペン](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span><span class="sxs-lookup"><span data-stu-id="0ca10-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0ca10-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0ca10-113">Compiling the Code</span></span>  
 <span data-ttu-id="0ca10-114">Windows フォームを作成し、処理、フォームの<xref:System.Windows.Forms.Control.Paint>イベント。</span><span class="sxs-lookup"><span data-stu-id="0ca10-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="0ca10-115">上記のコードを貼り付け、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="0ca10-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="0ca10-116">置き換える`Texture.jpg`イメージ システム上で有効にします。</span><span class="sxs-lookup"><span data-stu-id="0ca10-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca10-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ca10-117">See Also</span></span>  
 [<span data-ttu-id="0ca10-118">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="0ca10-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="0ca10-119">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="0ca10-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
