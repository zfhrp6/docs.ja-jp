---
title: "グローバル変換とローカル変換 | Microsoft Docs"
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
  - "行列, 使用 (変換を)"
  - "変換, global"
  - "変換, local"
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# グローバル変換とローカル変換
グローバル変換は、特定の <xref:System.Drawing.Graphics> オブジェクトで描画されるすべての項目に対して適用される変換です。  これに対し、ローカル変換は、描画される特定の項目に対して適用される変換です。  
  
## グローバル変換  
 グローバル変換を行うには、<xref:System.Drawing.Graphics> オブジェクトを作成し、そのオブジェクトの <xref:System.Drawing.Graphics.Transform%2A> プロパティを操作します。  <xref:System.Drawing.Graphics.Transform%2A> プロパティは <xref:System.Drawing.Drawing2D.Matrix> オブジェクトであるため、連続するアフィン変換の任意の組み合わせを保持できます。  <xref:System.Drawing.Graphics.Transform%2A> プロパティに格納される変換を、ワールド変換と呼びます。  <xref:System.Drawing.Graphics> クラスには、複合ワールド変換を構築するためのメソッドとして、<xref:System.Drawing.Graphics.MultiplyTransform%2A>、<xref:System.Drawing.Graphics.RotateTransform%2A>、<xref:System.Drawing.Graphics.ScaleTransform%2A>、および <xref:System.Drawing.Graphics.TranslateTransform%2A> が用意されています。  ワールド変換の作成前に 1 回、作成後に 1 回楕円を描画する例を次に示します。  この変換では、y 方向にファクター 0.5 のスケーリング、x 方向に 50 単位の平行移動、30°の回転を順に実行します。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 この変換で使用される行列を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05\_art14")  
  
> [!NOTE]
>  上の例の楕円の回転の中心は座標系の原点で、これはクライアント領域の左上隅にあります。  この結果は、回転の中心が楕円の中心である場合とは異なります。  
  
## ローカル変換  
 ローカル変換は、描画される特定の項目に対して適用されます。  たとえば、<xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトの <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> メソッドを使用すると、そのパスのデータ点を変換できます。  次の例は、変換せずに四角形を描画し、回転変換を実行してパスを描画します。  ワールド変換は適用されないことを前提とします。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 さまざまな結果を得るために、ワールド変換とローカル変換を組み合わせて実行できます。  たとえば、ワールド変換を使用して座標系を変更し、新しい座標系上に描画されたオブジェクトをローカル変換を使用して回転およびスケーリングできます。  
  
 たとえば、クライアント領域の左端から 200 ピクセル、上端から 150 ピクセルの位置にある点を座標系の原点にするとします。  また、単位がピクセル、x 軸が右向き、y 軸が上向きであることを前提とします。  既定の座標系の y 軸は下向きであるため、水平軸を基準とした反転を実行する必要があります。  このような反転の行列を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.png "AboutGdip05\_art15")  
  
 次に、右に 200 単位、下に 150 単位の平行移動を実行する必要があるとします。  
  
 <xref:System.Drawing.Graphics> オブジェクトのワールド変換を設定することにより、上で説明した座標系を設定する例を次に示します。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 左下隅が新しい座標系の原点である四角形 1 つで構成されるパスを作成するコードを次に示します。このコードは、上の例の末尾に記述します。  この四角形は、ローカル変換を適用せずに 1 回、ローカル変換を適用して 1 回塗りつぶされます。  このローカル変換は、水平方向にファクター 2 のスケーリングと、それに続く 30°の回転で構成されます。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 新しい座標系と 2 つの四角形を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.png "AboutGdip05\_art16")  
  
## 参照  
 [座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [マネージ GDI\+ での変換の使用](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)