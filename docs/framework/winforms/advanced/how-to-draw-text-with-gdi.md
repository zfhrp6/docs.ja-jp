---
title: "方法 : GDI を使用してテキストを描画する | Microsoft Docs"
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
  - "描画, テキスト"
  - "GDI, 描画 (テキストを) [Windows フォーム]"
  - "テキスト, 描画 (TextRenderer を使用して)"
  - "Windows フォーム, 描画 (GDI でテキストを)"
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : GDI を使用してテキストを描画する
<xref:System.Windows.Forms.TextRenderer> クラスの <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドを使用すると、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 機能を利用してフォームまたはコントロールにテキストを描画できます。  [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] のテキスト描画機能は、一般に [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] よりもパフォーマンスが高く、テキストの寸法の計測も正確です。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer> クラスの <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドでは、印刷はサポートされていません。  印刷時には常に <xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawString%2A> メソッドを使用してください。  
  
## 使用例  
 次のコード例は、<xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドを使用して、四角形内の複数の行にテキストを描画する方法を示しています。  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <xref:System.Windows.Forms.TextRenderer> クラス内でテキストを描画するには、<xref:System.Drawing.Graphics> や <xref:System.Drawing.Font> などの <xref:System.Drawing.IDeviceContext>、テキストを描画する位置、および描画する色が必要です。  オプションで、<xref:System.Windows.Forms.TextFormatFlags> 列挙値を使ってテキストの書式を指定することも可能です。  
  
 <xref:System.Drawing.Graphics> の取得の詳細については、「[方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)」を参照してください。  <xref:System.Drawing.Font> の構築の詳細については、「[方法 : フォント ファミリとフォントを作成する](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)」を参照してください。  
  
## コードのコンパイル  
 前述のコード例は Windows フォームでの使用を前提としたものであり、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 <xref:System.Windows.Forms.TextRenderer>   
 <xref:System.Drawing.Font>   
 <xref:System.Drawing.Color>   
 <xref:System.Drawing.Color>   
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)