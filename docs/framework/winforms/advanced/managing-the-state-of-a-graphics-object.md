---
title: Graphics オブジェクトの状態の管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: b81c3c8b25f13ac5791b5d2116b8536575f9ebcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525120"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Graphics オブジェクトの状態の管理
<xref:System.Drawing.Graphics>クラスは、の中核は[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]します。 取得するものを描画するには<xref:System.Drawing.Graphics>オブジェクト、そのプロパティを設定し、そのメソッドを呼び出す<xref:System.Drawing.Graphics.DrawLine%2A>、 <xref:System.Drawing.Graphics.DrawImage%2A>、<xref:System.Drawing.Graphics.DrawString%2A>など)。  
  
 次の例では、<xref:System.Drawing.Graphics.DrawRectangle%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。 渡される最初の引数、<xref:System.Drawing.Graphics.DrawRectangle%2A>メソッドは、<xref:System.Drawing.Pen>オブジェクト。  
  
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
  
## <a name="graphics-state"></a>グラフィックスの状態  
 A<xref:System.Drawing.Graphics>オブジェクトが描画のメソッドをなど提供以上<xref:System.Drawing.Graphics.DrawLine%2A>と<xref:System.Drawing.Graphics.DrawRectangle%2A>です。 A<xref:System.Drawing.Graphics>オブジェクトは、グラフィックスの状態は、次のカテゴリに分類できますをも保持します。  
  
-   品質の設定  
  
-   変換  
  
-   クリッピング領域  
  
### <a name="quality-settings"></a>品質の設定  
 A<xref:System.Drawing.Graphics>オブジェクトが描画されるアイテムの品質に影響を与えるいくつかのプロパティです。 たとえば、設定、<xref:System.Drawing.Graphics.TextRenderingHint%2A>テキストに適用されます (存在する場合) のアンチエイリアシングの種類を指定するプロパティです。 品質に影響を与える他のプロパティは<xref:System.Drawing.Graphics.SmoothingMode%2A>、 <xref:System.Drawing.Graphics.CompositingMode%2A>、 <xref:System.Drawing.Graphics.CompositingQuality%2A>、および<xref:System.Drawing.Graphics.InterpolationMode%2A>です。  
  
 次の例は、スムージング モードを設定 1 つ、2 つの楕円を描画<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>、スムージング モードを設定 1 つと<xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
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
  
### <a name="transformations"></a>変換  
 A<xref:System.Drawing.Graphics>オブジェクトを保持するによって描画されたすべての項目に適用される 2 つの変換 (世界と ページ)<xref:System.Drawing.Graphics>オブジェクト。 ワールド変換には、任意のアフィン変換を格納することができます。 アフィン変換には、拡大/縮小、回転、反転、傾斜、および翻訳が含まれます。 スケーリングの単位 (たとえば、インチをピクセル単位) を変更して、ページの変換を使用できます。 詳細については、次を参照してください。[座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)です。  
  
 次の例は、ワールド変換とページ変換の<xref:System.Drawing.Graphics>オブジェクト。 ワールド変換は、30 度回転に設定されます。 ページ変換を設定すると、座標は、2 番目に渡されるように<xref:System.Drawing.Graphics.DrawEllipse%2A>はピクセル単位ではなくミリメートル単位として扱われます。 同じ 2 つの呼び出しは、コードは、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッドです。 ワールド変換は、最初に適用<xref:System.Drawing.Graphics.DrawEllipse%2A>呼び出し、および両方の変換 (世界と ページ)、2 番目に適用されます<xref:System.Drawing.Graphics.DrawEllipse%2A>呼び出します。  
  
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
  
 次の図は、次の 2 つの省略記号ボタンを示します。 30 ° 回転が (クライアント領域の左上隅) 座標系の原点を基点、省略記号の中心でないことに注意してください。 1 のペンの幅が 2 番目の楕円の最初の楕円および 1 ミリメートル 1 ピクセルを意味にも注意してください。  
  
 ![楕円](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")  
  
### <a name="clipping-region"></a>クリッピング領域  
 A<xref:System.Drawing.Graphics>オブジェクトを保持するによって描画されたすべてのアイテムに適用されるクリッピング領域<xref:System.Drawing.Graphics>オブジェクト。 クリッピング領域を設定するには呼び出すことによって、<xref:System.Drawing.Graphics.SetClip%2A>メソッドです。  
  
 次の例では、2 つの四角形の和集合を形成する、十字型の領域を作成します。 クリッピング領域としてその地域が指定されている、<xref:System.Drawing.Graphics>オブジェクト。 コードは、クリッピング領域の内部に制限されている 2 つの線を描画します。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
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
  
 次の図は、クリップされた行を示します。  
  
 ![クリップ領域を制限](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")  
  
## <a name="see-also"></a>関連項目  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [入れ子になっているグラフィックス コンテナーの使用](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)
