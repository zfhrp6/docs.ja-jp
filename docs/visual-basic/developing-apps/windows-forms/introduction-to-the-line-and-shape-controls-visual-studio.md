---
title: ライン コントロールとシェイプ コントロールの概要 (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
ms.openlocfilehash: 3ad740f7dd15194830959a5493970b4ba54ce142
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590739"
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>ライン コントロールとシェイプ コントロールの概要 (Visual Studio)
Visual Basic Power Packs のライン コントロールとシェイプ コントロールは、フォームとコンテナーの直線と図形を描画するための 3 つのグラフィカル コントロールのセットです。 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>水平、垂直方向、および斜めの線を描画するコントロールを使用します。 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>円、楕円を描画するコントロールを使用し、<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>四角形と正方形を描画するコントロールを使用します。  
  
## <a name="line-and-shape-controls"></a>ライン コントロールとシェイプ コントロール  
 ライン コントロールとシェイプ コントロールをカプセル化に含まれているグラフィックス メソッドの多くは、<xref:System.Drawing>名前空間。 これにより、1 つの手順でグラフィックス オブジェクト、ペン、およびブラシを作成することがなく線と形状を描画することができます。 グラデーション塗りつぶしなどの複雑なグラフィックスの手法は、いくつかのプロパティを設定するだけで実現できます。  
  
 グラフィックス メソッドを使用して直線と図形を描画することも、行および形状のコントロールを使用するいくつかの利点のあります。  
  
-   グラフィックス メソッドは、実行時にのみ呼び出すことができます。 ライン コントロールとシェイプ コントロールは、デザイン時にフォームに追加できます。 これにより、どのように見えるを参照してください。 に正確に配置するにはまた、実行時にも追加できます。  
  
-   ライン コントロールとシェイプ コントロールは、選択可能な実行時にイベントをなどを提供する<xref:Microsoft.VisualBasic.PowerPacks.Shape.Click>と<xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>です。 グラフィックス メソッドの出力が選択できず、イベントを提供しません。  
  
-   ライン コントロールとシェイプ コントロールを提供<xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A>と<xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A>をデザイン時および実行時に、z オーダーを制御する方法です。 グラフィックス メソッドの z オーダーは、実行時に実行順序を変更することでのみ制御できます。  
  
-   ライン コントロールとシェイプ コントロールはウィンドウレス コントロールです。ウィンドウ ハンドルがなく可能ためシステム リソースを使用します。  
  
### <a name="object-model"></a>オブジェクト モデル  
 ライン コントロールとシェイプ コントロールは、ベースから派生<xref:Microsoft.VisualBasic.PowerPacks.Shape>共有のプロパティ、メソッド、およびイベントを定義するクラス。  
  
 次の図は、Line および Shape オブジェクト階層を示します。  
  
 ![Line および Shape オブジェクト階層のダイアグラム](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Line および Shape オブジェクト階層  
  
 派生した<xref:Microsoft.VisualBasic.PowerPacks.LineShape>クラスには、プロパティ、メソッド、および行に固有のイベントが含まれています。 派生した<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>クラスの基底クラスは、<xref:Microsoft.VisualBasic.PowerPacks.OvalShape>と<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; プロパティ、メソッド、およびすべての図形に共通のイベントが含まれています。 派生できますも<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>独自に作成する`Shape`コントロール。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>と<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>クラスは、円、楕円、四角形、および角の丸い四角形を描画するために使用できます。  
  
 行または形状のコントロールをフォームまたはコンテナーを非表示を追加するときに<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>オブジェクトを作成します。 <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>各コンテナー コントロール内の図形のキャンバスの役目です。 各<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>に、対応する<xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection>行および形状のコントロールを反復処理することができます。 ドラッグ アンド ドロップまたは切り取りと貼り付けを使用して、別に 1 つのコンテナーから図形を移動できます。 最後の図形が、コンテナーから削除されたときに、<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>も削除されます。  
  
> [!NOTE]
>  すべてのコンテナー コントロールは、行および形状のコントロールをサポートします。 行または形状のコントロールをホストすることはできません、<xref:System.Windows.Forms.TableLayoutPanel>または<xref:System.Windows.Forms.FlowLayoutPanel>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks>  
 [方法: LineShape コントロールを使用して線を描画する](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [方法: OvalShape コントロールおよび RectangleShape コントロールを使用して図形を描画する](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [方法: 図形間のタブ移動を有効にする](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
