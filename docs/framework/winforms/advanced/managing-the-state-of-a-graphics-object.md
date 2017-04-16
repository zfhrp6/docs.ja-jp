---
title: "Graphics オブジェクトの状態の管理 | Microsoft Docs"
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
  - "グラフィックス, クリップする"
  - "グラフィックス, 管理 (状態を)"
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Graphics オブジェクトの状態の管理
<xref:System.Drawing.Graphics> クラスは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] の中核となる役割を果たします。  描画を行う場合は、<xref:System.Drawing.Graphics> オブジェクトを取得し、そのプロパティを設定し、そのメソッド \(<xref:System.Drawing.Graphics.DrawLine%2A>、<xref:System.Drawing.Graphics.DrawImage%2A>、<xref:System.Drawing.Graphics.DrawString%2A> など\) を呼び出します。  
  
 <xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.DrawRectangle%2A> メソッドを呼び出す例を次に示します。  <xref:System.Drawing.Graphics.DrawRectangle%2A> メソッドに渡される最初の引数は <xref:System.Drawing.Pen> オブジェクトです。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## グラフィックスの状態  
 <xref:System.Drawing.Graphics> オブジェクトは、<xref:System.Drawing.Graphics.DrawLine%2A> や <xref:System.Drawing.Graphics.DrawRectangle%2A> などの描画メソッドを用意するだけではありません。  <xref:System.Drawing.Graphics> オブジェクトは、次のカテゴリに分類されるグラフィックスの状態も維持します。  
  
-   画質の設定  
  
-   変換  
  
-   クリッピング領域  
  
### 画質の設定  
 <xref:System.Drawing.Graphics> オブジェクトには、描画対象となる項目の画質に影響する複数のプロパティがあります。  たとえば、<xref:System.Drawing.Graphics.TextRenderingHint%2A> プロパティには、テキストに適用するアンチエイリアシングの種類を指定できます。  項目の画質に影響するその他のプロパティには、<xref:System.Drawing.Graphics.SmoothingMode%2A>、<xref:System.Drawing.Graphics.CompositingMode%2A>、<xref:System.Drawing.Graphics.CompositingQuality%2A>、および <xref:System.Drawing.Graphics.InterpolationMode%2A> があります。  
  
 2 つの楕円を描画する例を次に示します。一方にはスムージング モードとして <xref:System.Drawing.Drawing2D.SmoothingMode> を設定し、もう一方にはスムージング モードとして <xref:System.Drawing.Drawing2D.SmoothingMode> を設定しています。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### 変換  
 <xref:System.Drawing.Graphics> オブジェクトは 2 種類の変換 \(ワールド変換およびページ変換\) を維持しており、これらの変換がその <xref:System.Drawing.Graphics> オブジェクトが描画するすべての項目に適用されます。  ワールド変換には、任意のアフィン変換を格納できます。  アフィン変換には、スケーリング、回転、反転、傾斜、および平行移動があります。  ページ変換は、スケーリングや単位の変更 \(ピクセルからインチへの変更など\) のために使用できます。  詳細については、「[座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)」を参照してください。  
  
 <xref:System.Drawing.Graphics> オブジェクトのワールド変換およびページ変換を設定する例を次に示します。  ワールド変換として、30°の回転を設定します。  ページ変換は、2 番目の <xref:System.Drawing.Graphics.DrawEllipse%2A> に渡される座標がピクセル単位ではなくミリメートル単位で扱われるように設定されます。  このコードは、<xref:System.Drawing.Graphics.DrawEllipse%2A> メソッドをまったく同じように 2 回呼び出します。  最初の <xref:System.Drawing.Graphics.DrawEllipse%2A> 呼び出しにはワールド変換が適用され、2 回目の <xref:System.Drawing.Graphics.DrawEllipse%2A> 呼び出しには両方の変換 \(ワールド変換およびページ変換\) が適用されます。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 結果として得られる 2 つの楕円を次の図に示します。  30°の回転は、楕円の中心ではなく、座標系の原点 \(クライアント領域の左上隅\) を軸として行われます。  また、ペン幅の 1 とは、最初の楕円では 1 ピクセルを意味し、2 番目の楕円では 1 ミリメートルを意味します。  
  
 ![楕円](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")  
  
### クリッピング領域  
 <xref:System.Drawing.Graphics> オブジェクトは、その <xref:System.Drawing.Graphics> オブジェクトが描画するすべての項目に適用されるクリッピング領域を維持しています。  クリッピング領域を設定するには、<xref:System.Drawing.Graphics.SetClip%2A> メソッドを呼び出します。  
  
 2 つの四角形を交差させることによって十字型の領域を作成する例を次に示します。  この領域が、<xref:System.Drawing.Graphics> オブジェクトのクリッピング領域として指定されます。  次に、このコードは、描画範囲がクリッピング領域の内側に限定された 2 本の直線を描画します。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](../../../../amples/snippets/visualbasic/VS_Snippets_Wpf/ToolBarOrient_snip/visualbasic/toolbargraphics/new.bmp Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 クリップされた直線を次の図に示します。  
  
 ![制限されたクリップ領域](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")  
  
## 参照  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [入れ子になっているグラフィックス コンテナーの使用](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)