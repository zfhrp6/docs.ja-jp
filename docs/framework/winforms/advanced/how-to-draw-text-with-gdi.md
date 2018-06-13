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
# <a name="how-to-draw-text-with-gdi"></a>方法 : GDI を使用してテキストを描画する
<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドで、<xref:System.Windows.Forms.TextRenderer>アクセスできるクラス、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]フォームまたはコントロールのテキストを描画するための機能です。 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] テキスト レンダリングとパフォーマンスが向上しより正確なテキストが測定よりも通常は[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A>のメソッド、<xref:System.Windows.Forms.TextRenderer>クラスは、印刷のサポートされていません。 印刷する場合、常に使用、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。  
  
## <a name="example"></a>例  
 次のコード例を使用して、四角形内の複数の行のテキストを描画する方法を示します、<xref:System.Windows.Forms.TextRenderer.DrawText%2A>メソッドです。  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 テキストを表示するために、<xref:System.Windows.Forms.TextRenderer>クラス、する必要があります、 <xref:System.Drawing.IDeviceContext>、ように、<xref:System.Drawing.Graphics>と<xref:System.Drawing.Font>テキストをおよび描画ように色を描画する場所です。 必要に応じて、テキストを使用して書式設定を指定することができます、<xref:System.Windows.Forms.TextFormatFlags>列挙します。  
  
 取得の詳細については、<xref:System.Drawing.Graphics>を参照してください[する方法: 描画グラフィック オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)です。 構築の詳細については、<xref:System.Drawing.Font>を参照してください[する方法: フォント ファミリの構築とフォント](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前のコード例が、Windows フォームで使用するために設計されていて、必要があります、 <xref:System.Windows.Forms.PaintEventArgs> `e`、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
