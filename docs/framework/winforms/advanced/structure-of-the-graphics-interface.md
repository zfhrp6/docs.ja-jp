---
title: "グラフィックス インターフェイスの構造体 | Microsoft Docs"
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
  - "GDI+, 使用 (マネージ インターフェイスを)"
  - "グラフィックス, クラス構造"
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# グラフィックス インターフェイスの構造体
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] に対するマネージ クラス インターフェイスには、60 個のクラス、50 個の列挙体、および 8 個の構造体が含まれます。  <xref:System.Drawing.Graphics> クラスは、直線、曲線、図形、イメージ、およびテキストを実際に描画するクラスであり、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 機能の中核としての役割を果たします。  
  
## 重要なクラス  
 多くのクラスが、この <xref:System.Drawing.Graphics> クラスと連動して機能します。  たとえば、<xref:System.Drawing.Graphics.DrawLine%2A> メソッドは、描画される線の属性 \(色、幅、破線スタイルなど\) を保持する <xref:System.Drawing.Pen> オブジェクトを受け取ります。  <xref:System.Drawing.Graphics.FillRectangle%2A> メソッドは <xref:System.Drawing.Drawing2D.LinearGradientBrush> オブジェクトへのポインターを受け取る場合がありますが、このオブジェクトは <xref:System.Drawing.Graphics> オブジェクトと連動し、グラデーション カラーで四角形を塗りつぶします。  <xref:System.Drawing.Font> オブジェクトと <xref:System.Drawing.StringFormat> オブジェクトは、<xref:System.Drawing.Graphics> オブジェクトによるテキストの描画方法を制御します。  <xref:System.Drawing.Drawing2D.Matrix> オブジェクトは、イメージの回転、スケーリング、および反転に使用される、<xref:System.Drawing.Graphics> オブジェクトのワールド変換を操作および格納します。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、グラフィックス データを編成するための構造体 \(<xref:System.Drawing.Rectangle>、<xref:System.Drawing.Point>、<xref:System.Drawing.Size> など\) もいくつか提供します。  また、構造化データ型として主に機能するクラスもあります。  たとえば、<xref:System.Drawing.Imaging.BitmapData> クラスは <xref:System.Drawing.Bitmap> クラスのヘルパーであり、<xref:System.Drawing.Drawing2D.PathData> クラスは <xref:System.Drawing.Drawing2D.GraphicsPath> クラスのヘルパーです。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、関連する複数の定数のコレクションであるいくつかの列挙体を定義します。  たとえば、<xref:System.Drawing.Drawing2D.LineJoin> 列挙体は、2 つの直線を接合するときに使用するスタイルを指定する <xref:System.Drawing.Drawing2D.LineJoin>、<xref:System.Drawing.Drawing2D.LineJoin>、<xref:System.Drawing.Drawing2D.LineJoin> の各要素を格納しています。  
  
## 参照  
 [グラフィックスの概要](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)   
 [GDI\+ マネージ コードについて](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)   
 [マネージ グラフィックス クラスの使用](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)