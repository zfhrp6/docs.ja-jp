---
title: "WPF のグローバリゼーション | Microsoft Docs"
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
  - "グローバリゼーション"
  - "各国対応ユーザー インターフェイス, XAML"
  - "XAML, グローバリゼーション"
  - "XAML, 各国対応ユーザー インターフェイス"
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# WPF のグローバリゼーション
ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションをグローバル市場向けに作成する際の注意点について説明します。  グローバリゼーションのプログラミング要素は、[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] の `System.Globalization` に定義されています。  
  
   
  
<a name="xaml_globalization"></a>   
## XAML のグローバリゼーション  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] は [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] に基づいており、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 仕様で定義されているグローバリゼーション サポートを利用します。  以下のセクションでは、注意する必要がある [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 機能について説明します。  
  
<a name="char_reference"></a>   
### 文字参照コード  
 文字参照コードは、それによって表される特定の [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] 文字の番号を 10 進形式または 16 進形式で指定します。  10 進形式の文字参照コードの例を次に示します。  
  
```  
Ϩ  
```  
  
 次の例は、16 進形式の文字参照コードを示しています。  16 進数の前に **x** が付いていることに注意してください。  
  
```  
Ϩ  
```  
  
<a name="encoding"></a>   
### エンコーディング  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、[!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)]、[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]、UTF\-16、および UTF\-8 のエンコードがサポートされています。  エンコード ステートメントは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ドキュメントの先頭にあります。  エンコード属性が存在せず、バイト順がない場合、パーサーは既定で UTF\-8 に設定されます。  優先されるエンコードは UTF\-8 と UTF\-16 です。  UTF\-7 はサポートされていません。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルで UTF\-8 エンコードを指定する方法を次の例に示します。  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### Language 属性  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、[xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) を使用して要素の言語属性を表します。  <xref:System.Globalization.CultureInfo> クラスを利用するには、言語属性の値が <xref:System.Globalization.CultureInfo> で定義済みのカルチャ名である必要があります。  [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) は要素ツリーでの継承が可能で \(XML 規則では、依存関係プロパティが継承されるため必ずしも継承可能ではない\)、明示的に割り当てられていない場合の既定値は空の文字列です。  
  
 言語属性は、方言を指定する場合にとても便利です。  たとえばフランス語では、フランス、ケベック、ベルギー、およびスイスで、スペル、語彙、および発音がそれぞれ異なります。  また、中国語、日本語、および韓国語は、[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] のコード ポイントを共有していますが、文字の形状が異なるため、まったく異なるフォントを使用します。  
  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、`fr-CA` 言語属性を使用してカナダ フランス語を指定しています。  
  
```  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### Unicode  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は、サロゲートを含むすべての [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] 機能をサポートしています。  [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] にマッピングできる文字セットはすべてサポートされます。  たとえば、GB18030 によって導入される文字は、CJK \(Chinese, Japanese, and Korean\) 統合漢字拡張 A および B とサロゲート ペアにマッピングされるため、GB18030 は完全にサポートされます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションで <xref:System.Globalization.StringInfo> を使用すると、文字列にサロゲート ペアや組み合わせ文字があるかどうかに関係なく文字列を操作できます。  
  
<a name="design_intl_ui_with_xaml"></a>   
## XAML による各国対応ユーザー インターフェイスの設計  
 ここでは、アプリケーションを作成する際に考慮する必要がある[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 機能について説明します。  
  
<a name="intl_text"></a>   
### 各国対応テキスト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] でサポートされているすべての書記体系の処理が組み込まれています。  
  
 現在サポートされている書記体系を次に示します。  
  
-   アラビア語  
  
-   ベンガル語  
  
-   デバナガリ  
  
-   キリル語  
  
-   ギリシャ語  
  
-   グジャラート語  
  
-   グルムキー  
  
-   ヘブライ語  
  
-   表意文字  
  
-   カナラ語  
  
-   ラオス語  
  
-   ラテン語  
  
-   マラヤラム語  
  
-   モンゴル語  
  
-   オディア語  
  
-   シリア語  
  
-   タミル語  
  
-   テルグ語  
  
-   ターナ  
  
-   タイ語\*  
  
-   チベット語  
  
 \* このリリースでは、タイ語テキストの表示と編集はサポートされていますが、単語の区切りはサポートされていません。  
  
 現在サポートされていない書記体系を次に示します。  
  
-   クメール語  
  
-   韓国語の古ハングル  
  
-   ミャンマー  
  
-   シンハラ語  
  
 すべての書記体系エンジンで [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントがサポートされています。  [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォントには [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] レイアウト テーブルを含めることができるため、フォント作成者は、各国対応が強化された高品質なタイポグラフィ フォントをデザインすることができます。  [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォント レイアウト テーブルには、グリフ代替、グリフの配置、両端揃え、およびベースラインの配置に関する情報が含まれています。これにより、テキスト処理アプリケーションによるテキスト レイアウトが強化されます。  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォントでは、[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] エンコードを使用して大きなグリフ セットを処理することができます。  こうしたエンコードにより、グリフの文字体裁のバリエーションだけでなく、各国対応の幅も広がります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のテキスト レンダリングには、解像度に依存しないレンダリングをサポートする [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] サブピクセル テクノロジが利用されています。  これにより読みやすさが大幅に向上し、すべての書記体系で高品質な雑誌スタイルのドキュメントをサポートできるようになります。  
  
<a name="intl_layout"></a>   
### 各国対応レイアウト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、横型、縦型、および双方向のレイアウトをサポートするための非常に便利な方法が用意されています。  プレゼンテーション フレームワークで、<xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティを使用してレイアウトを定義できます。  フロー方向のパターンは次のとおりです。  
  
-   *LeftToRight* : ラテン言語や東アジア言語などの横型レイアウト。  
  
-   *RightToLeft* : アラビア語やヘブライ語などの双方向レイアウト。  
  
<a name="developing_localizable_apps"></a>   
## ローカライズ可能なアプリケーションの開発  
 世界各国で使用されるアプリケーションを作成する際には、アプリケーションがローカライズ可能でなければならないということを念頭に置く必要があります。  以下のトピックでは、その際に考慮する必要がある点について説明します。  
  
<a name="mui"></a>   
### 複数言語ユーザー インターフェイス  
 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] では、MUI \(Multilingual User Interface\) によって言語間での [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] の切り替えをサポートしています。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションは、アセンブリ モデルを使用して MUI をサポートします。  1 つのアプリケーションに、言語に依存しないアセンブリと、言語に依存するサテライト リソース アセンブリが含まれます。  エントリ ポイントはメイン アセンブリのマネージ .EXE です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] リソース ローダーは、[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] のリソース マネージャーを利用して、リソースのルックアップとフォールバックをサポートします。  複数の言語サテライト アセンブリが同じメイン アセンブリで動作します。  読み込まれるリソース アセンブリは、現在のスレッドの <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> によって決まります。  
  
<a name="localizable_ui"></a>   
### ローカライズ可能なユーザー インターフェイス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用して [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を定義します。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、一連のプロパティとロジックを持つオブジェクトの階層を指定することができます。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は主に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの開発に使用されますが、任意の[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクトの階層を指定することもできます。  ほとんどの開発者は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用してアプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を指定し、[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] などのプログラミング言語を使用してユーザー操作に応答します。  
  
 リソースの観点から見た場合、言語に依存しない [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を記述するために作成された [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルはリソース要素であるため、各国の言語をサポートするためには、最終的にローカライズ可能な形式で配布する必要があります。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] はイベントを処理できないため、多くの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] アプリケーションにはそのためのコードが含まれています。  詳細については、「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照してください。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルが XAML の BAML 形式にトークン化されると、コードが取り除かれて別のバイナリにコンパイルされます。XAML の BAML 形式のファイル、イメージ、およびその他の種類のマネージ リソース オブジェクトは、他の言語にローカライズできるようにサテライト リソース アセンブリに埋め込まれるか、ローカリゼーションが不要な場合にはメイン アセンブリに埋め込まれます。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションは、文字列テーブルやイメージなどを含むすべての [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] リソースをサポートしています。  
  
<a name="building_localizable_apps"></a>   
### ローカライズ可能なアプリケーションのビルド  
 ローカリゼーションとは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を異なるカルチャに適合させることを意味します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションをローカライズ可能にするには、ローカライズ可能なすべてのリソースをリソース アセンブリに組み込む必要があります。  リソース アセンブリはさまざまな言語にローカライズされ、分離コードがリソース管理 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] を使用して読み込みます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに必要なファイルの 1 つはプロジェクト ファイル \(.proj\) です。  プロジェクト ファイルには、アプリケーションで使用するすべてのリソースを含める必要があります。  .csproj ファイルの場合の例を次に示します。  
  
```  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 アプリケーションでリソースを使用するには、<xref:System.Resources.ResourceManager> をインスタンス化し、使用するリソースを読み込みます。  この方法を次の例に示します。  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## ローカライズされたアプリケーションでの ClickOnce の使用  
 ClickOnce は Windows フォームの新しい配置テクノロジで、[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] で利用できます。  これにより、アプリケーションのインストールや Web アプリケーションのアップグレードを行うことができます。  ClickOnce で配置されたアプリケーションをローカライズした場合、ローカライズしたカルチャ以外では表示できません。  たとえば、配置されたアプリケーションを日本語にローカライズすると、日本語の [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] でしか表示できなくなります \(英語の [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] では表示できません\)。  日本のユーザーが英語版の [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] を実行するケースは珍しくないため、これは問題になります。  
  
 この問題を解決するには、ニュートラル言語フォールバック属性を設定します。  アプリケーション開発者は、リソースをメイン アセンブリから削除して、特定のカルチャに対応するサテライト アセンブリにそのリソースを置くように指定することができます。  この処理を制御するには、<xref:System.Resources.NeutralResourcesLanguageAttribute> を使用します。  <xref:System.Resources.NeutralResourcesLanguageAttribute> クラスのコンストラクターには 2 つのシグネチャがあります。そのうちの 1 つは、<xref:System.Resources.ResourceManager> がフォールバック リソースを抽出する場所 \(メイン アセンブリかサテライト アセンブリか\) を指定する <xref:System.Resources.UltimateResourceFallbackLocation> パラメーターを受け取ります。  この属性を使用する方法の例を次に示します。  このコードでは、最終フォールバック位置について、現在実行しているアセンブリのディレクトリの "de" サブディレクトリからリソースを検索するように <xref:System.Resources.ResourceManager> に指示しています。  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
  
```  
  
## 参照  
 [WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)