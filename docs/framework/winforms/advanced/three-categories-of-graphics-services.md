---
title: "グラフィックス サービスの 3 つのカテゴリ | Microsoft Docs"
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
  - "2 次元ベクター グラフィックス"
  - "グラフィックス, カテゴリ"
  - "イメージング"
  - "タイポグラフィ"
  - "ベクター グラフィックス"
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# グラフィックス サービスの 3 つのカテゴリ
Windows フォームでのグラフィックスの提供は、大きく次の 3 つのカテゴリに分けられます。  
  
-   2 次元 \(2\-D\) ベクター グラフィックス  
  
-   イメージング  
  
-   タイポグラフィ  
  
## 2 次元ベクター グラフィックス  
 2 次元のベクター グラフィックスは、座標系内の一連の点で指定されるプリミティブ \(直線、曲線、図形など\) です。  たとえば、直線は 2 つの端点によって指定され、四角形は左上隅の位置を示す点と、幅および高さを定義する数値の組み合わせによって指定されます。  単純なパスは、直線で結ばれる複数の点の配列によって指定されます。  ベジエ スプラインは、4 つの制御点で指定される複雑な曲線です。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、プリミティブ自体の情報を格納するクラスおよび構造体、プリミティブの描画方法についての情報を格納するクラス、および実際に描画を実行するクラスを提供します。  たとえば、<xref:System.Drawing.Rectangle> 構造体には四角形の位置とサイズが格納されます。<xref:System.Drawing.Pen> クラスには、線の色、幅、およびスタイルに関する情報が格納されます。<xref:System.Drawing.Graphics> クラスには、直線、長方形、パス、およびその他の図形を描画するためのメソッドがあります。  また、いくつかの <xref:System.Drawing.Brush> クラスは、閉じられた図形およびパスを色またはパターンで塗りつぶす方法に関する情報を格納します。  
  
 ベクター イメージ \(複数のグラフィックス コマンドから成るシーケンス\) はメタファイルに記録できます。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、メタファイルを記録、表示、および保存するための <xref:System.Drawing.Imaging.Metafile> クラスを提供します。  <xref:System.Drawing.Imaging.MetafileHeader> クラスと <xref:System.Drawing.Imaging.MetaHeader> クラスを使用すると、メタファイル ヘッダーに格納されているデータを調べることができます。  
  
## イメージング  
 ベクター グラフィックスの手法では表示するのが難しい画像や、表示することができない画像もあります。  たとえば、ツール バー ボタンに表示される画像やアイコンとして表示される画像を直線と曲線の集合として指定するのは困難です。  混雑した野球場の高解像度デジタル写真をベクター手法で作成するのはさらに困難です。  このようなイメージは、画面上の各ドットの色を表す数値の配列であるビットマップとして格納されます。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、ビットマップを表示、操作、および保存するための <xref:System.Drawing.Bitmap> クラスを提供します。  
  
## タイポグラフィ  
 タイポグラフィは、さまざまなフォント、サイズ、およびスタイルでテキストを表示する機能です。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] には、この複雑なタスクをサポートするための広範なサポートが用意されています。  たとえば、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] の新機能の 1 つであるサブピクセル アンチエイリアシングを使用すると、LCD 画面上により滑らかな輪郭のテキストを描画できます。  
  
 また、Windows フォームには、<xref:System.Windows.Forms.TextRenderer> クラスで [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 機能を使用してテキストを描画するオプションも用意されています。  
  
## 参照  
 [グラフィックスの概要](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)   
 [GDI\+ マネージ コードについて](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)   
 [マネージ グラフィックス クラスの使用](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)