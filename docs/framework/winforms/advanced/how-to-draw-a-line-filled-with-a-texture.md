---
title: "方法 :テクスチャを使用して塗りつぶした直線を描画する | Microsoft Docs"
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
  - "描画 (線を), テクスチャ"
  - "描画, 線"
  - "線, テクスチャ"
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 :テクスチャを使用して塗りつぶした直線を描画する
線を純色で描画する代わりに、テクスチャを使用して描画できます。  テクスチャを使用して直線や曲線を描画するには、<xref:System.Drawing.TextureBrush> オブジェクトを作成し、その <xref:System.Drawing.TextureBrush> オブジェクトを <xref:System.Drawing.Pen.%23ctor%2A> コンストラクターに渡します。  テクスチャ ブラシに関連付けられたビットマップが使用され、そのビットマップ平面が見えないように並べられます。ペンが直線または曲線を描画するときに、並べられているテクスチャの特定のピクセルがペンのストロークに沿って表示されるようになります。  
  
## 使用例  
 ファイル  `Texture1.jpg` から <xref:System.Drawing.Bitmap> オブジェクトを作成する例を次に示します。  そのビットマップを使用して <xref:System.Drawing.TextureBrush> オブジェクトを作成し、その <xref:System.Drawing.TextureBrush> オブジェクトを使用して <xref:System.Drawing.Pen> オブジェクトを作成しています。  <xref:System.Drawing.Graphics.DrawImage%2A> を呼び出すと、左上隅が \(0, 0\) の位置にあるビットマップが描画されます。  <xref:System.Drawing.Graphics.DrawEllipse%2A> の呼び出しでは、<xref:System.Drawing.Pen> オブジェクトを使用して、テクスチャを適用した楕円を描画しています。  
  
 ビットマップと、テクスチャが適用された楕円を次の図に示します。  
  
 ![ペン](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## コードのコンパイル  
 Windows フォームを作成し、フォームの <xref:System.Windows.Forms.Control.Paint> イベントを処理します。  前述のコードを <xref:System.Windows.Forms.Control.Paint> イベント ハンドラーに貼り付けます。   `Texture.jpg` を、システムで有効なイメージで置き換えます。  
  
## 参照  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)