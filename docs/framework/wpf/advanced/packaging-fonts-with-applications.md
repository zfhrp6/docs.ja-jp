---
title: アプリケーションでのフォントのパッケージング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: 068a85a5fffd9b7463875695a4b494340ef66cd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="packaging-fonts-with-applications"></a>アプリケーションでのフォントのパッケージング
このトピックでは、パッケージで使用するフォントの方法の概要、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションです。  
  
> [!NOTE]
>  多くの種類のソフトウェアと同様に、フォント ファイルは、販売されるのではなくライセンスされます。 フォントの使用を管理するライセンス異なるベンダーが、一般にフォントをカバーするものを含め、ほとんどのライセンス[!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)]アプリケーションに提供し、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]フォントをアプリケーション内で埋め込みまたはそれ以外の場合に許可しません。再配布します。 したがって、開発者としては、フォントをアプリケーション内に埋め込む場合や別の方法でフォントを再頒布する場合、それらフォントに必要なライセンス権限を取得する責任があります。  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>フォントのパッケージングの概要  
 簡単にパッケージ化して、フォント内でリソースとして、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ベースのアプリケーションにユーザー インターフェイス テキストとその他の種類のテキストを表示するコンテンツ。 フォントは、アプリケーションのアセンブリ ファイルと別にすることも、その中に埋め込むこともできます。 アプリケーションから参照できる、リソース専用のフォント ライブラリを作成することもできます。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] および[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]フォントにライセンスを埋め込むフォントのフォントの権限を示すすれば、型フラグが含まれています。 しかし、この型フラグはドキュメントに格納された埋め込みフォントのみを参照し、アプリケーションに埋め込まれたフォントは参照しません。 作成することで、フォントの権利を埋め込むフォントを取得することができます、<xref:System.Windows.Media.GlyphTypeface>オブジェクトおよび参照するその<xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>プロパティです。 「OS/2 および Windows メトリック」セクションを参照してください、 [OpenType 仕様](http://www.microsoft.com/typography/otspec/os2.htm)すればフラグについての詳細。  
  
 [Microsoft タイポグラフィ](http://www.microsoft.com/typography/links/)Web サイトには、特定のフォントの仕入先を検索またはカスタムの作業のフォントの製造元を検索するのに役立つ連絡先の情報が含まれています。  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>コンテンツ項目としてのフォントの追加  
 フォントは、アプリケーションのアセンブリ ファイルとは別のプロジェクト コンテンツ項目としてアプリケーションに追加できます。 つまり、コンテンツ項目はアセンブリ内にリソースとして埋め込まれません。 コンテンツ項目を定義する方法を次のプロジェクト ファイル例に示します。  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 アプリケーションが実行時にフォントを使用できるようにするには、アプリケーションの展開ディレクトリでフォントをアクセス可能にする必要があります。 `<CopyToOutputDirectory>`アプリケーションのプロジェクト ファイル内の要素では、ビルド処理中に、フォントをアプリケーションの配置ディレクトリに自動的にコピーすることができます。 展開ディレクトリにフォントをコピーする方法を次のプロジェクト ファイル例に示します。  
  
```xml  
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
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>リソース項目としてのフォントの追加  
 フォントは、アプリケーションのアセンブリ ファイルに埋め込まれたプロジェクト リソース項目としてアプリケーションに追加できます。 リソース用として別のサブディレクトリを使用することは、アプリケーションのプロジェクト ファイルの整理に役立ちます。 フォントを別サブディレクトリ内のリソース項目として定義する方法を、次のプロジェクト ファイル例に示します。  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
>  アプリケーションにリソースとしてフォントを追加するときを設定することを確認してください、`<Resource>`要素、および not、`<EmbeddedResource>`アプリケーションのプロジェクト ファイル内の要素。 `<EmbeddedResource>`ビルド アクションの要素がサポートされていません。  
  
 アプリケーションのフォント リソースを参照する方法を次のマークアップ例に示します。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>コードからのフォント リソース項目の参照  
 コードからフォント リソース項目を参照するためには、2 つの部分のフォント リソースへの参照を指定する必要があります。 基本[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; とフォントの場所の参照。 これらの値がのパラメーターとして使用される、<xref:System.Windows.Media.FontFamily.%23ctor%2A>メソッドです。 次のコード例と呼ばれるプロジェクトのサブディレクトリに、アプリケーションのフォントのリソースを参照する方法を示しています。`resources`です。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 基本[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]フォント リソースが存在する、アプリケーションのサブディレクトリを含めることができます。 この場合、フォントの場所の参照は、ディレクトリを指定する必要はありませんが、先頭を含める必要があります"`./`"、フォント リソースを示しますが、ベースで指定された同じディレクトリに[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]です。 次のコード例は、フォント リソース項目を参照する別の方法を示しています。これは前のコード例と同等です。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>同じアプリケーション サブディレクトリからのフォントの参照  
 アプリケーションのコンテンツとリソース ファイルは、アプリケーション プロジェクトのユーザー定義の同じサブディレクトリに配置できます。 同じサブディレクトリで定義されたコンテンツ ページとフォント リソースを次のプロジェクト ファイル例に示します。  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 アプリケーション コンテンツとフォントが同じサブディレクトリ内にあるので、フォント参照はアプリケーション コンテンツから見た相対参照となります。 次の例では、フォントがアプリケーションと同じディレクトリ内にある場合にアプリケーションのフォント リソースを参照する方法を示します。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>アプリケーションでのフォントの列挙  
 フォントを列挙する、アプリケーション内のリソース項目として、いずれかの操作を使用して、<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>または<xref:System.Windows.Media.Fonts.GetTypefaces%2A>メソッドです。 次の例を使用する方法を示しています、<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>のコレクションを返すメソッドを<xref:System.Windows.Media.FontFamily>アプリケーション フォントの場所からのオブジェクト。 ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 次の例を使用する方法を示しています、<xref:System.Windows.Media.Fonts.GetTypefaces%2A>のコレクションを返すメソッドを<xref:System.Windows.Media.Typeface>アプリケーション フォントの場所からのオブジェクト。 ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>フォント リソース ライブラリの作成  
 フォントのみを含むリソース専用ライブラリを作成できます。この種類のライブラリ プロジェクトにはコードは含まれません。 リソース専用ライブラリの作成は、リソースを使用するアプリケーション コードからリソースを切り離すための一般的な手法です。 また、これにより、複数のアプリケーション プロジェクトでこのライブラリ アセンブリを組み込むことができます。 次のプロジェクト ファイル例に、リソース専用ライブラリ プロジェクトの主要部分を示します。  
  
```xml  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>リソース ライブラリ内のフォントの参照  
 アプリケーションからリソース ライブラリ内のフォントを参照するには、フォント参照の前にライブラリ アセンブリの名前を付加する必要があります。 ここでは、フォント リソース アセンブリは "FontLibrary" です。 アセンブリ名をアセンブリ内の参照と区切るために、';' 文字を使用します。 キーワード "Component" の後にフォント名への参照を続けて追加すると、フォント ライブラリのリソースへの完全参照が完成します。 次のコード例では、リソース ライブラリ アセンブリ内のフォントを参照する方法を示します。  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  この SDK には、サンプルのセットが含まれています。[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]とともに使用できるフォント[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。 フォントはリソース専用ライブラリで定義されています。 詳細については、「[OpenType フォント パックのサンプル](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)」をご覧ください。  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>フォントの使用に関する制限事項  
 次のリストは、パッケージおよび内のフォントの使用に関するいくつかの制限を説明[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。  
  
-   **フォント埋め込みアクセス許可ビット:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションはフォント埋め込みアクセス許可ビットのチェックも確認もしません。 参照してください、[パッケージングの概要フォント](#introduction_to_packaging_fonts)詳細についてはします。  
  
-   **配信元のフォントのサイト:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、http または ftp にフォントへの参照を許可しない[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]です。  
  
-   **パックを使用して絶対 URI: 表記:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション作成することはできません、<xref:System.Windows.Media.FontFamily>オブジェクトを使用してプログラムで"pack:"、絶対パスの一部として[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]フォントへの参照。 たとえば、`"pack://application:,,,/resources/#Pericles Light"`無効なフォント参照します。  
  
-   **自動フォント埋め込み:** デザイン時に、アプリケーションのフォントの使用を検索したり、アプリケーションのリソースにフォントを自動的に埋め込んだりすることはサポートされていません。  
  
-   **フォント サブセット:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、固定ドキュメント以外でフォント サブセットの作成はサポートされていません。  
  
-   正しくない参照がある場合、アプリケーションは使用可能なフォントの使用に戻ります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Documents.Typography>  
 <xref:System.Windows.Media.FontFamily>  
 [Microsoft の文字体裁: リンク、ニュース、および連絡先](http://www.microsoft.com/typography/links/)  
 [OpenType の仕様](http://www.microsoft.com/typography/otspec/)  
 [OpenType フォントの機能](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [OpenType フォント パックのサンプル](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
