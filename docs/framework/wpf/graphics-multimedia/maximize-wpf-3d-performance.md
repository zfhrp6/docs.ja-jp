---
title: WPF の 3D パフォーマンスの最大化
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 6677ee3a6d17ea38636d49327d7af22b53bc900e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565439"
---
# <a name="maximize-wpf-3d-performance"></a>WPF の 3D パフォーマンスの最大化
使用すると、 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D コントロールをビルドし、アプリケーションで 3D シーンを含むにはパフォーマンスの最適化を検討してください。 このトピックでは、3 D のクラスと、それらを使用するときにパフォーマンスを最適化するための推奨事項と共に、アプリケーションのパフォーマンスに影響を与えるプロパティの一覧を示します。  
  
 このトピックには、高度な理解が前提としています[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D の機能です。 このドキュメントで示す内容は「描画層 2」に適用: ほぼピクセル シェーダーのバージョン 2.0 と頂点シェーダーのバージョン 2.0 をサポートするハードウェアとして定義します。 詳細については、次を参照してください。[グラフィックス レンダリング階層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)です。  
  
## <a name="performance-impact-high"></a>パフォーマンスへの影響: 高  
  
|プロパティ|推奨事項|  
|-|-|  
|<xref:System.Windows.Media.Brush>|ブラシの速度 (最高への最も遅い):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> (キャッシュ済み)<br /><br /> <xref:System.Windows.Media.VisualBrush> (キャッシュ済み)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> (キャッシュ)<br /><br /> <xref:System.Windows.Media.VisualBrush> (キャッシュ)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|設定`Viewport3D.ClipToBounds`を false にする必要はありませんされるたびに[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]のコンテンツを明示的にクリップ、 <xref:System.Windows.Controls.Viewport3D> Viewport3D の四角形にします。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アンチ エイリアス処理された領域が非常に遅くできますと`ClipToBounds`(遅い) 既定では有効で<xref:System.Windows.Controls.Viewport3D>です。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|設定`Viewport3D.IsHitTestVisible`を必要としないときに false に[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の内容を考慮する、<xref:System.Windows.Controls.Viewport3D>実行マウス ヒット テストします。  ヒット テストの 3D コンテンツは、ソフトウェアでは実行され、大規模なメッシュで低速であることができます。 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 既定で有効に低速で<xref:System.Windows.Controls.Viewport3D>です。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|異なる素材または変換が必要な場合にのみ、異なるモデルを作成します。  多くを結合しようとするはそれ以外の場合、<xref:System.Windows.Media.Media3D.GeometryModel3D>マテリアルと変換が同じでインスタンスをいくつかの大きなに<xref:System.Windows.Media.Media3D.GeometryModel3D>と<xref:System.Windows.Media.Media3D.MeshGeometry3D>インスタンス。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|アニメーションをメッシュ — 個々 のフレームごとの単位でメッシュの頂点を変更する — 常に効率的ではありません[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。  各頂点が変更されたときに、変更通知のパフォーマンスに与える影響を最小限に抑える、頂点ごとの変更を実行する前に、ビジュアル ツリーからメッシュをデタッチします。  メッシュが変更された後は、ビジュアル ツリーに接続し直します。  また、この方法でアニメーション化されるメッシュのサイズを最小限に抑えてください。|  
|3D のアンチエイリアシング|表示速度を向上させるのにでのマルチ サンプリングを無効にする<xref:System.Windows.Controls.Viewport3D>添付プロパティを設定して<xref:System.Windows.Media.RenderOptions.EdgeMode%2A>に`Aliased`です。  既定では、3 D (アンチエイリアシング) が無効になって[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]で有効になっていると[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]ピクセルあたり 4 つのサンプルです。|  
|テキスト|3D シーンでテキストをライブ (live されているため、<xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>) 速度が低下することができます。 代わりに、テキストのイメージを使用しようとしています (を介して<xref:System.Windows.Media.Imaging.RenderTargetBitmap>)、テキストは変更しない限り、します。|  
|<xref:System.Windows.Media.TileBrush>|使用する場合、<xref:System.Windows.Media.VisualBrush>または<xref:System.Windows.Media.DrawingBrush>3D シーン ブラシのコンテンツが静的でないために、やり直してくださいブラシをキャッシュ (添付プロパティを設定<xref:System.Windows.Media.RenderOptions.CachingHint%2A>に`Cache`)。  スケールの最小値と最大の無効化のしきい値の設定 (添付プロパティを持つ<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>と<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>) キャッシュされたブラシされませんを再生成する頻度が高すぎる、目的のレベルの品質を維持しながらできるようにします。  既定では、<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>はキャッシュされません、たびに再表示するのには、ブラシで描画されたものブラシのコンテンツ全体必要がありますまずが再表示されることが中間の画面を意味します。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect> ハードウェア アクセラレータなしで表示する内容はすべて影響を受けるを強制します。  最適なパフォーマンスを使用しない<xref:System.Windows.Media.Effects.BitmapEffect>です。|  
  
## <a name="performance-impact-medium"></a>パフォーマンスへの影響: 中  
  
|プロパティ|推奨事項|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュが共有頂点三角形として定義されていて、その頂点の位置が、通常、およびテクスチャ座標、共有される各頂点を 1 回だけを定義してでインデックスを使用して、三角形を定義<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>です。|  
|<xref:System.Windows.Media.ImageBrush>|サイズを明示的に制御がある場合、テクスチャ サイズを最小限に抑えてください (使用している場合、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>や、 <xref:System.Windows.Media.ImageBrush>)。  低い解像度のテクスチャが画質の低下、品質とパフォーマンスのバランスを探してみましょうできますを注意してください。|  
|不透明度|半透明の 3D のコンテンツ (など) の反射) をレンダリングするときに、不透明度プロパティを使用して、ブラシまたは資料 (経由で<xref:System.Windows.Media.Brush.Opacity%2A>または<xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>) 半透明別に作成するのではなく<xref:System.Windows.Controls.Viewport3D>を設定して`Viewport3D.Opacity`1 より小さい値にします。|  
|<xref:System.Windows.Controls.Viewport3D>|数を最小限に抑える<xref:System.Windows.Controls.Viewport3D>場面で使用しているオブジェクトします。  モデルごとに個別の Viewport3D インスタンスを作成するのではなく、同じ Viewport3D に多数の 3D モデルを配置します。|  
|<xref:System.Windows.Freezable>|通常は再利用すると役に立つ<xref:System.Windows.Media.Media3D.MeshGeometry3D>、<xref:System.Windows.Media.Media3D.GeometryModel3D>ブラシ、および資料です。  派生しているために、すべてのどれ`Freezable`です。|  
|<xref:System.Windows.Freezable>|呼び出す、<xref:System.Windows.Freezable.Freeze%2A>アプリでそれらのプロパティが残っていなくても Freezable のメソッドは変更されません。  固定では、ワーキング セットを短縮でき、速度を向上することができます。|  
|<xref:System.Windows.Media.Brush>|使用して<xref:System.Windows.Media.ImageBrush>の代わりに<xref:System.Windows.Media.VisualBrush>または<xref:System.Windows.Media.DrawingBrush>ブラシのコンテンツが変更されない場合。  2D のコンテンツに変換できる、<xref:System.Windows.Controls.Image>を介して<xref:System.Windows.Media.Imaging.RenderTargetBitmap>で使用し、<xref:System.Windows.Media.ImageBrush>です。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|使用しない<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>実際の背面を表示する必要がない限り、<xref:System.Windows.Media.Media3D.GeometryModel3D>です。|  
|<xref:System.Windows.Media.Media3D.Light>|ライトの速度 (最高への最も遅い):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュ サイズがこれらの制限を維持しようとしてください。<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20,001<xref:System.Windows.Media.Media3D.Point3D>インスタンス<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60,003<xref:System.Int32>インスタンス|  
|<xref:System.Windows.Media.Media3D.Material>|素材の処理速度の (低速に最も速い):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 一貫した方法で 3D を非表示のブラシ (黒のアンビエント ブラシ、クリア ブラシなど) 除外しません。  シーンからこれらを省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|各<xref:System.Windows.Media.Media3D.Material>で、<xref:System.Windows.Media.Media3D.MaterialGroup>多くの資料を含むため、別のレンダリング パスと、単純なマテリアルでも、ご使用の GPU の塗りつぶし要求を飛躍的に増加することができます。  製品の数を最小限に抑える、<xref:System.Windows.Media.Media3D.MaterialGroup>です。|  
  
## <a name="performance-impact-low"></a>パフォーマンスに影響します低。  
  
|プロパティ|推奨事項|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|ときにアニメーションが不要またはデータ変換を複数の変換を含むグループを使用する代わりに、バインディングは、1 つを使用して<xref:System.Windows.Media.Media3D.MatrixTransform3D>には、それ以外の場合独立して存在トランス フォーム グループのすべての変換の製品であることに設定します。|  
|<xref:System.Windows.Media.Media3D.Light>|ライト、シーン内の数を最小限に抑えます。 シーンに光源が多すぎますが強制的に[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ソフトウェア レンダリングにフォールバックします。  制限は 110 ではほぼ<xref:System.Windows.Media.Media3D.DirectionalLight>オブジェクト、70<xref:System.Windows.Media.Media3D.PointLight>オブジェクト、または 40<xref:System.Windows.Media.Media3D.SpotLight>オブジェクト。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|静的オブジェクトから個別に置くことによってオブジェクトの移動を区切る<xref:System.Windows.Media.Media3D.ModelVisual3D>インスタンス。  ModelVisual3D がより「重い」<xref:System.Windows.Media.Media3D.GeometryModel3D>変換後の境界がキャッシュされるためです。  GeometryModel3D がするように最適化は、モデルシーン ノードにするのには、ModelVisual3D が最適化されます。  GeometryModel3D の共有インスタンスをシーンにするのにには、ModelVisual3D を使用します。|  
|<xref:System.Windows.Media.Media3D.Light>|シーン内のライトの数を変更した回数を最小限に抑えます。  光源の数のそれぞれの変更は、その構成が既に存在していた (とそのシェーダーがキャッシュしたがって) しない限り、強制的シェーダーの再生と再コンパイルします。|  
|淡色|黒のランプは見えませんが、時間を表示するために追加されます。これらを省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|大規模なコレクションの構築時を最小限に抑える[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、MeshGeometry3D のなど<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>、 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>、 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>、および<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>値の母集団の前に、コレクションのサイズを事前です。 可能であれば、配列またはリストなど、コレクションのコンス トラクター事前設定済みのデータ構造体を渡します。|  
  
## <a name="see-also"></a>関連項目  
 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
