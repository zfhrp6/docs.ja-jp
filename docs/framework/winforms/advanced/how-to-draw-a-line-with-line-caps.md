---
title: '方法 : ライン キャップを使用した直線を描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: be492f2317d4677776cc9f89f546c935d271019b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523222"
---
# <a name="how-to-draw-a-line-with-line-caps"></a>方法 : ライン キャップを使用した直線を描画する
ライン キャップと呼ばれるいくつかの図形のいずれかでは、開始または行の末尾を描画できます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] いくつかの線端、ラウンド、正方形、ひし形の矢印などをサポートしています。  
  
## <a name="example"></a>例  
 ライン キャップ (start cap) の行、行 (end cap) の末尾または破線の破線 (dash cap) の開始を指定することができます。  
  
 次の例では、一方の端にある矢印ともう一方の端、ラウンド線端直線を描画します。 図は、結果として得られる行を示しています。  
  
 ![ペン](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   Windows フォームを作成し、処理、フォームの<xref:System.Windows.Forms.Control.Paint>イベント。 コード例を貼り付け、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラーを渡す`e`として<xref:System.Windows.Forms.PaintEventArgs>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
