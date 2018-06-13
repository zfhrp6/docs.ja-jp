---
title: '方法 : GDI を使用してテキストを描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: e18ff96ea97eb636de8ab73aaa094c07b10fd456
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522916"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="be24a-102">方法 : GDI を使用してテキストを描画する</span><span class="sxs-lookup"><span data-stu-id="be24a-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="be24a-103"><xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドで、<xref:System.Windows.Forms.TextRenderer>アクセスできるクラス、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]フォームまたはコントロールのテキストを描画するための機能です。</span><span class="sxs-lookup"><span data-stu-id="be24a-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] functionality for drawing text on a form or control.</span></span> [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]<span data-ttu-id="be24a-104"> テキスト レンダリングとパフォーマンスが向上しより正確なテキストが測定よりも通常は[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="be24a-104"> text rendering typically offers better performance and more accurate text measuring than [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be24a-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A>のメソッド、<xref:System.Windows.Forms.TextRenderer>クラスは、印刷のサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="be24a-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="be24a-106">印刷する場合、常に使用、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="be24a-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be24a-107">例</span><span class="sxs-lookup"><span data-stu-id="be24a-107">Example</span></span>  
 <span data-ttu-id="be24a-108">次のコード例を使用して、四角形内の複数の行のテキストを描画する方法を示します、<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="be24a-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="be24a-109">テキストを表示するために、<xref:System.Windows.Forms.TextRenderer>クラス、する必要があります、 <xref:System.Drawing.IDeviceContext>、ように、<xref:System.Drawing.Graphics>と<xref:System.Drawing.Font>テキストをおよび描画ように色を描画する場所です。</span><span class="sxs-lookup"><span data-stu-id="be24a-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="be24a-110">必要に応じて、テキストを使用して書式設定を指定することができます、<xref:System.Windows.Forms.TextFormatFlags>列挙します。</span><span class="sxs-lookup"><span data-stu-id="be24a-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="be24a-111">取得の詳細については、<xref:System.Drawing.Graphics>を参照してください[する方法: 描画グラフィック オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)です。</span><span class="sxs-lookup"><span data-stu-id="be24a-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="be24a-112">構築の詳細については、<xref:System.Drawing.Font>を参照してください[する方法: フォント ファミリの構築とフォント](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)です。</span><span class="sxs-lookup"><span data-stu-id="be24a-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be24a-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="be24a-113">Compiling the Code</span></span>  
 <span data-ttu-id="be24a-114">前のコード例が、Windows フォームで使用するために設計されていて、必要があります、 <xref:System.Windows.Forms.PaintEventArgs> `e`、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。</span><span class="sxs-lookup"><span data-stu-id="be24a-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be24a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="be24a-115">See Also</span></span>  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [<span data-ttu-id="be24a-116">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="be24a-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
