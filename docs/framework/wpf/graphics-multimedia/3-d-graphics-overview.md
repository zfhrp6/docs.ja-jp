---
title: "3-D グラフィックスの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "3-D グラフィックス"
  - "グラフィックス [WPF], 3-D"
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 3-D グラフィックスの概要
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 機能により、マークアップ コードおよび手順コードの両方で、開発者は 3\-D グラフィックスを描画、変換、およびアニメーション化できます。  開発者は、[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] グラフィックスと [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] グラフィックスを組み合わせることで、多彩なコントロールを作成したり、複雑なイラストレーションのデータを提供したり、アプリケーション インターフェイスのユーザー エクスペリエンスを向上させることができます。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] での [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] サポートは、多機能なゲーム開発プラットフォームを提供するために設計されたものではありません。このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] グラフィックス システムの [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] 機能の概要について説明します。  
  
   
  
<a name="threed_in_2d"></a>   
## 2\-D コンテナー内の 3\-D グラフィックス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] グラフィックス コンテンツは、2 次元要素の構造内に追加できる <xref:System.Windows.Controls.Viewport3D> 要素内にカプセル化されます。  グラフィックス システムでは、他の多くの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と同様に、<xref:System.Windows.Controls.Viewport3D> を 2 次元のビジュアル要素として扱います。  <xref:System.Windows.Controls.Viewport3D> は、3 次元シーンへのウィンドウ \(ビューポート\) として機能します。  正確には、[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] シーンが投影されるサーフェイスです。  
  
 従来の [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] アプリケーションでは、Grid や Canvas などの他のコンテナー要素と同じように <xref:System.Windows.Controls.Viewport3D> を使用します。  <xref:System.Windows.Controls.Viewport3D> と他の [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 描画オブジェクトを同じシーン グラフで使用することはできますが、<xref:System.Windows.Controls.Viewport3D> 内で [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] オブジェクトと [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] オブジェクトを相互に貫入させることはできません。  ここでは、<xref:System.Windows.Controls.Viewport3D> 内で [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] グラフィックスを描画する方法を中心に説明します。  
  
<a name="coord_space"></a>   
## 3\-D 座標空間  
 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] グラフィックスの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 座標系では、レンダリング領域 \(通常は画面\) の左上に原点を置きます。  [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 座標系では、正の x 軸の値で右に移動し、正の y 軸の値で下に移動します。  しかし、[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 座標系では、原点はレンダリング領域の中心に置かれ、正の x 軸の値で右に移動しますが、正の y 軸の値では上に移動し、さらに正の z 軸の値で原点から離れて閲覧者に向かう方向に移動します。  
  
 ![座標系](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem\-1")  
従来の 2\-D 座標系および 3\-D 座標系の表現  
  
 これらの軸によって定義される空間は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] オブジェクトを参照する静止座標系です。  この座標空間にモデルを構築し、照明とカメラを作成して表示するときに、この静止座標系、つまり "ワールド座標" と、変換を適用するときにモデルごとに作成するローカル座標とを区別すると役に立ちます。  また、ワールド座標のオブジェクトは、照明とカメラの設定によってまったく違って見えたり何も表示されないことがあります。ただし、カメラの位置によってワールド座標におけるオブジェクトの場所が変わることはありません。  
  
<a name="cameras"></a>   
## カメラと投影  
 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] を操作する開発者は、2 次元の画面上に描画プリミティブを配置することに慣れています。  [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] シーンを作成するときには、実際は [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] オブジェクトの [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 表現を作成しているということを忘れないことが重要です。  [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] シーンは閲覧者の視点によって異なって見えるため、視点を指定する必要があります。  この [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] シーンの視点は、<xref:System.Windows.Media.Media3D.Camera> クラスによって指定できます。  
  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] シーンを [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] サーフェイス上で表現する方法を理解するために、表示するサーフェイス上への投影としてシーンを説明することもできます。  <xref:System.Windows.Media.Media3D.ProjectionCamera> では、閲覧者からの [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] モデルの見え方を変化させる多様な投影とそのプロパティを指定できます。  <xref:System.Windows.Media.Media3D.PerspectiveCamera> は、シーンを遠近短縮する投影を指定します。  つまり、<xref:System.Windows.Media.Media3D.PerspectiveCamera> は、消失点の視野を提供します。  シーンの座標空間内のカメラの位置、カメラの向きと視野、およびシーン内での "上" の方向を定義するベクターを指定できます。  <xref:System.Windows.Media.Media3D.PerspectiveCamera> の投影を表す図を次に示します。  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera> の <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> プロパティと <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> プロパティは、カメラの投影の範囲を制限します。  カメラはシーン内の任意の場所に配置できるため、カメラの実際の配置がモデルの内部だったりモデルに近すぎたりして、オブジェクトを適切に識別できなくなる可能性もあります。  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> では、その距離を超えるとオブジェクトが描画されなくなる、カメラからの最短の距離を指定できます。  逆に、<xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> では、識別できないほど離れたオブジェクトがシーンに含まれないように、その距離を超えるとオブジェクトが描画されなくなる、カメラからの最長の距離を指定できます。  
  
 ![カメラ設定](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-6.png "CoordSystem\-6")  
カメラの位置  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> は、[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] ビジュアル サーフェイスに対する [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] モデルの正投影を指定します。  他のカメラと同様に、位置、表示方向、および "上向き" 方向を指定します。  ただし、<xref:System.Windows.Media.Media3D.PerspectiveCamera> とは異なり、<xref:System.Windows.Media.Media3D.OrthographicCamera> は遠近短縮を含まない投影を記述します。  つまり、<xref:System.Windows.Media.Media3D.OrthographicCamera> は、辺がカメラの 1 点に集まる表示ボックスではなく、辺が平行な表示ボックスを記述します。  次の図は、<xref:System.Windows.Media.Media3D.PerspectiveCamera> および <xref:System.Windows.Media.Media3D.OrthographicCamera> を使用して表示した同じモデルを示しています。  
  
 ![正投影とパースペクティブ射影](../../../../docs/framework/wpf/graphics-multimedia/media/camera-projections4.png "Camera\_projections4")  
透視投影と正投影  
  
 次のコードは、一般的なカメラの設定を示しています。  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## モデルとメッシュ プリミティブ  
 <xref:System.Windows.Media.Media3D.Model3D> は、汎用 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] オブジェクトを表す抽象基本クラスです。  [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] シーンを構築するには、表示するためのオブジェクトが必要です。シーン グラフを構成するオブジェクトは、<xref:System.Windows.Media.Media3D.Model3D> から派生します。  現在、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、<xref:System.Windows.Media.Media3D.GeometryModel3D> でモデリングするジオメトリをサポートしています。  このモデルの <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> プロパティは、メッシュ プリミティブを受け取ります。  
  
 モデルを構築するには、プリミティブまたはメッシュを構築することから開始します。  [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] プリミティブは、単一の [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] エンティティを形成する頂点のコレクションです。  大多数の [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] システムは、最も単純な閉じた図形、つまり 3 つの頂点で定義された三角形に基づいてモデル化されるプリミティブを提供します。  三角形の 3 つの点は同一平面上にあるため、さらに複雑な図形 \(メッシュ\) をモデル化するために引き続きいくつかの三角形を追加できます。  
  
 現在の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] システムには、ジオメトリを指定できる <xref:System.Windows.Media.Media3D.MeshGeometry3D> クラスが用意されています。現時点では、球体や立方体のような定義済みの [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] プリミティブはサポートしていません。  三角形の頂点のリストを <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> プロパティとして指定して、<xref:System.Windows.Media.Media3D.MeshGeometry3D> の作成を開始します。  各頂点は、<xref:System.Windows.Media.Media3D.Point3D> として指定します   \([!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、各頂点の座標を表して 3 つにグループ化した数値のリストとしてこのプロパティを指定します\)。ジオメトリに応じて、メッシュは、一部が同じ角 \(頂点\) を共有する数多くの三角形で構成される場合があります。  メッシュを正しく描画するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は複数の三角形が共有する頂点に関する情報を必要とします。  この情報を与えるには、三角形のインデックスのリストとその <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> プロパティを指定します。  このリストは、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> リストに指定された点が三角形を決定する順序を示します。  
  
 [!code-xml[basic3d#Basic3DXAML3DN3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 前の例で、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> リストには、立方体の形状のメッシュを定義する 8 つの頂点を指定しています。  <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> プロパティでは、3 つのインデックスの 12 のグループのリストを指定しています。  リスト内の各数値は、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> リストへのオフセットを参照します。  たとえば、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> リストで指定される最初の 3 つの頂点は、\(1,1,0\)、\(0,1,0\)、および \(0,0,0\) です。  <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> リストに指定される最初の 3 つのインデックスは、0、2、および 1 です。これは、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> リスト内の 1 番目の点、3 番目の点、2 番目の点に対応します。  結果として、立方体モデルを形成する最初の三角形は \(1,1,0\) から \(0,1,0\)、\(0,0,0\) で構成され、残りの 11 の三角形も同様に決定されます。  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> プロパティおよび <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> プロパティの値を指定して、モデルの定義を続行できます。  モデルのサーフェイスをレンダリングするために、グラフィックス システムは、指定された任意の三角形でサーフェイスが向いている方向に関する情報を必要とします。  この情報はモデルの光源計算に使用されます。直接光源に向いているサーフェイスは、光源から離れた角度のサーフェイスよりも明るく見えます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、位置座標を使用して既定の法線ベクターを決定できます。曲面のサーフェイスの外観に接する別の法線ベクターを指定することもできます。  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> プロパティは、メッシュの頂点にテクスチャを描画する方法を決定する座標のマッピング方法をグラフィックス システムに通知する <xref:System.Windows.Point> のコレクションを指定します。  <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> は、0 ～ 1 の値として指定されます。  <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> プロパティの場合と同様に、グラフィックス システムは既定のテクスチャ座標を計算できますが、たとえば、繰り返すパターンの一部を含むテクスチャのマッピングを制御する別のテクスチャ座標の設定を選択することもできます。  テクスチャ座標に関する追加の情報は、後続のトピックまたは Managed Direct3D SDK を参照してください。  
  
 手順コードで立方体モデルの 1 つの面を作成する方法を次の例に示します。  立方体の全体を単一の GeometryModel3D として描画できます。この例では、後で各面に別々のテクスチャを適用するために、立方体の表面を別個のモデルとして描画しています。  
  
 [!code-csharp[3doverview#3DOverview3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## モデルへのマテリアルの適用  
 メッシュは 3 次元オブジェクトのように見えますが、光を発してカメラに映るには、頂点と三角形によって定義されるサーフェイスを覆うテクスチャの適用が必要です。  [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] では、<xref:System.Windows.Media.Brush> クラスを使用して、色、パターン、グラデーション、または他のビジュアル コンテンツを画面の領域に適用します。  しかし、[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] オブジェクトの外観は、適用された単なる色またはパターンではなく、照明モデルの機能です。  実世界のオブジェクトは、サーフェイスの品質によって光の反射の仕方が異なります。光沢があって輝いているサーフェイスは、粗くマットなサーフェイスの外観と同じではありません。光を吸収するように見えるオブジェクトもあれば、光を放つように見えるオブジェクトもあります。  [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] オブジェクトに適用できるブラシはすべて [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] オブジェクトにも適用できますが、直接適用することはできません。  
  
 モデルのサーフェイスの特性を定義するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は <xref:System.Windows.Media.Media3D.Material> 抽象クラスを使用します。  Material の具象サブクラスは、モデル サーフェイスの外観の特性の一部を決定します。それぞれが、SolidColorBrush、TileBrush、または VisualBrush を渡す Brush プロパティを提供します。  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial> は、そのモデルが光を拡散させるかのように、ブラシをモデルに適用することを指定します。  DiffuseMaterial の使用は、[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] モデルに直接ブラシを使用することに似ています。モデルのサーフェイスは光沢のようには光を反射しません。  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial> は、モデルのサーフェイスが硬質であるかのように、または光沢があってハイライトを反射できるかのように、ブラシをモデルに適用することを指定します。  <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> プロパティの値を指定することによって、この反射の品質 \("輝き"\) を示すテクスチャの度合いを設定できます。  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial> では、モデルがブラシの色と同じ光を放射しているかのように、テクスチャを適用することを指定できます。  これは、モデルを光源にするものではありませんが、DiffuseMaterial または SpecularMaterial でテクスチャを適用した場合とは異なる影を加えます。  
  
 パフォーマンスの向上のために、<xref:System.Windows.Media.Media3D.GeometryModel3D> の背面 \(これらの面は、カメラの反対側に位置するモデルの面なので、表示されません\) はシーンから除かれます。  <xref:System.Windows.Media.Media3D.Material> を指定して平面のようなモデルの背面に適用するには、モデルの <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> プロパティを設定します。  
  
 光り輝く効果や反射の効果のようなサーフェイスの品質を実現するために、モデルに数種類のブラシを続けて適用することができます。  <xref:System.Windows.Media.Media3D.MaterialGroup> クラスを使用すると、複数のマテリアルを適用し、再利用できます。  MaterialGroup の子は、複数の描画パスの始めから終わりまで適用されます。  
  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] モデルにブラシとして純色と描画を適用する方法を次のコード例に示します。  
  
 [!code-xml[basic3d#Basic3DXAML3DN5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xml[3doverview#3DOverview3DN9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## シーンの照明  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] グラフィックス内の光源は、現実の世界で光が果たす役割を果たします。つまり、サーフェイスを見えるようにします。  さらに、光源は、投影に含まれるシーンの部分を決定します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の光源オブジェクトは、多彩な光と影の効果を作り出し、現実の世界のさまざまな光源の振る舞いに従ってモデル化されます。  シーンには少なくとも 1 つの光源を入れる必要があります。そうしないと、モデルが表示されません。  
  
 次の光源は、<xref:System.Windows.Media.Media3D.Light> 基本クラスから派生します。  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>: 位置や向きに関係なく、すべてのオブジェクトを一様に照らすアンビエント光を提供します。  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>: 遠くにある光源のように照らします。  指向性のある光源には、Vector3D として指定される <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> はありますが、特定の位置はありません。  
  
-   <xref:System.Windows.Media.Media3D.PointLight>: 隣接する光源のように照らします。  PointLight には位置があり、その位置から光を投げかけます。  シーン内のオブジェクトは、その位置と、光源に対する距離に応じて照らされます。  <xref:System.Windows.Media.Media3D.PointLightBase> は <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> プロパティを公開します。これは、モデルが光源によって照らされなくなる距離を決定します。  PointLight は、光の強さが距離に応じて減少する割合を決定する減衰のプロパティを公開します。  光の減衰には定数補間、線形補間、または 2 次補間を指定できます。  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>: <xref:System.Windows.Media.Media3D.PointLight> から継承します。  スポットライトは PointLight のように照らし、位置と方向の両方があります。  <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> プロパティおよび <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> プロパティによって設定される円すい形の領域に、指定された程度の光を投射します。  
  
 光源は <xref:System.Windows.Media.Media3D.Model3D> オブジェクトなので、位置、色、方向、および範囲などの光源のプロパティを変換したり、アニメーション化したりできます。  
  
 [!code-xml[hittest3d#HitTest3D3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## モデルの変換  
 モデルを作成すると、モデルはシーン内の特定の場所に配置されます。  モデルをシーン内で移動したり、回転したり、サイズを変更したりするために、モデル自身を定義する頂点を変更するのは実用的ではありません。  代わりに、[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] と同様、モデルに変換を適用します。  
  
 各モデル オブジェクトには、<xref:System.Windows.Media.Media3D.Model3D.Transform%2A> プロパティがあり、モデルを移動したり、向きやサイズを変更したりできます。  変換を適用すると、変換で指定されたベクターまたは値だけ効果的にモデルのすべての点をオフセットすることができます。  つまり、モデルが定義されている座標空間 \(モデル空間\) を変換しても、シーン全体の座標系におけるモデルの図形座標 \(ワールド座標\) を構成する値は変更されません。  
  
 モデルの変換の詳細については、「[3\-D 変換の概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md)」を参照してください。  
  
<a name="animations"></a>   
## モデルへのアニメーションの適用  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 実装は、[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] グラフィックスと同じタイミングとアニメーション システムに追加されます。  つまり、3\-D シーンにアニメーションを適用するには、そのモデルのプロパティにアニメーションを適用します。  プリミティブのプロパティに直接アニメーションを適用できますが、通常はモデルの位置や外観を変更する変換にアニメーションを適用する方が簡単です。  変換は、個々のモデル同様、<xref:System.Windows.Media.Media3D.Model3DGroup> オブジェクトに適用できるため、Model3DGroup の子にアニメーションのセットを適用し、子オブジェクトのグループに別のアニメーションのセットを適用することが可能です。  シーンの光源のプロパティをアニメーション化することによって、さまざまな視覚効果を実現できます。  最後に、カメラの位置または視野をアニメーション化することによって、投影自体をアニメーション化することもできます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のタイミングとアニメーション システムに関する背景情報については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」、および「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のオブジェクトをアニメーション化するには、タイムラインを作成し、アニメーションを定義し \(これは、実際は一定期間にわたって一部のプロパティ値を変更します\)、アニメーションを適用するプロパティを指定します。  [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] シーン内のすべてのオブジェクトは <xref:System.Windows.Controls.Viewport3D> の子であるため、シーンに適用するアニメーションの対象となるプロパティは、Viewport3D のプロパティになります。  
  
 モデルが同じ場所で揺れて見えるようにするとします。  モデルに <xref:System.Windows.Media.Media3D.RotateTransform3D> を適用して、あるベクターから別のベクターへの回転の軸にアニメーションを適用できます。  RotateTransform3D は TransformGroup でモデルに適用されている複数の変換の 1 つであるという前提で、Vector3DAnimation を変換の Rotation3D の Axis プロパティに適用する方法を次のコード例に示します。  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## ウィンドウへの 3\-D コンテンツの追加  
 シーンを描画するには、モデルと光源を <xref:System.Windows.Media.Media3D.Model3DGroup> に追加し、その <xref:System.Windows.Media.Media3D.Model3DGroup> を <xref:System.Windows.Media.Media3D.ModelVisual3D> の <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> として設定します。  <xref:System.Windows.Media.Media3D.ModelVisual3D> を <xref:System.Windows.Controls.Viewport3D> の <xref:System.Windows.Controls.Viewport3D.Children%2A> コレクションに追加します。  <xref:System.Windows.Controls.Viewport3D.Camera%2A> プロパティを設定することによって、カメラを <xref:System.Windows.Controls.Viewport3D> に追加します。  
  
 最後に、ウィンドウに <xref:System.Windows.Controls.Viewport3D> を追加します。  <xref:System.Windows.Controls.Viewport3D> が Canvas などのレイアウト要素のコンテンツとして含まれる場合、その <xref:System.Windows.FrameworkElement.Height%2A> プロパティおよび <xref:System.Windows.FrameworkElement.Width%2A> プロパティ \(<xref:System.Windows.FrameworkElement> から継承\) を設定することによって、Viewport3D のサイズを設定します。  
  
 [!code-xml[hostingwpfusercontrolinwf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## 参照  
 <xref:System.Windows.Controls.Viewport3D>   
 <xref:System.Windows.Media.Media3D.PerspectiveCamera>   
 <xref:System.Windows.Media.Media3D.DirectionalLight>   
 <xref:System.Windows.Media.Media3D.Material>   
 [3\-D 変換の概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md)   
 [WPF の 3D パフォーマンスの最大化](../../../../docs/framework/wpf/graphics-multimedia/maximize-wpf-3d-performance.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-how-to-topics.md)   
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)