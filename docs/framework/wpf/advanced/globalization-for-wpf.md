---
title: "WPF のグローバリゼーション"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 418a1b6d2033b8bc84a18578cfc227c5f227ad91
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="globalization-for-wpf"></a>WPF のグローバリゼーション
このトピックの内容を記述する際に注意する必要がありますのある問題が導入されています[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]グローバル市場向けアプリケーション。 グローバリゼーションのプログラミング要素がで定義されている[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]で`System.Globalization`です。  
  

  
<a name="xaml_globalization"></a>   
## <a name="xaml-globalization"></a>XAML グローバリゼーション  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]基づく[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]で定義されているグローバル化のサポートを利用して、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]仕様です。 次のセクションでは、いくつか説明[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]機能を認識しておく必要があります。  
  
<a name="char_reference"></a>   
### <a name="character-references"></a>文字参照  
文字参照は、特定の UTF16 コード単位[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]文字、10 進数または 16 進数のいずれか。 次の例では、コプト語 CAPITAL LETTER 作成、または 'Ϩ' の参照を 10 進数の文字を示しています。

```
&#1000;
```

次の例では、16 進文字の参照を示します。 持つことに注意してください、 **x** 16 進数の前にします。

```
&#x3E8;
```

<a name="encoding"></a>   
### <a name="encoding"></a>エンコード  
 サポートされているエンコード[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は[!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)]、 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] utf-16、および utf-8 です。 先頭には、エンコード ステートメント[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ドキュメント。 エンコーディング属性が存在せず、バイト順もない場合、パーサーでは既定として UTF-8 が使用されます。 UTF-8 と UTF-16 は優先エンコードです。 UTF-7 には対応していません。 次の例での utf-8 エンコードを指定する方法を示します、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル。  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### <a name="language-attribute"></a>言語属性  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]使用して[xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)を要素の language 属性を表します。  活用するために、<xref:System.Globalization.CultureInfo>クラス、言語属性値がによって定義済みカルチャ名のいずれかを指定する必要があります<xref:System.Globalization.CultureInfo>です。 [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) は要素ツリーで継承可能であり (XML ルールによる継承であり、必ずしも依存関係プロパティの継承によるものではありません)、その既定値は、明示的に割り当てられていない場合、空の文字列になります。  
  
 言語属性は、方言を指定するときに非常に役立ちます。 たとえば、フランス語であれば、フランス、ケベック、ベルギー、スイスでスペル、語彙、発音が異なります。 中国語、日本語、および韓国語での内のコード ポイントの共有も[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]が表意文字の形状が異なると、まったく異なるフォントを使用します。  
  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の例では、`fr-CA`カナダ フランス語を指定する言語の属性です。  
  
```xml  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### <a name="unicode"></a>Unicode  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]すべてをサポートしている[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]サロゲートを含む機能します。 文字セットにマップできる限り[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]はサポートされています。 たとえば、GB18030 では、一部の文字が中国語、日本語、韓国語 (CFK) の拡張 A および B とサロゲート ペアにマッピングされているため、完全に対応しています。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションを使用できる<xref:System.Globalization.StringInfo>サロゲート ペアがあるかどうかを理解することや、組み合わせ文字なし文字列を操作します。  
  
<a name="design_intl_ui_with_xaml"></a>   
## <a name="designing-an-international-user-interface-with-xaml"></a>XAML で各国対応ユーザー インターフェイスを設計する  
 このセクションで説明[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]機能アプリケーションを作成するときに考慮する必要があります。  
  
<a name="intl_text"></a>   
### <a name="international-text"></a>国際対応テキスト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]すべての組み込みの処理が含まれます[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]書記体系をサポートします。  
  
 現在、次の書体がサポートされています。  
  
-   アラビア語  
  
-   ベンガル語  
  
-   デバナガリ  
  
-   キリル言語  
  
-   ギリシャ語  
  
-   グジャラート語  
  
-   グルムキー  
  
-   ヘブライ語  
  
-   表意文字スクリプト  
  
-   カナラ語  
  
-   ラオス語  
  
-   ラテン語  
  
-   マラヤーラム語  
  
-   モンゴル語  
  
-   オディア語  
  
-   シリア語  
  
-   タミール語  
  
-   テルグ語  
  
-   ターナ  
  
-   タイ語*  
  
-   チベット語  
  
 * このリリースでは、タイ語テキストを表示し、編集できますが、単語を分割することはできません。  
  
 現在、次のスクリプトはサポートされていません。  
  
-   クメール語  
  
-   韓国語の古いハングル  
  
-   ミャンマー  
  
-   シンハラ語  
  
 すべての書記体系エンジン サポート[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントです。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]フォントを含めることができます、[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]より国際化とハイエンド傍点を文字のフォントをデザインするフォントの作成者を可能にするテーブルをレイアウトします。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]フォント レイアウト テーブルに関する情報が含まグリフの置換、グリフ配置、理由、およびベースラインは、次の配置、テキスト レイアウトを向上させるためにテキスト処理アプリケーションを有効にするとします。  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]大規模なグリフの処理は、設定を使用してフォントを許可する[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]エンコードします。 このようなエンコードにより、広範な国際対応が可能になり、さまざまなグリフを印刷できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テキストのレンダリングが電源に[!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]解決の独立性をサポートするサブ ピクセル テクノロジです。 これにより読みやすさが大幅に向上し、あらゆる書体で高品質の雑誌スタイルの書面を作成できます。  
  
<a name="intl_layout"></a>   
### <a name="international-layout"></a>国際対応レイアウト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では非常に便利な方法で横書きレイアウト、双方向レイアウト、縦書きレイアウトを作成できます。 プレゼンテーション フレームワークで、<xref:System.Windows.FrameworkElement.FlowDirection%2A>レイアウトを定義するプロパティを使用できます。 フローの方向パターン:  
  
-   *LeftToRight* - ラテン語や東アジア言語などのための横書きレイアウト。  
  
-   *RightToLeft* - アラビア語やヘブライ語などのための双方向レイアウト。  
  
<a name="developing_localizable_apps"></a>   
## <a name="developing-localizable-applications"></a>ローカライズ可能なアプリケーションの開発  
 世界中で利用されるアプリケーションを開発するときは、アプリケーションをローカライズ可能にすることを忘れてはなりません。 後続のトピックで、考慮事項を指摘します。  
  
<a name="mui"></a>   
### <a name="multilingual-user-interface"></a>多言語ユーザー インターフェイス  
 多言語ユーザー インターフェイス (MUI) は、[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]の切り替えをサポートして[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]を別の 1 つの言語からです。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでは、アセンブリのモデルを使用して、MUI をサポートします。 1 つのアプリケーションに言語に依存しないアセンブリと言語に依存するサテライト リソース アセンブリが含まれます。 エントリ ポイントはメイン アセンブリのマネージ .EXE です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]リソース ローダーを活用、[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]のリソースの検索とフォールバックをサポートするためにリソース マネージャー。 多言語サテライト アセンブリは同じメイン アセンブリと連動します。 読み込まれているリソース アセンブリに依存して、<xref:System.Globalization.CultureInfo.CurrentUICulture%2A>現在のスレッド。  
  
<a name="localizable_ui"></a>   
### <a name="localizable-user-interface"></a>ローカライズ可能なユーザー インターフェイス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を定義する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で開発すると、オブジェクトの階層に一連のプロパティとロジックを指定できます。 主な用途[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を開発するが[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが、これを使用して、任意の階層を指定して[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]オブジェクト。 ほとんどの開発者が使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]がアプリケーションの指定に[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]などのプログラミング言語を使用して[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]ユーザーとのやり取りに反応するためです。  
  
 リソースの観点から、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルの言語に依存するについて説明するように設計[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]リソースがあり、したがってその最終的な配信形式が国際対応の言語をサポートするためにローカライズできる必要があります。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]多くようにイベントが処理できない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アプリケーションには、これを行うコードのブロックが含まれています。 詳細については、次を参照してください。 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)です。 コードが除去され、異なるバイナリにコンパイル時に、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルは XAML の BAML 形式にトークンです。 XAML ファイル、画像、その他の種類の管理対象リソース オブジェクトの BAML 形式はサテライト リソース アセンブリに組み込まれます。サテライト リソース アセンブリに組み込むことで、他の言語にローカライズできます。ローカライズが必要なければ、メイン アセンブリに組み込まれます。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]すべてのアプリケーションをサポート、 [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]リソース文字列テーブル、イメージ、およびなどを含むです。  
  
<a name="building_localizable_apps"></a>   
### <a name="building-localizable-applications"></a>ローカライズ可能なアプリケーションの構築  
 ローカライズとは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を異なるカルチャ。 させる、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションのローカライズ可能な開発者は、すべてのローカライズ可能なリソースをリソース アセンブリに組み込む必要があります。 リソース アセンブリは、異なる言語にローカライズし、分離コードがリソースの管理を使用して[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]を読み込めません。 必要なファイルのいずれか、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、プロジェクト ファイル (.proj)。 アプリケーションで使用するすべてのリソースをプロジェクト ファイルに含める必要があります。 その方法を .csproj ファイルからの次の例で示します。  
  
```xml  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 使用する、アプリケーションでリソースのインスタンスを作成、<xref:System.Resources.ResourceManager>し、使用するリソースを読み込みます。 この方法を次の例に示します。  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## <a name="using-clickonce-with-localized-applications"></a>ローカライズされたアプリケーションで ClickOnce を使用する  
 ClickOnce は、新しい Windows フォーム展開テクノロジが付属している[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]です。 アプリケーションをインストールしたり、Web アプリケーションをアップグレードしたりできます。 ClickOnce で展開されたアプリケーションがローカライズされると、ローカライズされたカルチャでのみ表示できます。 たとえば、配置済みのアプリケーションが日本語にローカライズされている場合のみ表示する日本語で[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]英語ではなく[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]です。 これは、問題の英語バージョンを実行する日本語のユーザーの一般的なシナリオになっているため[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]です。  
  
 この問題の解決策は、非依存言語フォールバック属性を設定することです。 アプリケーション開発者はメイン アセンブリからリソースを任意で削除し、特定のカルチャに対応するサテライト アセンブリでそのリソースを見つけられるように指定できます。 このプロセスで使用するを制御する、<xref:System.Resources.NeutralResourcesLanguageAttribute>です。 コンス トラクター、<xref:System.Resources.NeutralResourcesLanguageAttribute>クラスを受け取る 1 つ、2 つの署名には、<xref:System.Resources.UltimateResourceFallbackLocation>場所を指定するパラメーターを<xref:System.Resources.ResourceManager>フォールバック リソースを抽出する必要があります: メイン アセンブリまたはサテライト アセンブリ。 この属性を使用する方法の例を次に示します。 コードがによって、最終フォールバック位置の<xref:System.Resources.ResourceManager>"de"ディレクトリのサブディレクトリに、現在実行中のアセンブリのリソースを検索します。  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
```  
  
## <a name="see-also"></a>関連項目  
 [WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
