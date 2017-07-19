---
title: "GDI+ でのイメージの描画、配置、およびクローン作成 | Microsoft Docs"
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
  - "描画, イメージ"
  - "描画, ラスター イメージ"
  - "GDI+, クローン作成 (イメージの)"
  - "GDI+, 描画 (イメージを)"
  - "GDI+, 配置 (イメージを)"
  - "イメージ [Windows フォーム], クローンの作成"
  - "イメージ [Windows フォーム], 描画"
  - "イメージ [Windows フォーム], 配置"
  - "ラスター イメージ"
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# GDI+ でのイメージの描画、配置、およびクローン作成
<xref:System.Drawing.Bitmap> クラスを使用して、ラスター イメージを読み込んだり表示したりできます。また、<xref:System.Drawing.Imaging.Metafile> クラスを使用して、ベクター イメージを読み込んだり表示したりできます。  <xref:System.Drawing.Bitmap> クラスおよび <xref:System.Drawing.Imaging.Metafile> クラスは、<xref:System.Drawing.Image> クラスを継承します。  ベクター イメージを表示するには、<xref:System.Drawing.Graphics> クラスのインスタンスと <xref:System.Drawing.Imaging.Metafile> が必要です。  ラスター イメージを表示するには、<xref:System.Drawing.Graphics> クラスのインスタンスと <xref:System.Drawing.Bitmap> が必要です。  <xref:System.Drawing.Graphics> クラスのインスタンスには、<xref:System.Drawing.Imaging.Metafile> または <xref:System.Drawing.Bitmap> を引数として受け取る <xref:System.Drawing.Graphics.DrawImage%2A> メソッドが用意されています。  
  
## ファイルの種類とクローン作成  
 ファイル Climber.jpg から <xref:System.Drawing.Bitmap> を構築し、ビットマップを表示するコード例を次に示します。  イメージの左上隅を配置する点 \(10, 10\) は、2 番目と 3 番目のパラメーターで指定されます。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 このイメージを次の図に示します。  
  
 ![イメージ サンプル](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.png "AboutGdip03\_Art04")  
  
 BMP、GIF、JPEG、EXIF、PNG、TIFF、ICON などさまざまなグラフィックス ファイル形式から <xref:System.Drawing.Bitmap> オブジェクトを構築できます。  
  
 さまざまな種類のファイルから <xref:System.Drawing.Bitmap> オブジェクトを構築し、ビットマップを表示するコード例を次に示します。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap> クラスには、既存の <xref:System.Drawing.Bitmap> のコピーを作成するために使用できる <xref:System.Drawing.Bitmap.Clone%2A> メソッドが用意されています。  <xref:System.Drawing.Bitmap.Clone%2A> メソッドには、コピー元のビットマップでコピーする部分を指定するために使用できる四角形パラメーターがあります。  既存の <xref:System.Drawing.Bitmap> の上半分のクローンを作成して <xref:System.Drawing.Bitmap> を作成するコード例を次に示します。  次に、両方のイメージを描画します。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 2 つのイメージを次の図に示します。  
  
 ![トリミング](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.png "AboutGdip03\_Art05")  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)