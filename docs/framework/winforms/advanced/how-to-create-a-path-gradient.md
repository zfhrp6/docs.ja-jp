---
title: "方法 : パス グラデーションを作成する | Microsoft Docs"
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
  - "グラデーション, 作成 (パスを)"
  - "グラフィックス パス, 作成 (グラデーションを)"
  - "パス グラデーション, 作成"
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : パス グラデーションを作成する
<xref:System.Drawing.Drawing2D.PathGradientBrush> クラスを使用すると、図形を塗りつぶすときの段階的な色の変化をカスタマイズできます。  たとえば、パスの中心に 1 つの色を指定し、パスの境界に別の色を指定できます。  また、パスの境界上にある点ごとに個別の色を指定することもできます。  
  
> [!NOTE]
>  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] におけるパスとは、<xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトによって維持される連続した複数の直線と曲線のことです。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] パスの詳細については、「[GDI\+ でのグラフィックス パス](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)」、および「[パスの作成および描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)」を参照してください。  
  
### パス グラデーションを使用して楕円を塗りつぶすには  
  
-   パス グラデーション ブラシで楕円を塗りつぶす例を次に示します。  中心の色が青に設定され、境界の色が明るい緑青に設定されています。  塗りつぶされた楕円を次の図に示します。  
  
     ![グラデーション パス](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")  
  
     既定では、パス グラデーション ブラシはパスの境界の外側には拡張されません。  パス グラデーション ブラシを使用して、パスの境界の外側まで図を塗りつぶす場合、パスの外側にある画面領域は塗りつぶされません。  
  
     次のコードの <xref:System.Drawing.Graphics.FillEllipse%2A> の呼び出しを `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)` に変更した場合に実行される処理を、次の図に示します。  
  
     ![グラデーション パス](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     このコード例は Windows フォームでの使用を前提としたものであり、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> が必要です。  
  
### 境界上の点を指定するには  
  
-   星型のパスからパス グラデーション ブラシを生成する例を次に示します。  このコードでは、星型の重心の色として赤を指定するように <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> プロパティを設定します。  次に、<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> プロパティを設定して、`points` 配列内の個々の点に、`colors` 配列に格納されているさまざまな色を指定します。  最後のコード ステートメントは、星型のパスをパス グラデーション ブラシで塗りつぶします。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   コード内で <xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトを使用せずに、パス グラデーションを描画する例を次に示します。  この例で使用されている特定の <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> コンストラクターは点の配列を受け取りますが、<xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトは必要としません。  また、<xref:System.Drawing.Drawing2D.PathGradientBrush> は、パスではなく四角形を塗りつぶすために使用されています。  この四角形は、ブラシを定義するために使用した閉じたパスよりも大きいため、四角形の一部はブラシによって塗りつぶされていません。  四角形 \(点線\) とパス グラデーション ブラシによって塗りつぶされた四角形部分を次の図に示します。  
  
     ![グラデーション](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### パス グラデーションをカスタマイズするには  
  
-   パス グラデーション ブラシをカスタマイズする方法の 1 つとして、そのブラシの <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> プロパティを設定する方法があります。  フォーカス スケールは、メイン パスの内側にある内部パスを指定します。  中心の色は、中心点だけでなく、この内部パスの内側すべてに適用されます。  
  
     楕円のパスに基づいてパス グラデーション ブラシを作成する例を次に示します。  このコードでは、境界の色を青に設定し、中心の色を明るい緑青に設定してから、パス グラデーション ブラシで楕円のパスを塗りつぶします。  
  
     次に、パス グラデーション ブラシのフォーカス スケールを設定します。  x フォーカス スケールは 0.3 に、y フォーカス スケールは 0.8 に設定します。  このコードは、<xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.TranslateTransform%2A> メソッドを呼び出して、続けて呼び出す <xref:System.Drawing.Graphics.FillPath%2A> では最初の楕円の右側にある楕円を塗りつぶすようにします。  
  
     フォーカス スケールの効果を確認するために、小さな楕円がメインの楕円と中心を共有すると想定してみます。  小さな \(内部\) 楕円は、メインの楕円を水平方向に 0.3、垂直方向に 0.8 の係数を適用して縮小した図形です。  外側の楕円の境界から内側の楕円の境界に移動するにつれて、色が青から明るい緑青に段階的に変化していきます。  内側の楕円の境界から共有の中心へと移動しても、色は明るい緑青のままです。  
  
     次のコードによる出力を次の図に示します。  左側の楕円は、中心点だけが明るい緑青になっています。  右側の楕円は、内側のパスの内部すべてが明るい緑青になっています。  
  
 ![グラデーション](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### 補間を使用してカスタマイズするには  
  
-   パス グラデーション ブラシをカスタマイズする別の方法として、補間色の配列と補間位置の配列を指定する方法もあります。  
  
     三角形に基づいてパス グラデーション ブラシを作成する例を次に示します。  このコードは、パス グラデーション ブラシの <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> プロパティを設定して、補間色の配列 \(濃い緑、明るい緑青、青\) と補間位置の配列 \(0, 0.25, 1\) を指定します。  三角形の境界から中心点に移動するにつれて、色が濃い緑から明るい緑青へ、さらに明るい緑青から青へと変化していきます。  濃い緑から明るい緑青への変化は、濃い緑から青までの距離の 25% の部分で発生します。  
  
     このカスタム パス グラデーション ブラシで塗りつぶされた三角形を次の図に示します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### 中心点を設定するには  
  
-   既定では、パス グラデーション ブラシの中心点は、ブラシを作成するために使用したパスの重心になります。  <xref:System.Drawing.Drawing2D.PathGradientBrush> クラスの <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> プロパティを設定することによって、中心点の位置を変更できます。  
  
     楕円に基づいてパス グラデーション ブラシを作成する例を次に示します。  この楕円の中心は \(70, 35\) ですが、パス グラデーション ブラシの中心点は \(120, 40\) に設定されています。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     塗りつぶされた楕円とパス グラデーション ブラシの中心点を次の図に示します。  
  
     ![グラデーション パス](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")  
  
-   パス グラデーション ブラシの中心点をそのブラシを作成するために使用したパスの外側の位置に設定することもできます。  前のコードの <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> プロパティを設定するための呼び出しを置換する例を次に示します。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     この変更による出力を次の図に示します。  
  
     ![グラデーション パス](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")  
  
     上の図では、楕円の右端にある点の色は、青にきわめて近い色ですが、純粋な青ではありません。  グラデーション内の色は、塗りつぶしが点 \(145, 35\) にまで達し、その点が純粋な青 \(0, 0, 255\) になるように配置されます。  しかし、パス グラデーション ブラシはそのパスの内側しか塗りつぶさないため、実際の塗りつぶしが点 \(145, 35\) まで達することはありません。  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [グラデーション ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)