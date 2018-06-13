---
title: 変換を使用した色のスケーリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 6cfe90cef42086672990c45c99961db3d29c3ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525968"
---
# <a name="using-transformations-to-scale-colors"></a>変換を使用した色のスケーリング
拡大縮小変換は、番号で 4 つの色要素の 1 つ以上を乗算します。 拡大/縮小を表すカラー マトリックス エントリは、次の表で表されます。  
  
|コンポーネントを拡張します。|マトリックスのエントリ|  
|----------------------------|------------------|  
|赤|[0][0]|  
|緑|[1][1]|  
|青|[2][2]|  
|[アルファ]|[3][3]|  
  
## <a name="scaling-one-color"></a>1 つの色のスケーリング  
 次の例の構築、 <xref:System.Drawing.Image> ColorBars2.bmp ファイルからオブジェクト。 コードは、2 倍の図の各ピクセルの青の成分をスケーリングします。 変換後のイメージが並んで、元の画像が描画されます。  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 次の図は、右側の左側に元のイメージとスケーリングされたイメージを示します。  
  
 ![色をスケーリング](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")  
  
 次の表では、青のスケーリングの前後に、次の 4 つのバーの色ベクターが一覧表示します。 4 番目のカラー バーの青の要素が 0.6 を 0.8 からしたことに注意してください。 これはため[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]は、結果の小数部の一部のみが保持されます。 たとえば、(2)(0.8) = 1.6、1.6 の小数部は 0.6 です。 小数部分のみを保持とは、結果は、常には [0, 1] 間隔することを確認します。  
  
|元|拡大/縮小|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>複数の色のスケーリング  
 次の例の構築、 <xref:System.Drawing.Image> ColorBars2.bmp ファイルからオブジェクト。 コードは、イメージ内の各ピクセルの赤、緑、および青のコンポーネントをスケーリングします。 赤の要素は、25% に縮小し、緑の要素は 35% に縮小青の要素は、50% に縮小します。  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 次の図は、右側の左側に元のイメージとスケーリングされたイメージを示します。  
  
 ![色をスケーリング](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")  
  
 次の表では、赤、緑、青のスケーリングの前後に、次の 4 つのバーの色ベクターが一覧表示します。  
  
|元|拡大/縮小|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)
