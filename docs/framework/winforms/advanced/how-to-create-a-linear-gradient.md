---
title: "方法 : 線形グラデーションを作成する | Microsoft Docs"
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
  - "色, 作成 (線形グラデーションを)"
  - "グラデーション"
  - "グラデーション, 作成 (線形)"
  - "線形グラデーション, 作成"
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : 線形グラデーションを作成する
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、水平方向、垂直方向、および対角線方向の線形グラデーションをサポートしています。  既定では、線形グラデーションの色は均等に変化していきます。  しかし、線形グラデーションをカスタマイズして、色が不均等に変化していくようにすることもできます。  
  
 直線、楕円、および四角形を水平方向の線形グラデーション ブラシで塗りつぶす例を次に示します。  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> コンストラクターは、4 つの引数として 2 つの点と 2 つの色を受け取ります。  最初の点 \(0, 10\) は最初の色 \(赤\) に関連付けられており、2 番目の点 \(200, 10\) は 2 番目の色 \(青\) に関連付けられています。  想定されるとおり、\(0, 10\) から \(200, 10\) へと描画された直線は、赤から青に段階的に変化していきます。  
  
 点 \(50, 10\) と点 \(200, 10\) の座標内の 10 という値そのものは重要ではありません。  ここで重要なのは、2 つの点の 2 番目の座標が同じであること、つまり 2 つの点を結ぶ直線が水平であるということです。  楕円と四角形も水平方向の座標値が 0 から 200 に移動するにつれて、赤から青に段階的に変化していきます。  
  
 これらの直線、楕円、および四角形を次の図に示します。  水平方向の座標値が 200 を超えた場合は、同じグラデーション パターンが繰り返し適用されます。  
  
 ![線形グラデーション](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")  
  
### 水平方向の線形グラデーションを使用するには  
  
-   3 番目および 4 番目の引数として、それぞれ不透明な赤および不透明な青を渡します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 上の例では、水平方向の座標値が 0 から 200 に移動するにつれて、色の要素が線形に変化していきます。  たとえば、最初の座標が 0 から 200 までの間にある点は、青の要素も 0 から 255 までの間にあります。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、色がグラデーションの一方の端からもう一方の端へ向かって変化していくようすを調整できます。  黒から赤に変化するグラデーション ブラシを次の表に基づいて作成する場合を考えます。  
  
|水平方向の座標|RGB コンポーネント|  
|-------------|-----------------|  
|0|\(0, 0, 0\)|  
|40|\(128, 0, 0\)|  
|200|\(255, 0, 0\)|  
  
 水平方向の座標が 0 から 200 までの値の 20% にしか満たない値のときに、赤の要素の輝度が既に最大値の半分になっています。  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush> オブジェクトの <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> プロパティを設定して、3 つの相対的な輝度値を 3 つの相対位置に関連付ける例を次に示します。  上の表で示したように、相対的な輝度値 0.5 を相対位置 0.2 に関連付けます。  このコードは、楕円および四角形をグラデーション ブラシで塗りつぶします。  
  
 結果として得られた楕円と四角形を次の図に示します。  
  
 ![線形グラデーション](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")  
  
### 線形グラデーションをカスタマイズするには  
  
-   3 番目および 4 番目の引数として、それぞれ不透明な黒および不透明な赤を渡します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 上の例のグラデーションは水平方向であり、つまり、水平線に沿って移動するにつれて色が段階的に変化していきました。  垂直方向のグラデーションと対角線方向のグラデーションも定義できます。  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> コンストラクターに点 \(0, 0\) と点 \(200, 100\) を渡す例を次に示します。  青色は点 \(0, 0\) に関連付けられており、緑色は点 \(200, 100\) に関連付けられています。  直線 \(ペン幅が 10\) と楕円が、線形グラデーション ブラシで塗りつぶされます。  
  
 これらの直線と楕円を次の図に示します。  点 \(0, 0\) から点 \(200, 100\) を結ぶ直線と平行な直線に沿って移動するにつれて、楕円内の色が段階的に変化しています。  
  
 ![線形グラデーション](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")  
  
### 対角線方向の線形グラデーションを作成するには  
  
-   3 番目および 4 番目の引数として、それぞれ不透明な青および不透明な緑を渡します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## 参照  
 [グラデーション ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)