---
title: "How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "OvalShape control"
  - "shapes, drawing"
  - "RectangleShape control"
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

デザイン時にも実行時にも、<xref:Microsoft.VisualBasic.PowerPacks.OvalShape> コントロールを使用して、フォームまたはコンテナーに円または楕円を描画できます。  <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> コントロールを使用して、フォームまたはコンテナーに正方形、長方形、または角の丸い四角形を描画できます。  デザイン時にも実行時にも、このコントロールを使用して、図形を描画することもできます。  
  
 境界線の幅、色、およびスタイルを変更することによって、図形の外観をカスタマイズできます。  図形の背景は、既定では透明になっていますが、純色、パターン、グラデーション塗りつぶし \(ある色から別の色への遷移\)、またはイメージが表示されるようにカスタマイズできます。  
  
### デザイン時に単純な図形を描画するには  
  
1.  **\[ツールボックス\]** の **\[Visual Basic PowerPacks\]** タブ \(インストール方法については、「[Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)」を参照してください\) から、<xref:Microsoft.VisualBasic.PowerPacks.OvalShape> または <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> のいずれかのコントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  サイズ変更ハンドルおよび移動ハンドルをドラッグして、図形のサイズと位置を設定します。  
  
     **\[プロパティ\]** ウィンドウの `Size` プロパティと `Position` プロパティを変更することによっても、図形のサイズと位置を設定できます。  
  
     角の丸い四角形を作成するには、**\[プロパティ\]** ウィンドウで `CornerRadius` プロパティを選択し、0 より大きい値に設定します。  
  
3.  **\[プロパティ\]** ウィンドウで、必要に応じて追加のプロパティを設定して、図形の外観を変更します。  
  
### 実行時に単純な図形を描画するには  
  
1.  **\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。  
  
2.  **\[参照の追加\]** ダイアログ ボックスで、**\[Microsoft.VisualBasic.PowerPacks.VS\]** を選択し、**\[OK\]** をクリックします。  
  
3.  **コード エディター**で、モジュールの先頭に `Imports` ステートメントまたは `using` ステートメントを追加します。  
  
    ```vb#  
    Imports Microsoft.VisualBasic.PowerPacks  
    ```  
  
    ```c#  
    using Microsoft.VisualBasic.PowerPacks;  
    ```  
  
4.  `Event` プロシージャに次のコードを追加します。  
  
     [!code-cs[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerpacksShapeCS/VbPowerpacksShape.cs#1)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerpacksShape/VbPowerpacksShape.vb#1)]  
  
## 図形のカスタマイズ  
 既定の設定を使用すると、<xref:Microsoft.VisualBasic.PowerPacks.OvalShape> と <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> の各コントロールが、1 ピクセル幅で透明な背景を持つ黒い実線の境界線と共に表示されます。  プロパティを設定することにより、境界線の幅、スタイル、および色を変更できます。  追加のプロパティを使用すると、図形の背景を純色、パターン、グラデーション塗りつぶし、またはイメージに変更できます。  
  
 図形の背景を変更する前に、一部のプロパティがどのように作用するかを知っておく必要があります。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> プロパティの設定は、<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> プロパティが <xref:Microsoft.VisualBasic.PowerPacks.BackStyle> に設定されていない限り、何の効果もありません。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.FillStyle> に設定した場合、<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>は <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> をオーバーライドします。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.FillStyle> や <xref:Microsoft.VisualBasic.PowerPacks.FillStyle> などのパターン値に設定した場合、そのパターンが <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> で表示されます。  <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.BackStyle> に設定した場合、背景は <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> で表示されます。  
  
-   グラデーション塗りつぶしを表示するには、<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.FillStyle> に設定し、<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle> 以外の値に設定する必要があります。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> プロパティをイメージに設定すると、他のすべての背景設定がオーバーライドされます。  
  
#### 飾り枠を持つ円を描画するには  
  
1.  **\[ツールボックス\]** の **\[Visual Basic PowerPacks\]** タブから、`OvalShape` コントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  **\[プロパティ\]** ウィンドウの `Size` プロパティで、`Height` と `Width` に同じ値を設定します。  
  
3.  `BorderColor` プロパティを任意の色に設定します。  
  
4.  `BorderStyle` プロパティを `Solid` 以外の任意の値に設定します。  
  
5.  `BorderWidth` をピクセル単位の任意のサイズに設定します。  
  
#### 純色の塗りつぶしを持つ円を描画するには  
  
1.  **\[ツールボックス\]** の **\[Visual Basic PowerPacks\]** タブから、`OvalShape` コントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  **\[プロパティ\]** ウィンドウの `Size` プロパティで、`Height` と `Width` に同じ値を設定します。  
  
3.  `BackColor` プロパティを任意の色に設定します。  
  
4.  `BackStyle` プロパティを `Opaque` に設定します。  
  
#### 塗りつぶしパターンを持つ円を描画するには  
  
1.  **\[ツールボックス\]** の **\[Visual Basic PowerPacks\]** タブから、`OvalShape` コントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  **\[プロパティ\]** ウィンドウの `Size` プロパティで、`Height` と `Width` に同じ値を設定します。  
  
3.  `BackColor` プロパティを任意の背景色に設定します。  
  
4.  `BackStyle` プロパティを `Opaque` に設定します。  
  
5.  `FillColor` プロパティを任意のパターン色に設定します。  
  
6.  `FillStyle` プロパティを `Transparent` または `Solid` 以外の任意の値に設定します。  
  
#### グラデーション塗りつぶしを持つ円を描画するには  
  
1.  **\[ツールボックス\]** の **\[Visual Basic PowerPacks\]** タブから、`OvalShape` コントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  **\[プロパティ\]** ウィンドウの `Size` プロパティで、`Height` と `Width` に同じ値を設定します。  
  
3.  `FillColor` プロパティを任意の開始色に設定します。  
  
4.  `FillGradientColor` プロパティを任意の終了色に設定します。  
  
5.  `FillGradientStyle` プロパティを `None` 以外の値に設定します。  
  
#### イメージで塗りつぶされる円を描画するには  
  
1.  **\[ツールボックス\]** の **\[Visual Basic PowerPacks\]** タブから、`OvalShape` コントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  **\[プロパティ\]** ウィンドウの `Size` プロパティで、`Height` と `Width` に同じ値を設定します。  
  
3.  `BackgroundImage` プロパティを選択し、**省略記号**ボタン \(...\) をクリックします。  
  
4.  **\[リソースの選択\]** ダイアログ ボックスで、表示するイメージを選択します。  イメージ リソースが一覧にない場合は、**\[インポート\]** をクリックしてイメージの場所を参照します。  
  
5.  **\[OK\]** をクリックしてイメージを挿入します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>   
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>   
 [Introduction to the Line and Shape Controls](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)   
 [How to: Draw Lines with the LineShape Control](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)