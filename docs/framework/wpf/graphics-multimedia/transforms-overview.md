---
title: "変換の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "2-D 変換クラス"
  - "クラス, 2-D 変換"
  - "FrameworkElement オブジェクト, 回転"
  - "FrameworkElement オブジェクト, スケーリング"
  - "FrameworkElement オブジェクト, 傾斜"
  - "FrameworkElement オブジェクト, 変換"
  - "変換クラス, 2-D"
  - "変換, 変換の概要"
  - "変換, 変換の概要"
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 変換の概要
ここでは、[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> クラスを使用して <xref:System.Windows.FrameworkElement> オブジェクトの回転、拡大縮小、移動 \(平行移動\)、および傾斜を行う方法について説明します。  
  
   
  
<a name="whatIsATransformSection"></a>   
## 変換とは  
 <xref:System.Windows.Media.Transform> は、ある座標空間の点を別の座標空間にマップまたは変換する方法を定義します。  このマッピングは、<xref:System.Double> 値を示す 3 つの列を持つ 3 つの行のコレクションである、変換 <xref:System.Windows.Media.Matrix> によって示されます。  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] では、行優先の行列が使用されます。  ベクターは、列ベクターではなく行ベクターとして表されます。  
  
 次の表は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 行列の構造を示しています。  
  
### 2\-D 変換行列  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> 既定値: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> 既定値: 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> 既定値: 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> 既定値: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> 既定値: 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> 既定値: 0.0|1.0|  
  
 行列値を操作することによって、オブジェクトの回転、拡大縮小、傾斜、および移動 \(平行移動\) を行うことができます。  たとえば、第 3 行の第 1 列にある値 \(<xref:System.Windows.Media.Matrix.OffsetX%2A> 値\) を 100 に変更した場合は、その値を使用し、オブジェクトを x 軸に沿って 100 単位移動できます。  第 2 行の第 2 列にある値を 3 に変更した場合は、この値を使用し、オブジェクトを現在の高さの 3 倍に引き伸ばすことができます。  両方の値を変更した場合、オブジェクトは x 軸に沿って 100 単位移動し、オブジェクトの高さは 3 倍に引き伸ばされます。  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] はアフィン変換のみをサポートするため、右の列の値は常に 0、0、1 です。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] では行列値を直接操作できますが、基になる行列構造体の構成方法がわからなくてもオブジェクトを変換できる、いくつかの <xref:System.Windows.Media.Transform> クラスも提供されています。  たとえば、変換行列を操作する代わりに、<xref:System.Windows.Media.ScaleTransform> クラスを使用し、<xref:System.Windows.Media.ScaleTransform.ScaleX%2A> プロパティと <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> プロパティを設定してオブジェクトをスケーリングできます。  同様に、<xref:System.Windows.Media.RotateTransform> クラスを使用すると、<xref:System.Windows.Media.RotateTransform.Angle%2A> プロパティを設定するだけでオブジェクトを回転できます。  
  
<a name="transformClassesSection"></a>   
## 変換クラス  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] には、一般的な変換操作用に次の [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> クラスが用意されています。  
  
|Class|Description|例|図|  
|-----------|-----------------|-------|-------|  
|<xref:System.Windows.Media.RotateTransform>|指定した <xref:System.Windows.Media.RotateTransform.Angle%2A> だけ要素を回転します。|[オブジェクトを回転させる](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)||  
|<xref:System.Windows.Media.ScaleTransform>|指定した <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> および <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> の量だけ要素をスケーリングします。|[要素をスケーリングする](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)||  
|<xref:System.Windows.Media.SkewTransform>|指定した <xref:System.Windows.Media.SkewTransform.AngleX%2A> および <xref:System.Windows.Media.SkewTransform.AngleY%2A> の量だけ要素を傾斜させます。|[要素を傾斜させる](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)||  
|<xref:System.Windows.Media.TranslateTransform>|指定した <xref:System.Windows.Media.TranslateTransform.X%2A> および <xref:System.Windows.Media.TranslateTransform.Y%2A> の量だけ要素を移動 \(平行移動\) します。|[要素を変換する](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)||  
  
 より複雑な変換を作成するために、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] は次の 2 つのクラスを提供します。  
  
|Class|Description|例|  
|-----------|-----------------|-------|  
|<xref:System.Windows.Media.TransformGroup>|複数の <xref:System.Windows.Media.TransformGroup> オブジェクトを、変換プロパティに適用できる単一の <xref:System.Windows.Media.Transform> にグループ化します。|[オブジェクトに複数の変換を適用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|他の <xref:System.Windows.Media.Transform> クラスによって提供されないカスタム変換を作成します。  <xref:System.Windows.Media.MatrixTransform> を使用する場合は、Matrix を直接操作します。|[MatrixTransform を使用してカスタム変換を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] は [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] 変換も提供します。  詳細については、<xref:System.Windows.Media.Media3D.Transform3D> クラスを参照してください。  
  
<a name="transformationproperties"></a>   
## 一般的な変換プロパティ  
 オブジェクトを変換する方法の 1 つとして、適切な <xref:System.Windows.Media.Transform> 型を宣言してオブジェクトの変換プロパティに適用する方法があります。  さまざまな型のオブジェクトが、異なる種類の変換プロパティを持ちます。  一般的に使用されるいくつかの [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 型とその変換プロパティを次の表に示します。  
  
|種類|変換プロパティ|  
|--------|-------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## 変換と座標系  
 オブジェクトを変換する場合は、オブジェクトを変換するだけでなく、オブジェクトが存在する座標空間を変換します。  既定では、変換の中心 \(0,0\) はターゲット オブジェクトの座標系の基点です。  唯一の例外は <xref:System.Windows.Media.TranslateTransform> です。<xref:System.Windows.Media.TranslateTransform> は、中心の位置に関係なく変換効果が同じであるため、中心を設定するためのプロパティはありません。  
  
 次の例では、<xref:System.Windows.Media.RotateTransform> を使用して、<xref:System.Windows.FrameworkElement> の一種である <xref:System.Windows.Shapes.Rectangle> 要素をその既定の位置 \(0, 0\) を中心に 45°回転します。  回転の効果を次の図に示します。  
  
 ![&#40;0,0&#41; を軸に 45 度回転した FrameworkElement](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm\_FE\_rotated\_about\_upperleft\_corner")  
点 \(0,0\) を中心として 45°回転した四角形要素  
  
 [!code-xml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 既定では、この要素は左上隅 \(0, 0\) を中心に回転します。  <xref:System.Windows.Media.RotateTransform>、<xref:System.Windows.Media.ScaleTransform>、および <xref:System.Windows.Media.SkewTransform> の各クラスは、変換が適用される点を指定できる CenterX プロパティと CenterY プロパティを提供します。  
  
 次の例でも、<xref:System.Windows.Media.RotateTransform> を使用して <xref:System.Windows.Shapes.Rectangle> 要素を 45°回転していますが、<xref:System.Windows.Media.RotateTransform.CenterX%2A> プロパティと <xref:System.Windows.Media.RotateTransform.CenterY%2A> プロパティは <xref:System.Windows.Media.RotateTransform> の中心が \(25, 25\) になるように設定されています。  回転の効果を次の図に示します。  
  
 ![&#40;25, 25&#41; を軸に 45 度回転した Geometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm\_FE\_rotated\_about\_center")  
点 \(25, 25\) を中心として 45°回転した四角形要素  
  
 [!code-xml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## FrameworkElement の変換  
 <xref:System.Windows.FrameworkElement> に変換を適用するには、<xref:System.Windows.Media.Transform> を作成して、<xref:System.Windows.FrameworkElement> クラスが提供する 2 つのプロパティのいずれかに適用します。  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A> – レイアウト パスの前に適用される変換。  変換の適用後に、レイアウト システムは要素の変換後のサイズおよび位置を処理します。  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A> – 要素の外観を変更する変換。レイアウト パスの完了後に適用されます。  <xref:System.Windows.FrameworkElement.LayoutTransform%2A> プロパティの代わりに <xref:System.Windows.UIElement.RenderTransform%2A> プロパティを使用すると、パフォーマンスを向上できます。  
  
 どちらのプロパティを使用すればよいでしょうか。  パフォーマンスを向上させるために、可能な場合 \(特にアニメーション化された <xref:System.Windows.Media.Transform> オブジェクトを使用する場合\) は必ず、<xref:System.Windows.UIElement.RenderTransform%2A> プロパティを使用してください。  拡大縮小、回転、または傾斜を行うときに、要素の変換後のサイズに合わせるために要素の親が必要になる場合は、<xref:System.Windows.FrameworkElement.LayoutTransform%2A> プロパティを使用します。  <xref:System.Windows.FrameworkElement.LayoutTransform%2A> プロパティと共に使用した場合、<xref:System.Windows.Media.TranslateTransform> オブジェクトは、要素に影響していないように見えます。  これは、レイアウト システムが処理の一部として平行移動された要素を元の位置に戻すためです。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のレイアウトの詳細については、「[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)」の概要を参照してください。  
  
<a name="exampleRotateAnElement45degSection"></a>   
## 例 : FrameworkElement を 45°回転する  
 次の例では、<xref:System.Windows.Media.RotateTransform> を使用して、ボタンを時計回りに 45°回転します。  このボタンは、他にも 2 つのボタンを持つ <xref:System.Windows.Controls.StackPanel> 内に存在します。  
  
 既定では、<xref:System.Windows.Media.RotateTransform> は点 \(0,0\) を中心として回転します。  この例では中心の値を指定しないため、ボタンはその左上隅の点 \(0, 0\) を中心として回転します。  <xref:System.Windows.Media.RotateTransform> は、<xref:System.Windows.UIElement.RenderTransform%2A> プロパティに適用されます。  変換の結果を次の図に示します。  
  
 ![RenderTransform を使用して変換されたボタン](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm\_RenderTransformWithDefaultCenter")  
左上隅から時計回りに 45°回転  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 次の例でも <xref:System.Windows.Media.RotateTransform> を使用してボタンを時計回りに 45 度回転していますが、ボタンの <xref:System.Windows.UIElement.RenderTransformOrigin%2A> を \(0.5, 0.5\) にも設定しています。  <xref:System.Windows.UIElement.RenderTransformOrigin%2A> プロパティの値は、ボタンのサイズに対して相対的です。  その結果、回転はボタンの左上隅ではなく中心に適用されます。  変換の結果を次の図に示します。  
  
 ![中心の周りで変換されたボタン](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm\_RenderTransformRelativeCenter")  
中心を軸に時計回りに 45°回転  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <xref:System.Windows.UIElement.RenderTransform%2A> プロパティの代わりに <xref:System.Windows.FrameworkElement.LayoutTransform%2A> プロパティを使用して、ボタンを回転する例を次に示します。  これにより、変換がボタンのレイアウトに影響し、レイアウト システムで完全パスをトリガーします。  ボタンはサイズが変更されたため、結果として回転し位置が変わります。  変換の結果を次の図に示します。  
  
 ![LayoutTransform を使用して変換されたボタン](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm\_LayoutTransform")  
LayoutTransform を使用したボタンの回転  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## 変換のアニメーション化  
 <xref:System.Windows.Media.Transform> クラスは、<xref:System.Windows.Media.Animation.Animatable> を継承するため、アニメーション化することができます。  <xref:System.Windows.Media.Transform> をアニメーション化するには、互換性のある種類のアニメーションをアニメーション化するプロパティに適用します。  
  
 次の例では、<xref:System.Windows.Media.Animation.Storyboard> と <xref:System.Windows.Media.Animation.DoubleAnimation> を、<xref:System.Windows.Media.RotateTransform> で使用して、<xref:System.Windows.Controls.Button> がクリックされたときにその場で回転させます。  
  
 [!code-xml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 サンプル全体については、[2\-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)を参照してください。  アニメーションの詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
<a name="freezable_features"></a>   
## Freezable の機能  
 <xref:System.Windows.Media.Transform> クラスは <xref:System.Windows.Freezable> クラスを継承しているため、<xref:System.Windows.Media.Transform> オブジェクトの[リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)としての宣言、複数のオブジェクトでの共有、読み取り専用に設定することによるパフォーマンスの向上、複製、スレッド セーフの設定など、特殊な機能を備えています。  <xref:System.Windows.Freezable> オブジェクトのさまざまな機能の詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.Matrix>   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)   
 [2\-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)