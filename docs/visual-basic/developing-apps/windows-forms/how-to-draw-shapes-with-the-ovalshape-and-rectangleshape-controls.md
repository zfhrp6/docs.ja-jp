---
title: '方法 : OvalShape コントロールおよび RectangleShape コントロールを使用して図形を描画する (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
ms.openlocfilehash: f87865ba3aebe5739b87d6ae6bfeaa957af726d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592276"
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>方法 : OvalShape コントロールおよび RectangleShape コントロールを使用して図形を描画する (Visual Studio)
デザイン時にも実行時にも、<xref:Microsoft.VisualBasic.PowerPacks.OvalShape> コントロールを使用して、フォームまたはコンテナーに円または楕円を描画できます。 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> コントロールを使用して、フォームまたはコンテナーに正方形、長方形、または角の丸い四角形を描画できます。 デザイン時にも実行時にも、このコントロールを使用して、図形を描画することもできます。  
  
 境界線の幅、色、およびスタイルを変更することによって、図形の外観をカスタマイズできます。 図形の背景は、既定では透明になっていますが、純色、パターン、グラデーション塗りつぶし (ある色から別の色への遷移)、またはイメージが表示されるようにカスタマイズできます。  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>デザイン時に単純な図形を描画するには  
  
1.  ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.OvalShape>または<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>から制御、 **Visual Basic PowerPacks**  タブ (をインストールするを参照してください[Visual Basic Power Packs コントロール](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) で、**ツールボックス**。フォームまたはコンテナーのコントロールです。  
  
2.  サイズ変更ハンドルおよび移動ハンドルをドラッグして、図形のサイズと位置を設定します。  
  
     ことができますものサイズし、位置の図形を変更して、`Size`と`Position`プロパティで、**プロパティ**ウィンドウです。  
  
     角が丸い四角形を作成するには、選択、`CornerRadius`プロパティに、**プロパティ**ウィンドウが 0 より大きい値に設定します。  
  
3.  **プロパティ**ウィンドウで、必要に応じて追加するプロパティを設定、図形の外観を変更します。  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>実行時に単純な図形を描画するには  
  
1.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。  
  
2.  **参照の追加**ダイアログ ボックスで、 **[microsoft.visualbasic.powerpacks.vs]**、順にクリック**OK**です。  
  
3.  **コード エディター**、追加、`Imports`または`using`モジュールの上部にあるステートメント。  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  `Event` プロシージャに次のコードを追加します。  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>図形のカスタマイズ  
 既定の設定を使用すると、<xref:Microsoft.VisualBasic.PowerPacks.OvalShape> と <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> の各コントロールが、1 ピクセル幅で透明な背景を持つ黒い実線の境界線と共に表示されます。 プロパティを設定することにより、境界線の幅、スタイル、および色を変更できます。 追加のプロパティを使用すると、図形の背景を純色、パターン、グラデーション塗りつぶし、またはイメージに変更できます。  
  
 図形の背景を変更する前に、一部のプロパティがどのように作用するかを知っておく必要があります。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> プロパティの設定は、<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> プロパティが <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque> に設定されていない限り、何の効果もありません。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> に設定した場合、<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>は <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> をオーバーライドします。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> や <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical> などのパターン値に設定した場合、そのパターンが <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> で表示されます。 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> に設定した場合、背景は <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque> で表示されます。  
  
-   グラデーション塗りつぶしを表示するには、<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> に設定し、<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None> 以外の値に設定する必要があります。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> プロパティをイメージに設定すると、他のすべての背景設定がオーバーライドされます。  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>飾り枠を持つ円を描画するには  
  
1.  ドラッグ、`OvalShape`から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。  
  
2.  **プロパティ**ウィンドウで、`Size`プロパティ、`Height`と`Width`に同じ値をします。  
  
3.  `BorderColor` プロパティを任意の色に設定します。  
  
4.  `BorderStyle` プロパティを `Solid` 以外の任意の値に設定します。  
  
5.  `BorderWidth` をピクセル単位の任意のサイズに設定します。  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>純色の塗りつぶしを持つ円を描画するには  
  
1.  ドラッグ、`OvalShape`から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。  
  
2.  **プロパティ**ウィンドウで、`Size`プロパティ、`Height`と`Width`に同じ値をします。  
  
3.  `BackColor` プロパティを任意の色に設定します。  
  
4.  `BackStyle` プロパティを `Opaque` に設定します。  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>塗りつぶしパターンを持つ円を描画するには  
  
1.  ドラッグ、`OvalShape`から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。  
  
2.  **プロパティ**ウィンドウで、`Size`プロパティ、`Height`と`Width`に同じ値をします。  
  
3.  `BackColor` プロパティを任意の背景色に設定します。  
  
4.  `BackStyle` プロパティを `Opaque` に設定します。  
  
5.  `FillColor` プロパティを任意のパターン色に設定します。  
  
6.  `FillStyle` プロパティを `Transparent` または `Solid` 以外の任意の値に設定します。  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>グラデーション塗りつぶしを持つ円を描画するには  
  
1.  ドラッグ、`OvalShape`から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。  
  
2.  **プロパティ**ウィンドウで、`Size`プロパティ、`Height`と`Width`に同じ値をします。  
  
3.  `FillColor` プロパティを任意の開始色に設定します。  
  
4.  `FillGradientColor` プロパティを任意の終了色に設定します。  
  
5.  `FillGradientStyle` プロパティを `None` 以外の値に設定します。  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>イメージで塗りつぶされる円を描画するには  
  
1.  ドラッグ、`OvalShape`から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。  
  
2.  **プロパティ**ウィンドウで、`Size`プロパティ、`Height`と`Width`に同じ値をします。  
  
3.  選択、`BackgroundImage`プロパティをクリックして、**省略記号**(...) ボタンをクリックします。  
  
4.  **[リソースの**] ダイアログ ボックスを表示するイメージを選択します。 イメージ リソースが表示されない場合は、クリックして**インポート**イメージの場所を参照します。  
  
5.  をクリックして**OK**イメージを挿入します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [ライン コントロールとシェイプ コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [方法: LineShape コントロールを使用して線を描画する](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
