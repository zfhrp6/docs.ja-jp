---
title: "WPF の 3D パフォーマンスの最大化 | Microsoft Docs"
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
  - "3-D グラフィックス [WPF]"
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# WPF の 3D パフォーマンスの最大化
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] を使用して 3D コントロールを構築し、アプリケーションに 3D シーンを含める場合は、パフォーマンスの最適化を検討することが重要です。このトピックでは、アプリケーションのパフォーマンスに影響を及ぼす可能性がある 3D クラスおよびプロパティを、使用する際のパフォーマンスの最適化に関する推奨事項と共に一覧にして示します。  
  
 このトピックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の 3D 機能に関する高度な専門知識があることを前提としています。  ここでの推奨事項は "描画層 2" に適用されます。これは、ピクセル シェーダーの Version 2.0 と頂点シェーダーの Version 2.0 をサポートするハードウェアとして大まかに定義されています。  詳細については、「[グラフィックスの描画層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)」を参照してください。  
  
## パフォーマンスへの影響 : 高  
  
|||  
|-|-|  
|プロパティ|推奨事項|  
|<xref:System.Windows.Media.Brush>|ブラシの処理速度 \(最高から最低への順\):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> \(キャッシュ済み\)<br /><br /> <xref:System.Windows.Media.VisualBrush> \(キャッシュ済み\)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> \(未キャッシュ\)<br /><br /> <xref:System.Windows.Media.VisualBrush> \(未キャッシュ\)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] で <xref:System.Windows.Controls.Viewport3D> のコンテンツを Viewport3D の四角形に明示的にクリップする必要がない場合は、`Viewport3D.ClipToBounds` を false に設定します。[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のアンチエイリアス クリッピングは非常に低速になることがあり、`ClipToBounds` は <xref:System.Windows.Controls.Viewport3D> に対して既定で有効 \(低速\) です。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|マウス ヒット テストを実行する際、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] で <xref:System.Windows.Controls.Viewport3D> のコンテンツを検討する必要がない場合は、`Viewport3D.IsHitTestVisible` を false に設定します。3D コンテンツのヒット テストはソフトウェアで行われ、メッシュが多いと低速になります。<xref:System.Windows.UIElement.IsHitTestVisible%2A> は <xref:System.Windows.Controls.Viewport3D> において既定で有効 \(低速\) です。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|異なる素材または変換が必要な場合にのみ、異なるモデルを作成します。  それ以外の場合は、同じ素材や変換を使用する多数の <xref:System.Windows.Media.Media3D.GeometryModel3D> インスタンスを少ない数の <xref:System.Windows.Media.Media3D.GeometryModel3D> インスタンスや <xref:System.Windows.Media.Media3D.MeshGeometry3D> インスタンスにまとめます。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュ アニメーションでは、メッシュの個々の頂点がフレームごとに変更されますが、これは [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では必ずしも効率的ではありません。各頂点が変更されるときの変更通知によるパフォーマンスへの影響を最小限に抑えるには、頂点ごとの変更が行われる前に、メッシュを仮想ツリーから切断します。メッシュの変更が完了したら、再び仮想ツリーに接続します。また、この方法でアニメーション化されるメッシュのサイズができるだけ小さくなるようにしてください。|  
|3D アンチエイリアシング|描画速度を向上させるには、<xref:System.Windows.Media.RenderOptions.EdgeMode%2A> 添付プロパティを `Aliased` に設定することで、<xref:System.Windows.Controls.Viewport3D> に対するマルチサンプリングを無効にします。  3D アンチエイリアシングは、[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] では既定で無効になっており、[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] では 4 サンプル\/ピクセルで有効になっています。|  
|テキスト|3D シーンでのライブ テキスト \(ライブである理由はそれが <xref:System.Windows.Media.DrawingBrush> または <xref:System.Windows.Media.VisualBrush> に含まれているため\) は低速になる可能性があります。  テキストが変化しないのであれば、テキストのイメージを使用するようにしてください \(<xref:System.Windows.Media.Imaging.RenderTargetBitmap> を使用\)。|  
|<xref:System.Windows.Media.TileBrush>|ブラシのコンテンツが静的ではないことが理由で、3D シーンで <xref:System.Windows.Media.VisualBrush> または <xref:System.Windows.Media.DrawingBrush> を使用する場合は、ブラシをキャッシュしてみてください \(<xref:System.Windows.Media.RenderOptions.CachingHint%2A> 添付プロパティを `Cache` に設定\)。  最小および最大スケールの無効化しきい値を設定することで \(<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> 添付プロパティと <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> 添付プロパティを使用\)、キャッシュされたブラシが頻繁に再生成されないようにすると同時に、望ましい品質レベルを維持します。  既定では <xref:System.Windows.Media.DrawingBrush> と <xref:System.Windows.Media.VisualBrush> はキャッシュされません。これは、そのブラシで何かが描画されるたびに、ブラシのコンテンツ全体がまず中間表面に再描画される必要があることを意味します。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect> は、影響を受けるすべてのコンテンツが、ハードウェア アクセラレータなしで描画されることを強制します。  パフォーマンスを最適にするためには、<xref:System.Windows.Media.Effects.BitmapEffect> を使用しないでください。|  
  
## パフォーマンスへの影響 : 中  
  
|||  
|-|-|  
|プロパティ|推奨事項|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュが頂点を共有して隣り合う三角形として定義されており、その頂点が同じ位置座標、標準座標、およびテクスチャ座標を持っている場合は、共有される各頂点を 1 回だけ定義し、三角形の定義には <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> を持つインデックスを使用します。|  
|<xref:System.Windows.Media.ImageBrush>|サイズを明示的にコントロールできる場合は \(<xref:System.Windows.Media.Imaging.RenderTargetBitmap> や <xref:System.Windows.Media.ImageBrush> を使用している場合\)、テクスチャ サイズをできるだけ小さくします。  テクスチャの解像度が低いと表示画質が低下するので、画質とパフォーマンスのバランスが適切になるようにしてください。|  
|Opacity|半透明の 3D コンテンツ \(リフレクションなど\) を描画するときは、`Viewport3D.Opacity` を 1 未満の値に設定して半透明 <xref:System.Windows.Controls.Viewport3D> を別に作成するのではなく、ブラシや素材の不透明度プロパティを \(<xref:System.Windows.Media.Brush.Opacity%2A> または <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A> を介して\) 使用します。|  
|<xref:System.Windows.Controls.Viewport3D>|シーンで使用する <xref:System.Windows.Controls.Viewport3D> オブジェクトの数を最小限に抑えます。  モデルごとに別個の Viewport3D を作成するのではなく、1 つの Viewport3D に多数の 3D モデルを組み込みます。|  
|<xref:System.Windows.Freezable>|通常は、<xref:System.Windows.Media.Media3D.MeshGeometry3D>、<xref:System.Windows.Media.Media3D.GeometryModel3D>、Brush、および Material を再利用することをお勧めします。  どれも `Freezable` から派生しており、マルチペアレント可能です。|  
|<xref:System.Windows.Freezable>|Freezable のプロパティがアプリケーションで変更されない場合は、Freezable に対して <xref:System.Windows.Freezable.Freeze%2A> を呼び出します。  フリーズさせることにより、作業セットが減り、処理速度が向上します。|  
|<xref:System.Windows.Media.Brush>|ブラシのコンテンツが変化しない場合は、<xref:System.Windows.Media.VisualBrush> や <xref:System.Windows.Media.DrawingBrush> ではなく、<xref:System.Windows.Media.ImageBrush> を使用します。  2D コンテンツは、<xref:System.Windows.Media.Imaging.RenderTargetBitmap> を使用して <xref:System.Windows.Controls.Image> に変換してから <xref:System.Windows.Media.ImageBrush> で使用します。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|<xref:System.Windows.Media.Media3D.GeometryModel3D> の背面を表示する必要が実際に発生しない限り、<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> は使用しないでください。|  
|<xref:System.Windows.Media.Media3D.Light>|光源の処理速度 \(最高から最低への順\):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュ サイズが次の制限を常に下回るようにしてください。<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20,001 <xref:System.Windows.Media.Media3D.Point3D> インスタンス<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60,003 <xref:System.Int32> インスタンス|  
|<xref:System.Windows.Media.Media3D.Material>|素材の処理速度 \(最高から最低への順\):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D は、非表示のブラシ \(黒のアンビエント ブラシ、クリア ブラシなど\) をすべて同じように除外するわけではありません。これらについては、シーンで省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|<xref:System.Windows.Media.Media3D.MaterialGroup> の各 <xref:System.Windows.Media.Media3D.Material> により他のレンダリングが発生するので、素材を多数含めると、それがシンプルなものであったとしても、GPU の塗りつぶし要求が大幅に増加する可能性があります。  <xref:System.Windows.Media.Media3D.MaterialGroup> に含まれる素材の数を最小限に抑えてください。|  
  
## パフォーマンスへの影響 : 低  
  
|||  
|-|-|  
|プロパティ|推奨事項|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|アニメーションまたはデータ バインディングが不要の場合は、変換を複数含む変換グループを使用する代わりに、<xref:System.Windows.Media.Media3D.MatrixTransform3D> を 1 つだけ使用し、変換グループ内では個別に存在するすべての変換の積になるように設定します。|  
|<xref:System.Windows.Media.Media3D.Light>|シーンに含まれる光源の数を最小限に抑えてください。  シーンに光源が多いと、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] はソフトウェアによる描画を使用します。制限は、およそ 110 <xref:System.Windows.Media.Media3D.DirectionalLight> オブジェクト、70 <xref:System.Windows.Media.Media3D.PointLight> オブジェクト、または 40 <xref:System.Windows.Media.Media3D.SpotLight> オブジェクトです。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|移動するオブジェクトと静的オブジェクトは、別々の <xref:System.Windows.Media.Media3D.ModelVisual3D> インスタンスに含めて分離します。  ModelVisual3D は <xref:System.Windows.Media.Media3D.GeometryModel3D> より "重い" のですが、その理由は変換された境界をキャッシュするからです。  GeometryModel3D はモデル用に最適化されています。ModelVisual3D はシーン ノード用に最適化されています。  GeometryModel3D の共有インスタンスをシーンに追加するには ModelVisual3D を使用します。|  
|<xref:System.Windows.Media.Media3D.Light>|シーンに含まれる光源の数を変更する回数を最小限に抑えてください。  光源の数を変更するたびに、シェーダーが再生成され、再コンパイルされます。ただし、この構成が前に終了されている \(したがってシェーダーがキャッシュされている\) 場合を除きます。|  
|Light|黒い光は見えませんが、描画時間には加算されるので、省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|MeshGeometry3D の <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>、<xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>、および <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> など、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] に含まれる大規模なコレクションの構築時間を最小限に抑えるには、値を読み込む前に、コレクションのサイズを事前に指定します。  可能であれば、コレクションのコンストラクターに、List の配列など、事前に読み込まれているデータ構造体を渡します。|  
  
## 参照  
 [3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)