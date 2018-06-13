---
title: '方法 : イメージの色を変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 48f506f76ff6e9ca648822d073b6f6a852b9ca8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522537"
---
# <a name="how-to-translate-image-colors"></a>方法 : イメージの色を変換する
翻訳は、次の 4 つの色要素の 1 つ以上に値を追加します。 翻訳を表すカラー マトリックス エントリは、次の表で表されます。  
  
|変換するコンポーネント|マトリックスのエントリ|  
|--------------------------------|------------------|  
|赤|[4][0]|  
|緑|[4][1]|  
|青|[4][2]|  
|[アルファ]|[4][3]|  
  
## <a name="example"></a>例  
 次の例の構築、 <xref:System.Drawing.Image> ColorBars.bmp ファイルからオブジェクト。 コードは、イメージ内の各ピクセルの赤の成分を 0.75 を追加します。 変換後のイメージが並んで、元の画像が描画されます。  
  
 次の図は、右側の左側に元のイメージと変換後のイメージを示します。  
  
 ![色の変換](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 次の表では、赤の平行移動の前後に、次の 4 つのバーの色ベクターが一覧表示します。 色要素の最大値は 1 であるため、2 番目の行の赤の要素が変更されないことに注意してください。 (同様に、色のコンポーネントの最小値は 0 です。)  
  
|元|翻訳先|  
|--------------|----------------|  
|黒 (0、0, 0, 1)|(0.75, 0, 0, 1)|  
|赤 (1、0, 0, 1)|(1, 0, 0, 1)|  
|緑 (0、1, 0, 1)|(0.75, 1, 0, 1)|  
|青 (0、0、1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。 置き換える`ColorBars.bmp`イメージのファイル名と、システムで有効なパスを使用します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)
