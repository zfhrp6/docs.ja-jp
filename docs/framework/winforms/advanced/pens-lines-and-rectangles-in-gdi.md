---
title: "GDI+ でのペン、直線、および四角形 | Microsoft Docs"
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
  - "描画, 線"
  - "描画, 四角形"
  - "例 [Windows フォーム], 描画 (線と形状を)"
  - "例 [Windows フォーム], GDI+"
  - "例 [Windows フォーム], ペン"
  - "GDI+, 線"
  - "GDI+, ペン"
  - "GDI+, 四角形"
  - "線"
  - "線, 破線"
  - "四角形"
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# GDI+ でのペン、直線、および四角形
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] で直線を描画するには、<xref:System.Drawing.Graphics> オブジェクトと <xref:System.Drawing.Pen> オブジェクトを作成する必要があります。  <xref:System.Drawing.Graphics> オブジェクトは実際に描画を実行するメソッドを提供し、<xref:System.Drawing.Pen> オブジェクトは線の色、幅、スタイルなどの属性を格納します。  
  
## 直線の描画  
 直線を描画するには、<xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.DrawLine%2A> メソッドを呼び出します。  <xref:System.Drawing.Pen> オブジェクトは、引数の 1 つとして <xref:System.Drawing.Graphics.DrawLine%2A> メソッドに渡されます。  点 \(4, 2\) から点 \(12, 6\) までの直線を描画する例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> は <xref:System.Drawing.Graphics> クラスのオーバーロードされたメソッドであるため、いくつかの方法でこのメソッドの引数を指定できます。  たとえば、2 つの <xref:System.Drawing.Point> オブジェクトを構築して、その <xref:System.Drawing.Point> オブジェクトを引数として <xref:System.Drawing.Graphics.DrawLine%2A> メソッドに渡すことができます。  
  
 [!code-csharp[LinesCurvesAndShapes#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## ペンの構築  
 <xref:System.Drawing.Pen> オブジェクトを構築するときに、所定の属性を指定できます。  たとえば、ある `Pen` コンストラクターでは色と幅を指定できます。  \(0, 0\) から \(60, 30\) まで幅 2 の青い直線を描画する例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## 破線とライン キャップ  
 <xref:System.Drawing.Pen> オブジェクトは、線の特性を指定するために使用できる <xref:System.Drawing.Pen.DashStyle%2A> などのプロパティも公開します。  \(100, 50\) から \(300, 80\) まで破線を描画する例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#44](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 <xref:System.Drawing.Pen> オブジェクトのプロパティを使用して、線の属性をさらに指定できます。  <xref:System.Drawing.Pen.StartCap%2A> プロパティと <xref:System.Drawing.Pen.EndCap%2A> プロパティは、直線のエンドポイントの外観を指定します。エンドポイントの外観として、フラット、直角、丸、三角、またはカスタム図形を指定できます。  <xref:System.Drawing.Pen.LineJoin%2A> プロパティでは、連結した直線の処理として、留め継ぎ \(角を丸めずに接合\)、面取り、丸め、またはクリッピングを指定できます。  さまざまなキャップ スタイルと接合スタイルを持つ直線を次の図に示します。  
  
 ![線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.png "Aboutgdip02\_art04")  
  
## 四角形の描画  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用した四角形の描画は、直線の描画に似ています。  四角形を描画するには、<xref:System.Drawing.Graphics> オブジェクトと <xref:System.Drawing.Pen> オブジェクトが必要です。  <xref:System.Drawing.Graphics> オブジェクトは <xref:System.Drawing.Graphics.DrawRectangle%2A> メソッドを提供し、<xref:System.Drawing.Pen> オブジェクトは線の幅やなどの属性を格納します。  <xref:System.Drawing.Pen> オブジェクトは、引数の 1 つとして <xref:System.Drawing.Graphics.DrawRectangle%2A> メソッドに渡されます。  左上隅 \(100, 50\)、幅 80、高さ 40 の四角形を描画する例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#45](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> は <xref:System.Drawing.Graphics> クラスのオーバーロードされたメソッドであるため、いくつかの方法でこのメソッドの引数を指定できます。  たとえば、<xref:System.Drawing.Rectangle> オブジェクトを構築して、その <xref:System.Drawing.Rectangle> オブジェクトを引数として <xref:System.Drawing.Graphics.DrawRectangle%2A> メソッドに渡すことができます。  
  
 [!code-csharp[LinesCurvesAndShapes#46](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 <xref:System.Drawing.Rectangle> オブジェクトには、四角形についての情報を操作および収集するためのメソッドとプロパティがあります。  たとえば、<xref:System.Drawing.Rectangle.Inflate%2A> メソッドと <xref:System.Drawing.Rectangle.Offset%2A> メソッドは、四角形のサイズと位置を変更します。  <xref:System.Drawing.Rectangle.IntersectsWith%2A> メソッドは、四角形が指定した別の四角形と重なる部分を持つかどうかを示します。<xref:System.Drawing.Rectangle.Contains%2A> メソッドは、指定した点が四角形の内部にあるかどうかを示します。  
  
## 参照  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 <xref:System.Drawing.Rectangle?displayProperty=fullName>   
 [方法 : ペンを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)   
 [方法 : Windows フォームに直線を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)   
 [方法 : 形状のアウトラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)