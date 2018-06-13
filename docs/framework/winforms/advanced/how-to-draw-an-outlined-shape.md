---
title: '方法 : 形状のアウトラインを描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.DrawEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- drawing [Windows Forms], shapes
- circular shapes
- forms [Windows Forms], drawing circular shapes
- circles
- outlined shapes [Windows Forms], examples
- outlined shapes [Windows Forms], drawing
- drawing [Windows Forms], circular shapes
- shapes [Windows Forms], drawing
ms.assetid: f4f9214c-607e-407d-8cdd-6549f0278451
ms.openlocfilehash: b674c4d80ba6c70c0bdff6d020527a039e5c7baa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521916"
---
# <a name="how-to-draw-an-outlined-shape"></a><span data-ttu-id="b5597-102">方法 : 形状のアウトラインを描画する</span><span class="sxs-lookup"><span data-stu-id="b5597-102">How to: Draw an Outlined Shape</span></span>
<span data-ttu-id="b5597-103">この例では、フォームに記載された楕円と四角形を描画します。</span><span class="sxs-lookup"><span data-stu-id="b5597-103">This example draws outlined ellipses and rectangles on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5597-104">例</span><span class="sxs-lookup"><span data-stu-id="b5597-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5597-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b5597-105">Compiling the Code</span></span>  
 <span data-ttu-id="b5597-106">このメソッドを呼び出すことはできません、<xref:System.Windows.Forms.Form.Load>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="b5597-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="b5597-107">フォームがサイズ変更されるか、別の形式によって隠されている場合、描画済みのコンテンツを再描画されませんされます。</span><span class="sxs-lookup"><span data-stu-id="b5597-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="b5597-108">コンテンツを自動的に再描画するために、オーバーライドする必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b5597-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b5597-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="b5597-109">Robust Programming</span></span>  
 <span data-ttu-id="b5597-110">常に呼び出す必要があります<xref:System.IDisposable.Dispose%2A>など、システム リソースを消費するすべてのオブジェクトに対する<xref:System.Drawing.Pen>と<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b5597-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5597-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5597-111">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Drawing.Graphics.DrawRectangle%2A>  
 [<span data-ttu-id="b5597-112">グラフィックス プログラミングについて</span><span class="sxs-lookup"><span data-stu-id="b5597-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="b5597-113">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="b5597-113">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="b5597-114">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="b5597-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
