---
title: '方法 : ペンを使用して四角形を描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: ad5b436f7162c282198c7a9d3cce4d3ce3fd3c6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524008"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>方法 : ペンを使用して四角形を描画する
四角形を描画する必要があります、<xref:System.Drawing.Graphics>オブジェクトおよび<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.DrawRectangle%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、線、色、太さなどの機能を格納します。  
  
## <a name="example"></a>例  
 次の例で左上隅を四角形を描画する (10, 10)。 四角形には、100 の幅と高さが 50 があります。 渡される 2 番目の引数、<xref:System.Drawing.Pen.%23ctor%2A>コンス トラクターの場合、ペンの幅が 5 ピクセルであることを示します。  
  
 四角形が描画されると、ペンが四角形の境界に中央揃えされます。 四角形の辺は描画 5 ピクセル、ペンの幅は 5 であるため、その 1 ピクセルが描画されるワイド、このような内側の境界上、2 のピクセルが描画され、2 ピクセルが外側に描画されます。 ペンの配置の詳細については、次を参照してください。[する方法: ペンの幅の設定とアラインメント](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)です。  
  
 次の図は、結果として得られる四角形を示します。 ここで、四角形が描画されるペンの幅が 1 つのピクセルをされていた場合点線表示します。 四角形の左上隅を拡大表示では、シック (thick) 黒い線はそれらの点線で中央揃えことを示します。  
  
 ![ペン](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。  
  
## <a name="see-also"></a>関連項目  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
