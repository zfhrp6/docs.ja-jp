---
title: '方法 : イメージを並べたパターンによって図形を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: 0905f29b0f74c72979e252cf94e677d1c7e0525d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523124"
---
# <a name="how-to-tile-a-shape-with-an-image"></a>方法 : イメージを並べたパターンによって図形を塗りつぶす
並べてフロアをカバーするタイルを配置すると同様、塗りつぶし (タイル) 図形を四角形のイメージを互いの横にある配置できます。 図形の内部を並べて表示するには、テクスチャ ブラシを使用します。 構築する場合、<xref:System.Drawing.TextureBrush>オブジェクトのコンス トラクターに渡す引数の 1 つは、<xref:System.Drawing.Image>オブジェクト。 図形の内部を描画するテクスチャ ブラシを使用する場合は、このイメージの繰り返しコピーで、図形が塗りつぶされます。  
  
 ラップ モード プロパティ、<xref:System.Drawing.TextureBrush>オブジェクトはどのように、画像には、四角形グリッドでそれが繰り返されるを決定します。 ことができます、グリッド内のタイルがすべて同じ印刷の向き、または、次に反転させる 1 つのグリッド位置からイメージを行うことができます。 反転は、水平、垂直、またはその両方です。 次の例は、さまざまな種類の反転を並べて表示します。  
  
### <a name="to-tile-an-image"></a>イメージを並べて表示  
  
-   この例では、次の 75 × 75 イメージを使用して、200 × 200 四角形を並べて表示します。  
  
 ![タイル 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")  
  
-   次の図は、四角形がイメージを並べて表示する方法を示します。 すべてのタイルが同じ方向; にあることに注意してください。切り替えることはありません。  
  
 ![タイル 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>水平方向に並べて表示するときにイメージを反転するには  
  
-   この例では、同じ 75 × 75 イメージを使用して、200 × 200 四角形の塗りつぶし。 ラップ モードは、イメージを水平方向に反転に設定されます。 次の図は、四角形がイメージを並べて表示する方法を示します。 特定の行ごとに 1 つのタイルから移動すると、イメージは水平方向に反転注意してください。  
  
 ![タイル 3 の](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>垂直方向に並べて表示するときにイメージを反転するには  
  
-   この例では、同じ 75 × 75 イメージを使用して、200 × 200 四角形の塗りつぶし。 ラップ モードは、イメージを垂直方向に反転に設定されます。  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>並べて表示するとき、イメージを水平方向および垂直方向に反転するには  
  
-   この例では、同じ 75 × 75 イメージを使用して、200 × 200 四角形を並べて表示します。 ラップ モードは、上下左右反転イメージ両方に設定されます。 次の図は、四角形がイメージを並べて表示する方法を示します。 1 つのタイルから次の特定の行に移動する、イメージは水平方向に反転しすると、イメージが垂直方向に反転させるように 1 つのタイルから特定の列で次に移動することに注意してください。  
  
 ![5 をタイル](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>関連項目  
 [ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
