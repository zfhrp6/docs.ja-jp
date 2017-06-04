---
title: "方法 : 四角形内にテキストを折り返して描画する | Microsoft Docs"
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
  - "文字列 [Windows フォーム], 描画 (四角形の中に)"
  - "テキスト [Windows フォーム], 描画 (四角形の中に)"
  - "Windows フォーム, 描画 (テキストを四角形の中に)"
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 四角形内にテキストを折り返して描画する
<xref:System.Drawing.Graphics> クラスのオーバーロードされた <xref:System.Drawing.Graphics.DrawString%2A> メソッドに <xref:System.Drawing.Rectangle> パラメーターまたは <xref:System.Drawing.RectangleF> パラメーターを渡して呼び出すと、四角形内にテキストを折り返して描画できます。  このとき、<xref:System.Drawing.Brush> と <xref:System.Drawing.Font> も使用します。  
  
 または、<xref:System.Windows.Forms.TextRenderer> のオーバーロードされた <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドに <xref:System.Drawing.Rectangle> パラメーターと <xref:System.Windows.Forms.TextFormatFlags> パラメーターを渡して呼び出しても、四角形内にテキストを折り返して描画できます。  このとき、<xref:System.Drawing.Color> と <xref:System.Drawing.Font> も使用します。  
  
 <xref:System.Drawing.Graphics.DrawString%2A> メソッドを使用して、四角形内にテキストを描画すると、次のように出力されます。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")  
  
### GDI\+ を使用して、テキストを四角形内に折り返して描画するには  
  
1.  オーバーロードされた <xref:System.Drawing.Graphics.DrawString%2A> メソッドに描画するテキスト、<xref:System.Drawing.Rectangle> \(または <xref:System.Drawing.RectangleF>\)、<xref:System.Drawing.Font> および <xref:System.Drawing.Brush> を渡して使用します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### GDI を使用して、テキストを四角形内に描画するには  
  
1.  <xref:System.Windows.Forms.TextFormatFlags> 列挙値を使用し、オーバーロードされた <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドに描画するテキスト、<xref:System.Drawing.Rectangle>、<xref:System.Drawing.Font>、および <xref:System.Drawing.Color> を渡して、テキストを折り返すことを指定します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## コードのコンパイル  
 上記の例では、次のものが必要です。  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`。これは、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターです。  
  
## 参照  
 [方法 : GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)   
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [方法 : フォント ファミリとフォントを作成する](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)   
 [方法 : テキストを指定の位置に描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)