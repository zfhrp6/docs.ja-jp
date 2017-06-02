---
title: "アプリケーションでのフォントのパッケージング | Microsoft Docs"
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
  - "アプリケーション, パッケージ化 (フォントを)"
  - "フォント, パッケージ化 (アプリケーションで)"
  - "パッケージ化 (アプリケーションでフォントを)"
  - "タイポグラフィ, パッケージ化 (アプリケーションでフォントを)"
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# アプリケーションでのフォントのパッケージング
ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションでフォントをパッケージ化する方法の概要について説明します。  
  
> [!NOTE]
>  多くの種類のソフトウェアと同様に、フォント ファイルは、販売されるのではなくライセンスされます。  フォントの使用を管理するライセンスはベンダーによって異なりますが、[!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] がアプリケーションや [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] で提供しているフォントをカバーするライセンスも含めて、通常、ほとんどのライセンスは、フォントをアプリケーションに埋め込んだり、別の方法で再頒布したりすることを許可していません。  したがって、アプリケーションに埋め込む、または別の方法で再頒布するフォントについて、必要なライセンス権限を取得することは、開発者であるユーザーの責任で行ってください。  
  
   
  
<a name="introduction_to_packaging_fonts"></a>   
## フォントのパッケージングの概要  
 ユーザー インターフェイスのテキストやその他の種類のテキスト ベースのコンテンツを表示するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のリソースとしてフォントを簡単にパッケージ化できます。  フォントは、アプリケーションのアセンブリ ファイルと別にすることも、アセンブリ ファイル内に埋め込むこともできます。  また、アプリケーションで参照できる、リソース専用のフォント ライブラリを作成することもできます。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] および [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] フォントには、各フォントにおけるフォント埋め込みのライセンス権限を示す、型フラグ fsType が含まれています。  ただし、この型フラグはドキュメントに格納された埋め込みフォントのみを参照し、アプリケーションに埋め込まれたフォントは参照しません。  フォントの埋め込み権限を取得するには、<xref:System.Windows.Media.GlyphTypeface> オブジェクトを作成し、その <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> プロパティを参照します。  fsType フラグの詳細については、[OpenType 仕様](http://www.microsoft.com/typography/otspec/os2.htm)の「OS\/2 and Windows Metrics」を参照してください。  
  
 特定のフォント ベンダーまたはカスタム作業のフォント ベンダーを探す際に役立つ連絡先情報については、[Microsoft の文字体裁](http://www.microsoft.com/typography/links/)の Web サイトを参照してください。  
  
<a name="adding_fonts_as_content_items"></a>   
## コンテンツ項目としてのフォントの追加  
 フォントは、アプリケーションのアセンブリ ファイルとは別のプロジェクト コンテンツ項目としてアプリケーションに追加できます。  つまり、コンテンツ項目はアセンブリ内にリソースとして埋め込まれません。  コンテンツ項目を定義する方法を次のプロジェクト ファイル例に示します。  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 アプリケーションが実行時にフォントを使用できるようにするには、アプリケーションの展開ディレクトリでフォントをアクセス可能にする必要があります。  アプリケーションのプロジェクト ファイルの `<CopyToOutputDirectory>` 要素を使用すると、ビルド プロセスでアプリケーション展開ディレクトリにフォントを自動的にコピーできます。  展開ディレクトリにフォントをコピーする方法を次のプロジェクト ファイル例に示します。  
  
```  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 次のコード例は、アプリケーションのフォントをコンテンツ項目として参照する方法を示しています。参照されるコンテンツ項目は、アプリケーションのアセンブリ ファイルと同じディレクトリ内に存在する必要があります。  
  
 [!code-xml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## リソース項目としてのフォントの追加  
 フォントは、アプリケーションのアセンブリ ファイルに埋め込まれたプロジェクト リソース項目としてアプリケーションに追加できます。  リソース用に個別のサブディレクトリを使用して、アプリケーションのプロジェクト ファイルを編成できます。  個別のサブディレクトリ内のリソース項目としてフォントを定義する方法を次のプロジェクト ファイル例に示します。  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
>  アプリケーションにリソースとしてフォントを追加する場合は、アプリケーションのプロジェクト ファイルに `<EmbeddedResource>` 要素ではなく、`<Resource>` 要素を設定していることを確認してください。  ビルド アクションで `<EmbeddedResource>` 要素はサポートされません。  
  
 アプリケーションのフォント リソースを参照する方法を次のマークアップ例に示します。  
  
 [!code-xml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### コードからのフォント リソース項目の参照  
 コードからフォント リソース項目を参照するには、基本[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] と、フォントの場所の参照との 2 つの部分で構成される、フォント リソース参照を指定する必要があります。  これらの値は、<xref:System.Windows.Media.FontFamily.%23ctor%2A> メソッドのパラメーターして使用されます。  プロジェクトの `resources` というサブディレクトリにある、アプリケーションのフォント リソースを参照する方法を次のコード例に示します。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 基本[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] には、フォント リソースが存在する、アプリケーションのサブディレクトリを含めることができます。  この場合、フォントの場所の参照でディレクトリを指定する必要はありませんが、先頭に "`./`" を付けて、基本[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] で指定するディレクトリと同じディレクトリ内のフォント リソースであることを示す必要があります。  次のコード例は、フォント リソース項目を参照する別の方法を示しています。これは前のコード例と同等です。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### 同じアプリケーション サブディレクトリからのフォントの参照  
 アプリケーションのコンテンツとリソース ファイルは、アプリケーション プロジェクトのユーザー定義の同じサブディレクトリに配置できます。  同じサブディレクトリで定義されたコンテンツ ページとフォント リソースを次のプロジェクト ファイル例に示します。  
  
```  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 アプリケーションのコンテンツとフォントが同じディレクトリにあるため、フォント参照はアプリケーションのコンテンツに関連しています。  フォントがアプリケーションと同じディレクトリにある場合に、アプリケーションのフォント リソースを参照する方法を次の例に示します。  
  
 [!code-xml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### アプリケーションでのフォントの列挙  
 アプリケーション内のリソース項目としてフォントを列挙するには、<xref:System.Windows.Media.Fonts.GetFontFamilies%2A> または <xref:System.Windows.Media.Fonts.GetTypefaces%2A> メソッドを使用します。  次の例は、<xref:System.Windows.Media.Fonts.GetFontFamilies%2A> メソッドを使用して、アプリケーション フォントの場所から <xref:System.Windows.Media.FontFamily> のコレクションを返す方法を示しています。  ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 次の例は、<xref:System.Windows.Media.Fonts.GetTypefaces%2A> メソッドを使用して、アプリケーション フォントの場所から <xref:System.Windows.Media.Typeface> のコレクションを返す方法を示しています。  ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## フォント リソース ライブラリの作成  
 フォントのみを含むリソース専用ライブラリを作成できます。この種類のライブラリ プロジェクトにはコードは含まれません。  リソース専用ライブラリの作成は、リソースを使用するアプリケーション コードからリソースを切り離すための一般的な手法です。  また、これにより、複数のアプリケーション プロジェクトでこのライブラリ アセンブリを組み込むことができます。  リソース専用ライブラリ プロジェクトの主要部分を次のプロジェクト ファイル例に示します。  
  
```  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### リソース ライブラリ内のフォントの参照  
 アプリケーションからリソース ファイル内のフォントを参照するには、フォント参照の前にライブラリ アセンブリの名前を付加する必要があります。  ここでは、フォント リソース アセンブリは "FontLibrary" です。  アセンブリ名をアセンブリ内の参照と区切るために、';' 文字を使用します。  キーワード "Component" の後にフォント名への参照を続けて追加すると、フォント ライブラリのリソースへの完全参照が完成します。  リソース ライブラリ アセンブリ内のフォントを参照する方法を次のコード例に示します。  
  
 [!code-xml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  この SDK には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションで使用できる一連の [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントがサンプルとして用意されています。  フォントは、リソース専用ライブラリで定義されています。  詳細については、「[OpenType フォント パックのサンプル](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)」を参照してください。  
  
<a name="limitations_on_font_usage"></a>   
## フォントの使用に関する制限事項  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでのフォントのパッケージングおよび使用に関するいくつかの制限事項を次に示します。  
  
-   **フォント埋め込みアクセス許可情報** : [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションは、フォント埋め込みアクセス許可情報をチェックまたは強制しません。  詳細については、「[フォントのパッケージングの概要](#introduction_to_packaging_fonts)」を参照してください。  
  
-   **フォントの起点サイト** : [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、http または ftp の [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] へのフォント参照は許可されていません。  
  
-   **pack: 表記を使用した絶対 URI** : [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、フォントへの絶対 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 参照の一部として "pack:" を使用してプログラムで <xref:System.Windows.Media.FontFamily> オブジェクトを作成することはできません。  たとえば、`"pack://application:,,,/resources/#Pericles Light"` は無効なフォント参照です。  
  
-   **自動フォント埋め込み** : デザイン時に、アプリケーションのフォントの使用を検索したり、アプリケーションのリソースにフォントを自動的に埋め込んだりすることはサポートされていません。  
  
-   **フォント サブセット** : [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、固定ドキュメント以外でフォント サブセットの作成はサポートされていません。  
  
-   正しくない参照がある場合、アプリケーションは使用可能なフォントの使用に戻ります。  
  
## 参照  
 <xref:System.Windows.Documents.Typography>   
 <xref:System.Windows.Media.FontFamily>   
 [Microsoft Typography: Links, News, and Contacts \(Microsoft タイポグラフィ: リンク、ニュース、連絡先\)](http://www.microsoft.com/typography/links/)   
 [OpenType Specification \(OpenType の仕様\)](http://www.microsoft.com/typography/otspec/)   
 [OpenType フォントの機能](../../../../docs/framework/wpf/advanced/opentype-font-features.md)   
 [OpenType フォント パックのサンプル](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)