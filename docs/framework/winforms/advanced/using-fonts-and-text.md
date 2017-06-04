---
title: "フォントとテキストの使用 | Microsoft Docs"
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
  - "例 [Windows フォーム], フォントとテキスト"
  - "フォント, 使用 (Windows フォームで)"
  - "GDI, 描画 (テキストを) [Windows フォーム]"
  - "文字列 [Windows フォーム], 描画 (Windows フォームで)"
  - "テキスト [Windows フォーム], 描画 (Windows フォームで)"
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# フォントとテキストの使用
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] と [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] には、Windows フォームでテキストを描画するためのクラスがいくつか用意されています。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] の <xref:System.Drawing.Graphics> クラスにはいくつかの <xref:System.Drawing.Graphics.DrawString%2A> メソッドがあり、これらのメソッドを使用して、テキストの位置、外接する四角形、フォント、書式などのさまざまな特徴を指定できます。  また、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] では `TextRenderer` クラスの <xref:System.Windows.Forms.TextRenderer.DrawText%2A> と <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> の静的メソッドを使用して、テキストの描画と寸法計測ができます。  [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] のメソッドを使用して、位置、フォント、および書式を指定することも可能です。  テキストの描画には [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] または [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を選択できますが、一般に [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] の方がパフォーマンスが高く、テキストの寸法計測も正確です。  この他にも、テキストの描画には `FontFamily`、`Font`、<xref:System.Drawing.StringFormat>、および `TextFormatFlags` などが使用されます。  
  
## このセクションの内容  
 [方法 : フォント ファミリとフォントを作成する](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 `Font` オブジェクトと `FontFamily` オブジェクトの作成方法について説明します。  
  
 [方法 : テキストを指定の位置に描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] と [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] を使用して、テキストを特定の位置に描画する方法について説明します。  
  
 [方法 : 四角形内にテキストを折り返して描画する](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] と [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] を使用して、テキストを四角形内に描画する方法について説明します。  
  
 [方法 : GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] によるテキストの描画方法について説明します。  
  
 [方法 : 描画テキストを配置する](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] と [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] でのテキストの書式設定の方法について説明します。  
  
 [方法 : 垂直方向のテキストを作成する](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] でテキストを垂直方向に配置して描画する方法について説明します。  
  
 [方法 : 描画されたテキストにタブ ストップを設定する](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] で、テキストにタブ ストップを設定して描画する方法について説明します。  
  
 [方法 : インストールされているフォントを列挙する](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 インストール済みのフォントの名前を一覧表示する方法について説明します。  
  
 [方法 : プライベート フォント コレクションを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 <xref:System.Drawing.Text.PrivateFontCollection> オブジェクトの作成方法について説明します。  
  
 [方法 : フォント メトリックを取得する](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 セルのアセントやディセントなどのフォント メトリックを取得する方法について説明します。  
  
 [方法 : テキストでのアンチエイリアシングの使用](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 テキストの描画にアンチエイリアシングを使用する方法について説明します。  
  
## 関連項目  
 <xref:System.Drawing.Font>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Drawing.FontFamily>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.TextRenderer>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。