---
title: "パス マークアップ構文 | Microsoft Docs"
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
  - "PathGeometry クラス"
  - "属性の使用方法 (XAML)"
  - "XAML 属性の使用方法"
  - "PathGeometry クラス"
  - "グラフィックス、PathGeometry クラス"
  - "XAML オブジェクト要素の使用"
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# パス マークアップ構文
パスは、後ほど[図形と WPF の概要での基本的な描画](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)と[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)、ただし、このトピックを詳しく説明よりコンパクトを使用してパス ジオメトリを指定するのに使用する、強力で複雑なミニ言語[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。  
  
 このトピックは、次のセクションで構成されています。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解する必要があります理解しておくの基本機能<xref:System.Windows.Media.Geometry>オブジェクトです。 詳細については、次を参照してください。、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)します。  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry と PathFigureCollection のミニ言語  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ジオメトリック パスを記述するためのミニ言語を提供する&2; つのクラスを提供します。 <xref:System.Windows.Media.StreamGeometry>と<xref:System.Windows.Media.PathFigureCollection>します。  
  
-   使用する、 <xref:System.Windows.Media.StreamGeometry>型のプロパティを設定するときのミニ言語<xref:System.Windows.Media.Geometry>など、<xref:System.Windows.UIElement.Clip%2A>のプロパティ、 <xref:System.Windows.UIElement>または<xref:System.Windows.Shapes.Path.Data%2A>のプロパティ、<xref:System.Windows.Shapes.Path>要素。 次の例では、属性の構文を使用して、作成、 <xref:System.Windows.Media.StreamGeometry>します。  
  
     [!code-xml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   使用する、 <xref:System.Windows.Media.PathFigureCollection>ミニ言語を設定する場合、<xref:System.Windows.Media.PathGeometry.Figures%2A>のプロパティ、 <xref:System.Windows.Media.PathGeometry>します。 次の例では、属性の構文を使用して、作成、 <xref:System.Windows.Media.PathFigureCollection>の<xref:System.Windows.Media.PathGeometry>します。  
  
     [!code-xml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 前の例からわかるように、2 つのミニ言語は、非常に似ています。 使用することは常に、 <xref:System.Windows.Media.PathGeometry>どのような状況を使用する場合に、 <xref:System.Windows.Media.StreamGeometry>; はどちらを使用する必要がありますか。 使用して、 <xref:System.Windows.Media.StreamGeometry>作成後にパスを変更する必要はありませんとを使用して、 <xref:System.Windows.Media.PathGeometry>はパスを変更する必要がある場合。  
  
 違いの詳細については<xref:System.Windows.Media.PathGeometry>と<xref:System.Windows.Media.StreamGeometry>オブジェクトを参照してください、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)します。  
  
### <a name="a-note-about-white-space"></a>空白に関する注意事項  
 簡潔にするために従うと、構文セクションには単一の空白が表示されるが、余分なスペースも許容可能な限り、1 つの領域を表示。  
  
 2 つの数値実際をコンマまたは空白で区切ってが、これだけする場合でも、結果の文字列はあいまいです。 たとえば、`2..3`は実際には&2; つの数値:「2」になります。 "です。&3;"です。 同様に、`2-3`は「2」と「-3」です。 スペースは必要ありません、コマンドの前後にするか。  
  
### <a name="syntax"></a>構文  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]属性に使用する構文、 <xref:System.Windows.Media.StreamGeometry>は省略可能なので構成<xref:System.Windows.Media.FillRule>値と&1; つ以上の説明を図です。  
  
|StreamGeometry XAML 属性の使用方法|  
|-----------------------------------------|  
|`<`*object* *property* `="`[                                         `fillRule`]                                          `figureDescription`[                                         `figureDescription`]*`" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]属性に使用する構文、 <xref:System.Windows.Media.PathFigureCollection>は&1; つまたは複数の図の説明で構成されます。  
  
|PathFigureCollection XAML 属性の使用方法|  
|-----------------------------------------------|  
|`<`*object* *property* `="` `figureDescription`[                                         `figureDescription`]*`" ... />`|  
  
|用語|説明|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=fullName><br /><br /> 指定するかどうか、 <xref:System.Windows.Media.StreamGeometry>を使用して、 <xref:System.Windows.Media.FillRule>または<xref:System.Windows.Media.FillRule><xref:System.Windows.Media.PathGeometry.FillRule%2A>します。<br /><br /> -   `F0`指定、 <xref:System.Windows.Media.FillRule>塗りつぶしルール。<br />-   `F1`指定、 <xref:System.Windows.Media.FillRule>塗りつぶしルール。<br /><br /> サブパスは、既定の動作を使用してこのコマンドを省略すると、 <xref:System.Windows.Media.FillRule>します。 このコマンドを指定する場合は最初に配置する必要があります。|  
|*figureDescription*|コマンド、およびオプションの閉じるコマンド、[移動] コマンドから成る図を描画します。<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|図の開始位置を指定する移動コマンドです。 参照してください、 [Move コマンド](#themovecommand)セクションです。|  
|*drawCommands*|図の内容を記述する&1; つまたは複数の描画コマンドです。 参照してください、[描画コマンド](#drawcommands)セクションです。|  
|*closeCommand*|図を閉じている省略可能な終了コマンドです。 参照してください、 [[閉じる] コマンド](#closecommand)セクションです。|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>移動 コマンド  
 新しい図形の開始位置を指定します。  
  
|構文|  
|------------|  
|`M`*startPoint*<br /><br /> または<br /><br /> `m`*startPoint*|  
  
|用語|説明|  
|----------|-----------------|  
|*開始ポイント*|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 新しい図形の開始点。|  
  
 大文字`M`ことを示します`startPoint`の絶対値は、小文字`m`ことを示します`startPoint`を過去の時点のオフセットです (0,&0;) が存在しない場合、またはです。 移動コマンドの後に複数のポイントを一覧表示行のコマンドを指定した場合に、それらのポイントにその行が描画されます。  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>描画コマンド  
 描画コマンドは、図形のいくつかのコマンドで構成できます。 図形の次のコマンドを使用できます。 行、水平線、垂直線、3 次ベジエ曲線、二次ベジエ曲線、スムーズ&3; 次ベジエ曲線、二次ベジエ曲線を滑らかな、および楕円の円弧です。  
  
 大文字または小文字のいずれかを使用して、各コマンドを入力: 大文字絶対値あり小文字のアルファベットが相対値を表す: そのセグメントの制御点は、前の例の終了位置。 同じ型の 1 つ以上のコマンドを順番に入力するは、重複するコマンドの入力を省略できます。たとえば、`L 100,200 300,400`は`L 100,200 L 300,400`です。 次の表の**移動**と**描画**コマンドです。  
  
### <a name="line-command"></a>コマンドライン  
 現在のポイントと指定の終了点を結ぶ線を作成します。                           `l 20 30``L 20,30`の有効な例を示します**行**コマンドです。  
  
|構文|  
|------------|  
|`L`*エンドポイント*<br /><br /> または<br /><br /> `l`*エンドポイント*|  
  
|用語|説明|  
|----------|-----------------|  
|*エンドポイント*|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 線の終点。|  
  
### <a name="horizontal-line-command"></a>横線コマンド  
 現在のポイントと指定した x 座標の水平の線を作成します。                          `H 90`有効な横線コマンドの例に示します。  
  
|構文|  
|------------|  
|`H`  *x*<br /><br /> または<br /><br /> `h`  *x*|  
  
|用語|説明|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=fullName><br /><br /> 直線の終了点の x 座標。|  
  
### <a name="vertical-line-command"></a>縦線コマンド  
 現在のポイントと指定した座標の y 座標の垂直線を作成します。                          `v 90`有効な縦線コマンドの例に示します。  
  
|構文|  
|------------|  
|`V`  *y*<br /><br /> または<br /><br /> `v`  *y*|  
  
|用語|説明|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=fullName><br /><br /> 直線の終了点の y 座標。|  
  
### <a name="cubic-bezier-curve-command"></a>3 次ベジエ曲線コマンド  
 2 つの指定したコントロール ポイントを使用して、現在のポイントと指定したエンドポイント間で&3; 次ベジエ曲線を作成 ( `controlPoint`1 と`controlPoint`2)。                          `C 100,200 200,400 300,200`有効な曲線コマンドの例に示します。  
  
|構文|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> または<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|用語|説明|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線の開始の接線を決定する、曲線の最初の制御点です。|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線の終了の接線を決定する、曲線の&2; 番目の制御点。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線を描画するポイント。|  
  
### <a name="quadratic-bezier-curve-command"></a>2 次ベジエ曲線コマンド  
 指定したコントロール ポイントを使用して、現在のポイントと指定したエンドポイント間で&2; 次ベジエ曲線を作成 ( `controlPoint`)。                          `q 100,200 300,200`2 次ベジエ曲線の有効なコマンドの例に示します。  
  
|構文|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> または<br /><br /> `q` `controlPoint` `endPoint`|  
  
|用語|説明|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 最初と最後の曲線の接線を決定する、曲線の制御点。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線を描画するポイント。|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>3 次ベジエ曲線が滑らかなコマンド  
 現在のポイントと指定したエンドポイント間で&3; 次ベジエ曲線を作成します。 最初の制御点は、現在のポイントの基準とした前のコマンドの&2; 番目の制御点のリフレクションと見なされます。 前のコマンドが存在しない場合、または前のコマンドはなかった場合&3; 次ベジエ曲線コマンドまたはスムーズ&3; 次ベジエ曲線のコマンドは、最初の制御点は、現在のポイントと一致すると仮定します。 2 番目の制御点、曲線の終了の制御点を指定して`controlPoint`2 です。 たとえば、`S 100,200 200,300`有効なスムーズ 3 次ベジエ曲線コマンドです。  
  
|構文|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> または<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|用語|説明|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線の終了の接線を決定する、曲線の制御点。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線を描画するポイント。|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>2 次ベジエ曲線が滑らかなコマンド  
 現在のポイントと指定したエンドポイント間で&2; 次ベジエ曲線を作成します。 コントロール ポイントは、現在のポイントの基準とした前のコマンドの制御点のリフレクションと見なされます。 前のコマンドが存在しない場合、または前のコマンドはなかった場合、2 次ベジエ曲線コマンドまたはスムーズ&2; 次ベジエ曲線のコマンドは、コントロール ポイントは、現在のポイントと一致します。  
  
|構文|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> または<br /><br /> `t` `controlPoint` `endPoint`|  
  
|用語|説明|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 起動して、曲線の接線を決定する、曲線の制御点。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線を描画するポイント。|  
  
### <a name="elliptical-arc-command"></a>楕円の円弧コマンド  
 現在のポイントと指定したエンドポイント間での楕円の円弧を作成します。  
  
|構文|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> または<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|用語|説明|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=fullName><br /><br /> 円弧の x 半径と y 半径。|  
|`rotationAngle`|<xref:System.Double?displayProperty=fullName><br /><br /> (度単位)、楕円の回転が異なります。|  
|`isLargeArcFlag`|円弧の角度が 180 度べき場合 1 に設定。それ以外の場合、0 に設定します。|  
|`sweepDirectionFlag`|正の角の方向に弧が描画された場合は、1 に設定します。それ以外の場合、0 に設定します。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 円弧が描画される点。|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>[閉じる] コマンド  
 現在の図を終了し、図の開始点を現在の点を結ぶ線を作成します。 このコマンドでは、最後のセグメントと、図の最初のセグメントの間に線結合 (上) を作成します。  
  
|構文|  
|------------|  
|`Z`<br /><br /> または<br /><br /> `z`|  
  
<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>点の構文  
 点の x 座標と y 座標をについて説明します。  
  
|構文|  
|------------|  
|`x` `,` `y`<br /><br /> または<br /><br /> `x` `y`|  
  
|用語|説明|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=fullName><br /><br /> 点の x 座標。|  
|`y`|<xref:System.Double?displayProperty=fullName><br /><br /> 点の y 座標。|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>特殊な値  
 標準的な数値ではなく、次の特殊な値を使用することもできます。 これらの値は大文字小文字を区別します。  
  
 無限大  
 表す<xref:System.Double.PositiveInfinity?displayProperty=fullName>します。  
  
 -Infinity  
 表す<xref:System.Double.NegativeInfinity?displayProperty=fullName>します。  
  
 NaN  
 表す<xref:System.Double.NaN?displayProperty=fullName>します。  
  
 また、科学的表記法を使用することがあります。 たとえば、`+1.e17`有効な値です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.StreamGeometry>   
 <xref:System.Windows.Media.PathGeometry>   
 <xref:System.Windows.Media.PathFigureCollection>   
 [図形と基本描画の WPF の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [操作方法に関するトピック](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)