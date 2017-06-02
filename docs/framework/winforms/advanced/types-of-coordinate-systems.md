---
title: "座標系の種類 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "座標系"
  - "デバイス座標系"
  - "ページ座標系"
  - "ページ変換"
  - "変換, ページ"
  - "変換, ワールド"
  - "単位"
  - "ワールド座標系"
  - "ワールド変換"
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 座標系の種類
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、ワールド座標空間、ページ座標空間、およびデバイス座標空間の 3 種類を使用します。  ワールド座標は、特定のグラフィック ワールドをモデル化するために使用する座標であり、.NET Framework でメソッドに渡す座標です。  ページ座標とは、フォームやコントロールなどの描画サーフェイスで使用される座標系です。  デバイス座標とは、画面や紙などの、描画が行われる物理デバイスで使用される座標です。  `myGraphics.DrawLine(myPen, 0, 0, 160, 80)` を呼び出す場合、<xref:System.Drawing.Graphics.DrawLine%2A> メソッドに渡す点 `(0, 0)` と `(160, 80)` は、ワールド座標空間内の点です。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] が画面上に直線を描画する前に、この座標に対して一連の変換処理が適用されます。  つまり、ワールド変換によってワールド座標がページ座標に変換され、次にページ変換によってページ座標がデバイス座標に変換されます。  
  
## 変換と座標系  
 クライアント領域の左上隅ではなく内側に原点がある座標系を使用するとします。  たとえば、クライアント領域の左端から 100 ピクセル、上端から 50 ピクセルの点を原点にするとします。  この座標系を、次の図に示します。  
  
 ![座標系](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.png "AboutGdip05\_art01")  
  
 `myGraphics.DrawLine(myPen, 0, 0, 160, 80)` を呼び出すと、次の図に示す直線が描画されます。  
  
 ![座標系](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.png "AboutGdip05\_art02")  
  
 この直線の端点の座標は、3 つの座標空間では、それぞれ次のようになります。  
  
|||  
|-|-|  
|World|\(0, 0\) ～ \(160, 80\)|  
|ページ|\(100, 50\) ～ \(260, 130\)|  
|デバイス|\(100, 50\) ～ \(260, 130\)|  
  
 ページ座標空間の原点は、常にクライアント領域の左上隅です。  また、単位がピクセルであるため、デバイス座標はページ座標と同じになります。  単位をピクセル以外のインチなどに設定すると、デバイス座標はページ座標と異なる値になります。  
  
 ワールド座標からページ座標への変換をワールド変換と呼び、この変換は <xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.Transform%2A> プロパティが保持します。  上の例のワールド変換は、x 方向に 100 単位、y 方向に 50 単位の平行移動です。  <xref:System.Drawing.Graphics> オブジェクトのワールド変換を設定し、その <xref:System.Drawing.Graphics> オブジェクトを使用して上の図に示す直線を描画する例を次に示します。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 ページ座標からデバイス座標への変換をページ変換と呼びます。  <xref:System.Drawing.Graphics> クラスには、ページ変換を操作するための <xref:System.Drawing.Graphics.PageUnit%2A> プロパティと <xref:System.Drawing.Graphics.PageScale%2A> プロパティが用意されています。  <xref:System.Drawing.Graphics> クラスには、ディスプレイ デバイスの水平方向および垂直方向の dpi \(インチごとのドット数\) を調べるために、<xref:System.Drawing.Graphics.DpiX%2A> と <xref:System.Drawing.Graphics.DpiY%2A> の 2 つの読み取り専用プロパティも用意されています。  
  
 <xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.PageUnit%2A> プロパティを使用して、ピクセル以外の単位を指定できます。  
  
> [!NOTE]
>  <xref:System.Drawing.Graphics.PageUnit%2A> プロパティを <xref:System.Drawing.GraphicsUnit> に設定することはできません。これは物理単位ではないため、例外が発生します。  
  
 \(0, 0\) から \(2, 1\) まで直線を描画する例を次に示します。ここで、点 \(2, 1\) は、点 \(0, 0\) から右に 2 インチ、下に 1 インチの位置にあります。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  ペンを構築するときにペン幅を指定しないと、上の例では 1 インチ幅の直線が描画されます。  ペンの幅は、次に示すように <xref:System.Drawing.Pen> コンストラクターの 2 番目の引数で指定できます。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 ディスプレイ デバイスの dpi が水平方向で 96 ドット、垂直方向で 96 ドットであると仮定すると、上の例で示した直線の端点の座標は、3 つの座標空間では、それぞれ次のようになります。  
  
|||  
|-|-|  
|World|\(0, 0\) ～ \(2, 1\)|  
|ページ|\(0, 0\) ～ \(2, 1\)|  
|デバイス|\(0, 0\) ～ \(192, 96\)|  
  
 ワールド座標空間の原点はクライアント領域の左上隅であるため、ページ座標はワールド座標と同じになります。  
  
 さまざまな効果を得るために、ワールド変換とページ変換を組み合わせて実行できます。  たとえば、単位としてインチを使用し、座標系の原点として、クライアント領域の左端から 2 インチ、上端から 1\/2 インチの点を使用するとします。  <xref:System.Drawing.Graphics> オブジェクトのワールド変換とページ変換を設定し、\(0, 0\) から \(2, 1\) まで直線を描画する例を次に示します。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 この直線と座標系を次の図に示します。  
  
 ![座標系](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.png "AboutGdip05\_art03")  
  
 ディスプレイ デバイスの dpi が水平方向で 96 ドット、垂直方向で 96 ドットであると仮定すると、上の例で示した直線の端点の座標は、3 つの座標空間では、それぞれ次のようになります。  
  
|||  
|-|-|  
|World|\(0, 0\) ～ \(2, 1\)|  
|ページ|\(2, 0.5\) ～ \(4, 1.5\)|  
|デバイス|\(192, 48\) ～ \(384, 144\)|  
  
## 参照  
 [座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [変換の行列表現](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)