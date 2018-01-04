---
title: "方法 :ピクセルをコピーして Windows フォームのちらつきを低減する"
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
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17253e21739911d4aa0541fde9ae205b0be1c5a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="9c1de-102">方法 :ピクセルをコピーして Windows フォームのちらつきを低減する</span><span class="sxs-lookup"><span data-stu-id="9c1de-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="9c1de-103">単純なグラフィックをアニメーション化するときにユーザーことができる場合もありますが発生ちらつき、またはその他の望ましくない視覚効果。</span><span class="sxs-lookup"><span data-stu-id="9c1de-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="9c1de-104">この問題を制限する 1 つの方法は、プロセスを使用して、"bitblt"画像の上です。</span><span class="sxs-lookup"><span data-stu-id="9c1de-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="9c1de-105">Bitblt は、「ビット ブロック転送」色データの元の四角形にはピクセルからピクセルの四角形に。</span><span class="sxs-lookup"><span data-stu-id="9c1de-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="9c1de-106">Windows フォームで bitblt が使用される、<xref:System.Drawing.Graphics.CopyFromScreen%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="9c1de-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="9c1de-107">メソッドのパラメーターでは、ソースと宛先 (ポイント) として、コピーするのには、領域のサイズおよび新しい図形の描画に使用するグラフィックス オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c1de-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="9c1de-108">次の例では、図形が描画されるフォームでその<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="9c1de-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="9c1de-109">次に、<xref:System.Drawing.Graphics.CopyFromScreen%2A>メソッドは、図形の複製に使用します。</span><span class="sxs-lookup"><span data-stu-id="9c1de-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c1de-110">設定、フォームの<xref:System.Windows.Forms.Control.DoubleBuffered%2A>プロパティを`true`でグラフィックス ベースのコードになります、<xref:System.Windows.Forms.Control.Paint>イベントとなるダブル バッファリングします。</span><span class="sxs-lookup"><span data-stu-id="9c1de-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="9c1de-111">ない、明確なパフォーマンスの向上と、次のコードを使用して、複雑なグラフィックス操作のコードを使用する場合に留意するものがあります。</span><span class="sxs-lookup"><span data-stu-id="9c1de-111">While this will not have any discernable performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c1de-112">例</span><span class="sxs-lookup"><span data-stu-id="9c1de-112">Example</span></span>  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9c1de-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9c1de-113">Compiling the Code</span></span>  
 <span data-ttu-id="9c1de-114">上記のコードをフォームの実行は<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー、フォームが再描画されると、グラフィックスが永続化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9c1de-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="9c1de-115">そのためグラフィックスに関連するメソッドを呼び出す必要はありません、 <xref:System.Windows.Forms.Form.Load> 、イベント ハンドラー描画済みのコンテンツが再描画されませんフォームがサイズ変更されるか、別の形式によって隠されるためです。</span><span class="sxs-lookup"><span data-stu-id="9c1de-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1de-116">参照</span><span class="sxs-lookup"><span data-stu-id="9c1de-116">See Also</span></span>  
 <xref:System.Drawing.CopyPixelOperation>  
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="9c1de-117">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="9c1de-117">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="9c1de-118">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="9c1de-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
