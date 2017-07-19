---
title: "方法 : テキストを指定の位置に描画する | Microsoft Docs"
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
  - "描画 (テキストを)"
  - "描画 (テキストを), 指定された位置 [Windows フォーム]"
  - "テキスト, 描画 (指定された位置に) [Windows フォーム]"
  - "Windows フォーム, 描画 (指定された位置にテキストを)"
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : テキストを指定の位置に描画する
カスタムな描画を実行するとき、1 行のテキストを指定した位置から水平に描画できます。  <xref:System.Drawing.Graphics> クラスのオーバーロードされた <xref:System.Drawing.Graphics.DrawString%2A> メソッドに <xref:System.Drawing.Point> パラメーターまたは <xref:System.Drawing.PointF> パラメーターを渡して呼び出すと、この方法でテキストを描画できます。  <xref:System.Drawing.Graphics.DrawString%2A> メソッドには、<xref:System.Drawing.Brush> および <xref:System.Drawing.Font> も必要です。  
  
 また、<xref:System.Drawing.Point> を使用する <xref:System.Windows.Forms.TextRenderer> のオーバーロードされた <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドも使用できます。  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> には、<xref:System.Drawing.Color> および <xref:System.Drawing.Font> も必要です。  
  
 オーバーロードされた <xref:System.Drawing.Graphics.DrawString%2A> メソッドを使用するとき、指定した位置にテキストを描画すると、次のように出力されます。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")  
  
### GDI\+ を使用してテキスト行を描画するには  
  
1.  <xref:System.Drawing.Graphics.DrawString%2A> メソッドに描画するテキスト、<xref:System.Drawing.Point> \(または <xref:System.Drawing.PointF>\)、<xref:System.Drawing.Font> および <xref:System.Drawing.Brush> を渡して使用します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### GDI を使用してテキスト行を描画するには  
  
1.  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドに描画するテキスト、<xref:System.Drawing.Point>、<xref:System.Drawing.Font>、および <xref:System.Drawing.Color> を渡して使用します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## コードのコンパイル  
 上記の例では、次のものが必要です。  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`。これは、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターです。  
  
## 参照  
 [方法 : GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)   
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [方法 : フォント ファミリとフォントを作成する](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)   
 [方法 : 四角形内にテキストを折り返して描画する](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)