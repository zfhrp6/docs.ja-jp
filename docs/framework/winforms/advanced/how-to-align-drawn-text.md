---
title: '方法 : 描画テキストを配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
ms.openlocfilehash: 96e14ef510a08ed0c387733e37b6acae6cbd31cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522758"
---
# <a name="how-to-align-drawn-text"></a>方法 : 描画テキストを配置する
カスタム描画を実行するときに、フォームやコントロールを描画するテキストを中央揃えにすることがあります多くの場合。 描画されたテキストを簡単に揃えることができます、<xref:System.Drawing.Graphics.DrawString%2A>または<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドを正しく書式設定オブジェクトを作成し、適切な書式指定フラグを設定します。  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a>描画するには、GDI + (DrawString) を使用してテキストを中央揃え  
  
1.  使用して、<xref:System.Drawing.StringFormat>と適切な<xref:System.Drawing.Graphics.DrawString%2A>中央揃えのテキストを指定します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a>描画するには、GDI (DrawText) を使用してテキストを中央揃え  
  
1.  使用して、<xref:System.Windows.Forms.TextFormatFlags>ラッピングできるだけでなく、垂直方向および水平方向には、適切なテキストを中央揃えの列挙体<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドです。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記のコード例は、できるように設計された Windows フォームで使用して、必要な<xref:System.Windows.Forms.PaintEventArgs> `e`、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。  
  
## <a name="see-also"></a>関連項目  
 [方法: GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [方法: フォント ファミリとフォントを作成する](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
