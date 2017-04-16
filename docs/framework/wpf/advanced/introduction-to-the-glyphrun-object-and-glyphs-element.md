---
title: "GlyphRun オブジェクトと Glyphs 要素の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字体裁、Glyphs 要素"
  - "Glyphs 要素"
  - "GlyphRun オブジェクト"
  - "テキスト、グリフ"
  - "グリフ [WPF]"
  - "文字体裁、GlyphRun オブジェクト"
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# GlyphRun オブジェクトと Glyphs 要素の概要
このトピックの説明、 <xref:System.Windows.Media.GlyphRun>オブジェクトおよび<xref:System.Windows.Documents.Glyphs>要素。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>GlyphRun の概要  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]では、高度なテキストに直接アクセスできるグリフ レベルのマークアップを含む<xref:System.Windows.Documents.Glyphs>を途中受信してテキストの書式設定後は保持しお客様にします。 これらの機能要件を指定する重要なサポート、別のテキストのレンダリングの各シナリオを次にします。  
  
1.  固定形式のドキュメントの画面表示されます。  
  
2.  シナリオを印刷します。  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]デバイスのプリンター言語です。  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]。  
  
    -   出力元の以前のプリンター ドライバー[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]固定形式のアプリケーションです。  
  
    -   印刷スプール形式です。  
  
3.  固定形式のドキュメントの表示、以前のバージョンのクライアントを含む[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]やその他のコンピューティング デバイスです。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs>と<xref:System.Windows.Media.GlyphRun>固定形式のドキュメントの表示と印刷のシナリオ用に設計されています。                      [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]いくつかの要素は、一般的なレイアウトと[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]などのシナリオ<xref:System.Windows.Controls.Label>と<xref:System.Windows.Controls.TextBlock>します。 レイアウトについての詳細と[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]シナリオを参照して、 [WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)します。  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>GlyphRun オブジェクト  
 <xref:System.Windows.Media.GlyphRun>オブジェクトは、1 つのサイズに&1; つの描画スタイルで、1 つのフォントの書体のグリフのシーケンスを表します。  
  
 <xref:System.Windows.Media.GlyphRun>グリフ両方フォント詳細が含まれます<xref:System.Windows.Documents.Glyphs.Indices%2A>と個々 のグリフの位置。 元も含まれています。[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]コード ポイントの文字のグリフのバッファー オフセット マッピングの情報、および文字単位とグリフのフラグから生成された実行します。  
  
 <xref:System.Windows.Media.GlyphRun>高レベルに対応しています<xref:System.Windows.FrameworkElement>、<xref:System.Windows.Documents.Glyphs>します。                  <xref:System.Windows.Documents.Glyphs>要素ツリーを使用できます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を表すマークアップ<xref:System.Windows.Media.GlyphRun>出力します。  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Glyphs 要素  
 <xref:System.Windows.Documents.Glyphs>要素の出力を表す、 <xref:System.Windows.Media.GlyphRun>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 次のマークアップ構文を説明するため、<xref:System.Windows.Documents.Glyphs>要素。  
  
 [!code-xml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 次のプロパティの定義は、サンプルのマークアップ内の最初の&4; つの属性に対応します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|リソース識別子を指定します。 ファイル名を Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]、またはアプリケーションの .exe またはコンテナー リソース参照します。|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|描画サーフェイスの単位 (既定値は.96 インチ) では、フォント サイズを指定します。|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|太字や斜体のスタイルのフラグを指定します。|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|双方向のレイアウトのレベルを指定します。 偶数ゼロの値が左から右のレイアウトを示すもので、奇数の値は、右から左のレイアウトを意味します。|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>インデックスのプロパティ  
 <xref:System.Windows.Documents.Glyphs.Indices%2A>プロパティは、グリフの仕様の文字列です。 一連のグリフは、1 つのクラスターを形成、クラスター内の最初のグリフの仕様は、グリフの数の仕様とコード ポイントの数は、クラスターを形成する結合によって前します。 <xref:System.Windows.Documents.Glyphs.Indices%2A>プロパティでは、次のプロパティを&1; つの文字列内に収集します。  
  
-   グリフのインデックス  
  
-   グリフのアドバンス幅  
  
-   グリフの添付ファイルのベクトルを組み合わせる  
  
-   コード ポイントからグリフへのクラスターのマッピング  
  
-   グリフ フラグ  
  
 それぞれのグリフの仕様では、次の形式があります。  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>グリフのメトリック  
 各グリフ指定は、その他のメトリックを定義する<xref:System.Windows.Documents.Glyphs>します。 次の図では、2 文字の種類のグリフの印刷用のさまざまな特性を定義します。  
  
 ![グリフ単位のダイアグラム](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>グリフのマークアップ  
 次のコード例のさまざまなプロパティを使用する方法を示しています、<xref:System.Windows.Documents.Glyphs>内の要素[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
 [!code-xml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>関連項目  
 [WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [テキスト](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)