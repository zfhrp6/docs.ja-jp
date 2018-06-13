---
title: '方法 : 色を傾斜する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 204f15ce44d5ad688be0ea9ac0fa4a90781b25dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522448"
---
# <a name="how-to-shear-colors"></a>方法 : 色を傾斜する
傾斜だけ増加または減少色要素の色の別のコンポーネントに比例した量。 たとえば、赤の要素は青の要素の値の半分ずつ増加する、変換があるとします。 このような変換は、下にある色 (0.2、0.5, 1) になります (0.7, 0.5, 1)。 新しい赤の要素が 0.2 + (1/2)(1) 0.7 を = です。  
  
## <a name="example"></a>例  
 次の例の構築、 <xref:System.Drawing.Image> ColorBars4.bmp ファイルからオブジェクト。 コードは、イメージ内の各ピクセルに前の段落で説明した傾斜変換を適用します。  
  
 次の図は、右側の左側に元のイメージと傾斜されたイメージを示します。  
  
 ![色を傾斜](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 次の表では、および傾斜変換を実行後する前に、4 つのバーの色のベクターが一覧表示します。  
  
|元|傾斜|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。 置き換える`ColorBars.bmp`イメージの名前とパスがシステム上で有効にします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)
