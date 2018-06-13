---
title: '方法 : 線形グラデーションを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: 9eeedf1ef92bdf6e5e2724eeca5060765b0778f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522461"
---
# <a name="how-to-create-a-linear-gradient"></a>方法 : 線形グラデーションを作成する
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 水平方向、垂直方向、および対角線方向の線形グラデーションを提供します。 既定では、線形グラデーションの色を一様に変更します。 ただし、色が一様でない方法で変更されるように、線形グラデーションをカスタマイズできます。  
  
 次の例では、行、楕円、および水平方向の線形グラデーション ブラシを含む四角形を格納します。  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>コンス トラクターは、4 つの引数を受け取ります。 2 つのポイントと 2 つの色。 最初のポイント (0, 10) は最初の色 (赤) に関連付けられ、(200, 10) は、2 番目のポイントが 2 番目の色 (青) と関連付けられています。 想定されるようから描画される線で、(0, 10) に (200, 10) 徐々 に赤から青に変更します。  
  
 ポイント (50, 10) と (200, 10) の 10 件が重要ではありません。 2 つの点が同じ 2 つ目の座標にあることが重要なは、それらを結ぶ線は横方向です。 楕円および四角形も段階的に変化を 200 に水平方向の座標が 0 から出ると、青、赤です。  
  
 次の図は、行、楕円、および四角形を示します。 色のグラデーション繰り返される自体水平方向の座標が 200 を超えるよう注意してください。  
  
 ![線形グラデーション](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>水平方向の線形グラデーションを使用するには  
  
-   3 番目および 4 番目の引数として、それぞれ赤と不透明な青色の不透明なを渡します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 色の要素は前の例では 200 の水平方向の座標に水平方向の座標は 0 から移動すると直線的に変更します。 たとえば、最初の座標が 0 ~ 200 の範囲の中間に位置ポイントは、0 ~ 255 の範囲の中間に位置が青の要素があります。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] グラデーションの 1 つの辺によって色が異なるため、他の方法を調整できます。 黒から次の表に従って赤に変更するグラデーション ブラシを作成するとします。  
  
|水平方向の座標|RGB コンポーネント|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 赤の要素が半分の強さで水平方向の座標が 0 からように、200 の 20% のみである場合に注意してください。  
  
 次の例のセット、<xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A>のプロパティ、<xref:System.Drawing.Drawing2D.LinearGradientBrush>に 3 つの相対強度を 3 つの相対的な位置に関連付けるオブジェクト。 前の表のようには、0.5 の相対強度は、0.2 の相対的な位置に関連付けられます。 コードでは、楕円およびグラデーション ブラシを含む四角形を格納します。  
  
 次の図は、結果として得られる楕円および四角形を示します。  
  
 ![線形グラデーション](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")  
  
### <a name="to-customize-linear-gradients"></a>線形グラデーションをカスタマイズするには  
  
-   3 番目および 4 番目の引数として、それぞれ不透明な黒と不透明な赤いを渡します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 グラデーション前の例では、水平; されています。色は、水平線のいずれかに沿った移動すると、徐々 に変更します。 垂直グラデーションや対角線のグラデーションを定義することもできます。  
  
 次の例に、ポイント (0, 0) と (200, 100) を渡します、<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>コンス トラクターです。 青に関連付けられている (0, 0) に関連付けられている色の緑 (200, 100)。 (ペンの幅が 10) を使用した直線と楕円は、線形グラデーション ブラシで埋められます。  
  
 次の図は、行は、し、省略記号を示します。 楕円の色、徐々 にに沿って移動すると行のメモに並列に渡される行には (0, 0) と (200, 100)。  
  
 ![線形グラデーション](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>対角線方向の線形グラデーションを作成するには  
  
-   3 番目および 4 番目の引数として、それぞれ不透明青と不透明緑を渡します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>関連項目  
 [グラデーション ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
