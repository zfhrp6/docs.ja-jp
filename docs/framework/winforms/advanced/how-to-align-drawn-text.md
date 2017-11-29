---
title: "方法 : 描画テキストを配置する"
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
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a2f2f6bd088ad58277839cf7e32a98d67ca3bd15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-align-drawn-text"></a><span data-ttu-id="66ebc-102">方法 : 描画テキストを配置する</span><span class="sxs-lookup"><span data-stu-id="66ebc-102">How to: Align Drawn Text</span></span>
<span data-ttu-id="66ebc-103">カスタム描画を実行するときに、フォームやコントロールを描画するテキストを中央揃えにすることがあります多くの場合。</span><span class="sxs-lookup"><span data-stu-id="66ebc-103">When you perform custom drawing, you may often want to center drawn text on a form or control.</span></span> <span data-ttu-id="66ebc-104">描画されたテキストを簡単に揃えることができます、<xref:System.Drawing.Graphics.DrawString%2A>または<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドを正しく書式設定オブジェクトを作成し、適切な書式指定フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="66ebc-104">You can easily align text drawn with the <xref:System.Drawing.Graphics.DrawString%2A> or <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods by creating the correct formatting object and setting the appropriate format flags.</span></span>  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a><span data-ttu-id="66ebc-105">描画するには、GDI + (DrawString) を使用してテキストを中央揃え</span><span class="sxs-lookup"><span data-stu-id="66ebc-105">To draw centered text with GDI+ (DrawString)</span></span>  
  
1.  <span data-ttu-id="66ebc-106">使用して、<xref:System.Drawing.StringFormat>と適切な<xref:System.Drawing.Graphics.DrawString%2A>中央揃えのテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="66ebc-106">Use a <xref:System.Drawing.StringFormat> with the appropriate <xref:System.Drawing.Graphics.DrawString%2A> method to specify centered text.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a><span data-ttu-id="66ebc-107">描画するには、GDI (DrawText) を使用してテキストを中央揃え</span><span class="sxs-lookup"><span data-stu-id="66ebc-107">To draw centered text with GDI (DrawText)</span></span>  
  
1.  <span data-ttu-id="66ebc-108">使用して、<xref:System.Windows.Forms.TextFormatFlags>ラッピングできるだけでなく、垂直方向および水平方向には、適切なテキストを中央揃えの列挙体<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="66ebc-108">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration for wrapping as well as vertically and horizontally centering text with the appropriate <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="66ebc-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="66ebc-109">Compiling the Code</span></span>  
 <span data-ttu-id="66ebc-110">上記のコード例は、できるように設計された Windows フォームで使用して、必要な<xref:System.Windows.Forms.PaintEventArgs> `e`、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。</span><span class="sxs-lookup"><span data-stu-id="66ebc-110">The preceding code examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ebc-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="66ebc-111">See Also</span></span>  
 [<span data-ttu-id="66ebc-112">方法: GDI を使用してテキストを描画する</span><span class="sxs-lookup"><span data-stu-id="66ebc-112">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="66ebc-113">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="66ebc-113">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="66ebc-114">方法: フォント ファミリとフォントを作成する</span><span class="sxs-lookup"><span data-stu-id="66ebc-114">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
