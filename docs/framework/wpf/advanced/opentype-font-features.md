---
title: "OpenType フォントの機能 | Microsoft Docs"
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
  - "OpenType フォント"
  - "文字体裁、OpenType フォント テクノロジ"
  - "OpenType フォント テクノロジ"
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
caps.latest.revision: 38
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 37
---
# OpenType フォントの機能
このトピックのいくつかの主な機能の概要を示します[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]でフォント技術[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。  
  
   
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType フォントの書式  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントの書式はの拡張機能、[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]フォントの書式、PostScript フォント データに対するサポートを追加します。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントの書式が共同で開発された[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]および Adobe Corporation します。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントおよびオペレーティング システム サービスのどのサポート[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]、フォントが含まれているかどうかのフォントがインストールして、フォントを使用する簡単な方法をユーザーに提供[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)]アウトライン] または [CFF (PostScript) について説明します。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントの書式の次の開発者の課題に対処します。  
  
-   広範なマルチプラット フォームのサポート。  
  
-   国際文字セットのサポートが強化されます。  
  
-   フォント データを保護します。  
  
-   フォントの分布をより効率的にファイルのサイズを小さくします。  
  
-   高度なテキスト編集コントロールを幅広くサポートします。  
  
> [!NOTE]
>  Windows SDK には、サンプルのセットが含まれています。[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]で使用できるフォント[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションです。 これらのフォントは、このトピックの残りの部分で説明する機能のほとんどを提供します。 詳細については、次を参照してください。[サンプル OpenType フォント パック](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)します。  
  
 参照してください、 [OpenType 仕様](http://go.microsoft.com/fwlink/?LinkId=96731)の詳細については、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントの書式。  
  
### <a name="advanced-typographic-extensions"></a>高度な印刷用の拡張機能  
 高度な印刷用のテーブル ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]レイアウト テーブル) いずれかを使用するフォントの機能を拡張[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)]または CFF について説明します。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]レイアウトのフォントには、高品質の国際文字体裁をサポートするために、フォントの機能を拡張する追加の情報が含まれます。 ほとんど[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォント全体のサブセットのみを公開する[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]利用可能な機能です。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントは、次の機能を提供します。  
  
-   文字と合字、位置指定のフォーム、修正候補一覧, およびその他のフォント代替表をサポートするグリフの間の充実したマッピング。  
  
-   2 次元配置とグリフの結合をサポートします。  
  
-   明示的なスクリプトと言語の情報、フォントに含まれているため、テキスト処理アプリケーションでは、その動作を必要に応じて調整できます。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]レイアウト テーブルがで詳しく説明されている、 [「フォント ファイル テーブル」](http://www.microsoft.com/typography/otspec/otff.htm)のセクションで、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]仕様です。  
  
 この概要の残りの部分では、幅と、視覚的に対象のいくつかの柔軟性が導入されています[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]のプロパティによって公開されている機能、<xref:System.Windows.Documents.Typography>オブジェクトです。 このオブジェクトの詳細については、次を参照してください。[文字体裁クラス](#typography_class)します。  
  
<a name="variants"></a>   
## <a name="variants"></a>バリアント  
 バリアントを使用して、上付き文字と下付きなどのさまざまなタイポグラフィ スタイルを表示します。  
  
### <a name="superscripts-and-subscripts"></a>上付き/下付きの文字  
 <xref:System.Windows.Documents.Typography.Variants%2A>プロパティでは、上付き文字と下付き文字の値を設定することができます、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォント。  
  
 次のテキストは、Palatino Linotype フォントの上付き文字を表示します。  
  
 ![OpenType の上付き文字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont14.png "opentypefont14")  
OpenType の上付き文字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの上付き文字を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 次のテキストには、Palatino Linotype フォントの添字が表示されます。  
  
 ![OpenType の下付き文字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont15.png "opentypefont15")  
OpenType の下付き文字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの添字を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>上付き文字と下付き文字の装飾的な用途には  
 混在したテキストの装飾的な効果を作成するのに、上付き文字と下付きを使用することもできます。 次のテキストは、Palatino Linotype フォントの上付き文字と下付き文字のテキストを表示します。 大文字の影響がないことに注意してください。  
  
 ![OpenType の上付き文字と下付き文字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont16.png "opentypefont16")  
OpenType の上付き文字と下付き文字を使用するテキスト  
  
 次のマークアップの例は、上付き文字と下付きのプロパティを使用するフォントを定義する方法を示します、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>大文字  
 大文字に変換は、大文字のスタイルのグリフのテキストをレンダリングする文字体裁のフォームのセットです。 通常、テキストがすべて大文字で表示されると、文字間隔が表示されますあまりにも堅く太さと決して大きな文字の比率。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]小文字に変換する小型英大文字を含め、超小型英大文字、タイトル、および大文字スペーシングのさまざまなスタイルの形式をサポートしています。 これらのスタイル形式を使用して、英大文字の外観を制御できます。  
  
 次のテキストには、「小型英大文字」と"AllSmallCaps"スタイルを指定の文字の後に、Pescadero フォントの標準の大文字が表示されます。 この場合は、同じフォント サイズは、次の&3; つすべての単語です。  
  
 ![OpenType の大文字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont11.png "opentypefont11")  
OpenType の大文字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pescadero フォントの大文字に変換を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。 「小型英大文字」形式を使用する場合は、先頭の大文字は無視されます。  
  
 [!code-xml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>タイトル用大文字  
 タイトル用大文字は、重みと縦横比に明るくおよび通常の大文字より洗練された外観を指定する設計です。 通常、タイトル用大文字は見出しとして大きなフォント サイズで使用されます。 次のテキストを表示 Pescadero フォントの標準およびタイトル用大文字に変換します。 2 番目の行のテキストの幅の狭い縦線の幅を確認します。  
  
 ![OpenType のタイトル大文字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont20.png "OpenTypeFont20")  
OpenType のタイトル大文字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pescadero フォントのタイトル用大文字を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>大文字スペーシング  
 大文字間隔は、テキストをすべて大文字を使用する場合は、間隔を設けることができるようにする機能です。 通常、英大文字は小文字とブレンドする設計されます。 間で魅力的な間隔を表示し、大文字と小文字をあまりにも堅く見えますすべて大文字を使用するとします。 次のテキストには、Pescadero フォントの標準と資本の間隔が表示されます。  
  
 ![OpenType の大文字スペーシングを使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont21.png "OpenTypeFont21")  
OpenType の大文字スペーシングを使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pescadero フォントの大文字スペーシングを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>合字  
 合字とは、1 つのグリフを形成し、読み取り可能または魅力的なテキストを作成するために&2; つまたは複数の字形です。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントは、合字の&4; つの種類をサポートします。  
  
-   **標準合字**します。 読みやすさを高めるよう設計。 標準合字には、"fi"、"fl"および"ff"が含まれます。  
  
-   **コンテキスト合字**します。 合字を構成する文字の間の結合の動作を提供することによって、読みやすさを高めるよう設計。  
  
-   **随意合字**します。 装飾、読みやすくするために設計されたされるようにするために設計されています。  
  
-   **歴史的合字**します。 履歴、読みやすくするために設計されたされるようにするために設計されています。  
  
 次のテキストには、Pericles フォントの標準合字のグリフが表示されます。  
  
 ![OpenType の標準合字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont04.png "opentypefont04")  
OpenType の標準合字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pericles フォントの標準合字のグリフを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 次のテキストには、Pericles フォントの随意合字のグリフが表示されます。  
  
 ![OpenType の随意合字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont05.png "opentypefont05")  
OpenType の随意合字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pericles フォントの随意合字のグリフを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 既定では、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]で複数のフォント[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]標準合字を有効にします。 たとえば、Palatino Linotype フォントを使用する場合の標準合字"fi"、"ff"および"fl"として表示されます、組み合わせ文字のグリフ。 各標準合字の文字のペアが互いに接触することに注意してください。  
  
 ![OpenType の標準合字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont06.png "opentypefont06")  
OpenType の標準合字を使用するテキスト  
  
 ただし、"ff"などの標準合字は、結合された文字のグリフではなくとして&2; つの別個のグリフが表示されるように、標準合字機能が無効にできます。  
  
 ![OpenType の標準合字のテキストを使用して無効になっています](../../../../docs/framework/wpf/advanced/media/opentypefont07.png "opentypefont07")  
OpenType の無効な標準合字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの標準合字のグリフを無効にする方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>巻き髭  
 巻き髭は、多くの場合、カリグラフィに関連付けられている手の込んだ装飾を使用して装飾的なグリフです。 次のテキストには、標準グリフと飾り付きグリフ Pescadero フォントが表示されます。  
  
 ![OpenType の標準と飾り付きグリフを使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont08.png "opentypefont08")  
OpenType の標準グリフと飾り付きグリフを使用するテキスト  
  
 巻き髭は、イベントのお知らせなどの短い語句で装飾的な要素としてよく使用されます。 次のテキストでは、巻き髭を使用して、イベントの名前の大文字を強調します。  
  
 ![OpenType の巻き髭を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont09.png "opentypefont09")  
OpenType の巻き髭を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、フォントの巻き髭を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>コンテキスト巻き髭  
 スワッシュ グリフの特定の組み合わせには、隣接する文字の重なり合ったディセンダーなどの魅力的ではありません外観可能性があります。 コンテキスト飾り付きを使用するには、優れた外観を生成する代替飾り付きグリフを使用することができます。 次のテキストは前に、とコンテキストの飾り付きの適用後に、同じ単語を示します。  
  
 ![OpenType のコンテキスト巻き髭を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont19.png "OpenTypeFont19")  
OpenType のコンテキスト巻き髭を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pescadero フォントのコンテキストの飾り付きを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>代替  
 代替文字は、標準的なグリフの代わりに使用できますです。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]次の例で使用される Pericles フォントなどのフォントは、異なる外観のテキストを作成に使用できる代替グリフを含めることができます。 次のテキストには、Pericles フォントの標準グリフが表示されます。  
  
 ![OpenType の標準グリフを使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont01.png "opentypefont01")  
OpenType の標準グリフを使用するテキスト  
  
 Pericles[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントは、一連の標準グリフをデザインのバリエーションを提供する追加のグリフを格納します。 次のテキストのスタイル代替グリフを表示します。  
  
 ![OpenType のスタイル代替グリフを使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont02.png "opentypefont02")  
OpenType のスタイル代替グリフを使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pericles フォントのスタイル代替グリフを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 次のテキストには、いくつか他のスタイル代替グリフの Pericles フォントが表示されます。  
  
 ![OpenType のスタイル代替グリフを使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont03.png "opentypefont03")  
OpenType のスタイル代替グリフを使用するテキスト  
  
 次のマークアップの例では、これら他のスタイル代替グリフを定義する方法を示します。  
  
 [!code-xml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>ランダムなコンテキスト代替  
 ランダムなコンテキスト代替は、単一の文字の複数の代替グリフを提供します。 スクリプトの種類のフォントで実装された場合、この機能は、ランダムに選択したグリフの外観にわずかな相違点のセットを使用して、手書きをシミュレートできます。 次のテキストは、ランダムなコンテキスト代替を Lindsey フォントを使用します。 注意して、文字"a"がわずかに異なって表示  
  
 ![OpenType のランダムなコンテキスト代替を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont23.png "OpenTypeFont23")  
OpenType のランダムなコンテキスト代替を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Lindsey フォントのランダムなコンテキスト代替を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>履歴フォーム  
 歴史的形式は、過去に一般的であった表記規則です。 次のテキストには、「ボストン, マサチューセッツ州」という語句が表示されます。 Palatino Linotype フォントのグリフの履歴フォームを使用します。  
  
 ![OpenType の履歴フォームを使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont10.png "opentypefont10")  
OpenType の履歴フォームを使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの履歴フォームを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>数値のスタイル  
 OpenType フォントでは、大量のテキスト内の数値で使用できる機能をサポートします。  
  
### <a name="fractions"></a>1 秒未満部分  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントは、小数、スラッシュや積み上げなどのスタイルをサポートします。  
  
 次のテキストは、分数 Palatino Linotype フォントのスタイルを表示します。  
  
 ![OpenType を使用するテキストの削減し、分数を上下に並べて](../../../../docs/framework/wpf/advanced/media/opentypefont12.png "opentypefont12")  
OpenType の分数 (横) と分数 (縦) を使用するテキスト  
  
 次のマークアップの例は、分数スタイルのプロパティを使用して、Palatino Linotype フォントを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>古いスタイルの数字  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントは、古いスタイルの数字形式をサポートします。 この形式は、標準になっているスタイルの数字を表示するのに便利です。 次のテキストは、Palatino Linotype フォントの標準および古いスタイルの数字形式で 18 世紀日付を表示します。  
  
 ![OpenType の古いスタイルの数字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont24.png "OpenTypeFont24")  
OpenType の古いスタイルの数字を使用するテキスト  
  
 次のテキストには、古いスタイルの数字に続いて、Palatino Linotype フォントの標準の数字が表示されます。  
  
 ![OpenType 古いスタイルの数字セットを使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont13.png "opentypefont13")  
OpenType の古いスタイルの数字セットを使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの古いスタイルの数字を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>比例と表形式の数値  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントは、数字を使用するときに、幅の調整を制御するプロポーショナルおよび表形式の図の機能をサポートします。 プロポーショナル数字では、各数字を扱うさまざまな幅を持つものとして、「1」の「5」で使われています。 表形式の図は、位置が揃う縦方向に財務型情報を読みやすくできるように、等幅の数字として扱われます。  
  
 次のテキストは、Miramonte フォントを使用して最初の列に&2; つのプロポーショナル数字を表示します。 「5」と「1」数字の幅の違いに注意してください。 2 番目の列では、表形式の図の機能を使用して調整幅と同じ&2; つの数値が表示されます。  
  
 ![OpenType の比例 >/documents/report1.rdl」の表形式の数字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont22.png "OpenTypeFont22")  
OpenType のプロポーショナルおよび表形式の数字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Miramonte フォントでのプロポーショナルおよび表形式の数値を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>スラッシュ ゼロ  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントは、サポート、スラッシュ文字"O"と数字の「0」の違いを強調するために、ゼロの数字形式。 スラッシュ ゼロ、財務およびビジネス情報の識別子によく使用されます。  
  
 次のテキストは、Miramonte フォントを使用してサンプル発注 id を表示します。 最初の行では、標準の数字を使用します。 使用する&2; 番目の線はスラッシュ ゼロ コントラストを提供する優れた大文字の"O"とします。  
  
 ![0 個のスラッシュを付きの OpenType を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont17.png "OpenTypeFont17")  
OpenType のスラッシュ付きのゼロを使用するテキスト  
  
 次のマークアップの例を定義する方法を示しています。 スラッシュ付きのゼロのプロパティを使用して、Miramonte フォント、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>文字体裁クラス  
 <xref:System.Windows.Documents.Typography>オブジェクトは、一連の機能を公開する、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントをサポートしています。 プロパティを設定して<xref:System.Windows.Documents.Typography>マークアップでは、活用するためのドキュメントを作成することができます簡単に[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]機能します。  
  
 次のテキストには、「小型英大文字」と"AllSmallCaps"スタイルを指定の文字の後に、Pescadero フォントの標準の大文字が表示されます。 この場合は、同じフォント サイズは、次の&3; つすべての単語です。  
  
 ![OpenType の大文字を使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont11.png "opentypefont11")  
OpenType の大文字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pescadero フォントの大文字に変換を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクトです。 「小型英大文字」形式を使用する場合は、先頭の大文字は無視されます。  
  
 [!code-xml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 次のコード例では、前のマークアップの例と同じタスクを実行します。  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>文字体裁クラスのプロパティ  
 次の表は、プロパティ、値、および既定の設定、<xref:System.Windows.Documents.Typography>オブジェクトです。  
  
|プロパティ|[値]|既定値|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals>|<xref:System.Windows.FontCapitals?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage>|<xref:System.Windows.FontEastAsianLanguage>|<xref:System.Windows.FontEastAsianLanguage>|<xref:System.Windows.FontEastAsianLanguage?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths> |<xref:System.Windows.FontEastAsianWidths> |<xref:System.Windows.FontEastAsianWidths> |<xref:System.Windows.FontEastAsianWidths>|<xref:System.Windows.FontEastAsianWidths> |<xref:System.Windows.FontEastAsianWidths>|<xref:System.Windows.FontEastAsianWidths?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction>|<xref:System.Windows.FontFraction> |<xref:System.Windows.FontFraction>|<xref:System.Windows.FontFraction?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment>|<xref:System.Windows.FontNumeralAlignment>|<xref:System.Windows.FontNumeralAlignment>|<xref:System.Windows.FontNumeralAlignment?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|数値-バイト|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|数値-バイト|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants>|<xref:System.Windows.FontVariants> |<xref:System.Windows.FontVariants> |<xref:System.Windows.FontVariants> |<xref:System.Windows.FontVariants> |<xref:System.Windows.FontVariants>|<xref:System.Windows.FontVariants?displayProperty=fullName>|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Documents.Typography>   
 [OpenType の仕様](http://go.microsoft.com/fwlink/?LinkId=96731)   
 [WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [OpenType フォント パックのサンプル](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)   
 [アプリケーションでフォントのパッケージング](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)