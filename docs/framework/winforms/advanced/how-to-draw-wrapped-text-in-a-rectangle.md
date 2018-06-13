---
title: '方法 : 四角形内にテキストを折り返して描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: c753be6a200f166e59e1330c7dbcf1fadc7588a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524974"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>方法 : 四角形内にテキストを折り返して描画する
四角形で囲まれたテキストを描画するにを使用して、<xref:System.Drawing.Graphics.DrawString%2A>オーバー ロードされたメソッドの<xref:System.Drawing.Graphics>を受け取るクラス、<xref:System.Drawing.Rectangle>または<xref:System.Drawing.RectangleF>パラメーター。 また、使用、<xref:System.Drawing.Brush>と<xref:System.Drawing.Font>です。  
  
 使用して、四角形で囲まれたテキストを描画することも、<xref:System.Windows.Forms.TextRenderer.DrawText%2A>オーバー ロードされたメソッドの<xref:System.Windows.Forms.TextRenderer>を受け取る、<xref:System.Drawing.Rectangle>と<xref:System.Windows.Forms.TextFormatFlags>パラメーター。 また、使用、<xref:System.Drawing.Color>と<xref:System.Drawing.Font>です。  
  
 次の図に、使用すると、四角形に描画されるテキストの出力、<xref:System.Drawing.Graphics.DrawString%2A>メソッドです。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>GDI + での四角形にテキストを折り返して描画するには  
  
1.  使用して、<xref:System.Drawing.Graphics.DrawString%2A>オーバー ロードされたメソッド、するは、テキストを渡す<xref:System.Drawing.Rectangle>または<xref:System.Drawing.RectangleF>、<xref:System.Drawing.Font>と<xref:System.Drawing.Brush>です。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>GDI を使用して、四角形内にテキストを折り返して描画するには  
  
1.  使用して、<xref:System.Windows.Forms.TextFormatFlags>でテキストを指定する列挙値をラップする必要があります、<xref:System.Windows.Forms.TextRenderer.DrawText%2A>オーバー ロードされたメソッド、するは、テキストを渡す<xref:System.Drawing.Rectangle>、<xref:System.Drawing.Font>と<xref:System.Drawing.Color>です。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例が必要です。  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。  
  
## <a name="see-also"></a>関連項目  
 [方法: GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [方法: フォント ファミリとフォントを作成する](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [方法: テキストを指定の位置に描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
