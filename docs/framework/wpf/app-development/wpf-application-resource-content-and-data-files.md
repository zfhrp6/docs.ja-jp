---
title: WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: 571b8f71ce233011ae6fc7a6d4d53c5029d27d69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] データを含む実行可能でないなどのファイルに多くの場合、依存するアプリケーション[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]イメージ、ビデオ、およびオーディオです。 Windows Presentation Foundation (WPF) は、構成、識別、およびこれらの種類のアプリケーションのデータ ファイルと呼ばれる、データ ファイルを使用して特別なサポートを提供します。 このサポートの中心となるのは、次のような特定のアプリケーション データ ファイルの種類のセットです。  
  
-   **リソース ファイル**: 実行可能ファイルまたはライブラリにコンパイルされるデータ ファイル[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリ。  
  
-   **コンテンツ ファイル**: スタンドアロンのデータ ファイルを実行可能ファイルとの明示的な関連付けを持つ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリ。  
  
-   **配信元のファイルのサイト**: スタンドアロンのデータ ファイルを実行可能ファイルとの関連付けを持たない[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリ。  
  
 これらの 3 種類のファイルの重要な違いは、リソース ファイルとコンテンツ ファイルはビルド時に認識されるという点です。アセンブリは、これらを明確に認識します。 配信元のファイルのサイトのただし、アセンブリがあります認識したり、または暗黙的なナレッジ パックを[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]参照。 後者の場合の元のファイルの参照先のサイトが実際に存在するという保証はありません。  
  
 Windows Presentation Foundation (WPF) が、パックを使用するにはアプリケーションのデータ ファイルを参照するには、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]で詳しく説明されているスキーム[WPF のパック Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md))。  
  
 このトピックでは、アプリケーション データ ファイルを構成および使用する方法について説明します。  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>リソース ファイル (Visual Studio)  
 アプリケーション データ ファイルを常にアプリケーションで使用可能にするには、コンパイルしてアプリケーションのメイン実行可能アセンブリまたはその参照アセンブリの 1 つに組み込む必要があります。 この種類のアプリケーション データ ファイルと呼ばれる、*リソース ファイル*です。  
  
 リソース ファイルは、次のときに使用します。  
  
-   コンパイルしてアセンブリに組み込んだ後に、リソース ファイルのコンテンツを更新する必要がない。  
  
-   ファイルの依存関係の数を減らして、アプリケーション配布の複雑さを軽減する必要がある。  
  
-   アプリケーション データ ファイルをローカライズする必要があります (を参照してください[WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md))。  
  
> [!NOTE]
>  このセクションで説明されているリソース ファイルは、リソース ファイルの記載と異なる[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)しで説明されている埋め込みまたはリンクされたリソースとは異なる[を管理するアプリケーションのリソース (.NET)](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>リソース ファイルの構成  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、リソース ファイルに含まれているファイルとは、[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]としてプロジェクト、`Resource`項目。  
  
```xml  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、ファイルをプロジェクトの設定を追加して、リソース ファイルを作成するその`Build Action`に`Resource`です。  
  
 プロジェクトのビルド時に[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]アセンブリにリソースをコンパイルします。  
  
### <a name="using-resource-files"></a>リソース ファイルの使用  
 リソース ファイルを読み込むには、呼び出すことができます、<xref:System.Windows.Application.GetResourceStream%2A>のメソッド、<xref:System.Windows.Application>を渡して、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]目的のリソース ファイルを識別します。 <xref:System.Windows.Application.GetResourceStream%2A> 返します、<xref:System.Windows.Resources.StreamResourceInfo>として、リソース ファイルを公開するオブジェクト、<xref:System.IO.Stream>とそのコンテンツの種類について説明します。  
  
 たとえば、次のコードが使用する方法を示します<xref:System.Windows.Application.GetResourceStream%2A>を読み込む、<xref:System.Windows.Controls.Page>リソース ファイルのコンテンツとして設定し、 <xref:System.Windows.Controls.Frame> (`pageFrame`)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 呼び出し中に<xref:System.Windows.Application.GetResourceStream%2A>にアクセスすること、<xref:System.IO.Stream>を設定します、プロパティの型への変換の追加の作業を実行する必要があります。 代わりに、できる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の開始タグと変換するように注意、<xref:System.IO.Stream>直接コードを使用して型のプロパティにリソース ファイルを読み込む。  
  
 次の例を読み込む方法を示しています、<xref:System.Windows.Controls.Page>に直接、 <xref:System.Windows.Controls.Frame> (`pageFrame`) コードを使用します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>リソース ファイルとしてのアプリケーション コード ファイル  
 特殊な一連の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]パックを使用してアプリケーション コード ファイルを参照できる[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]windows、ページ、フロー ドキュメントのリソース ディクショナリなど、します。 たとえば、設定、<xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>のパック プロパティ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]ウィンドウまたはアプリケーションの起動時にロードしたいページを参照します。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 場合に、このを行うことができます、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]でファイルが含まれています、[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]としてプロジェクト、`Page`項目。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、追加<xref:System.Windows.Window>、 <xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.FlowDocument>、または<xref:System.Windows.ResourceDictionary>、プロジェクトに、`Build Action`マークアップのファイルは既定で`Page`です。  
  
 ときに使用したプロジェクトの`Page`項目をコンパイルすると、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目がバイナリ形式に変換され、関連するアセンブリにコンパイルします。 したがって、これらのファイルは、通常のリソース ファイルと同様に使用できます。  
  
> [!NOTE]
>  場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]としてファイルが構成されている、`Resource`項目、および生の分離コード ファイルがない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は生のバイナリのバージョンではなく、アセンブリにコンパイルされて[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>コンテンツ ファイル  
 A*コンテンツ ファイル*と共に実行可能アセンブリの loose ファイルとして配布されます。 コンテンツ ファイルはコンパイルされてアセンブリに組み込まれるのではありませんが、アセンブリのコンパイル時に、各コンテンツ ファイルとの関連付けを確立するメタデータが使用されます。  
  
 アプリケーションに必要な特定のアプリケーション データ ファイルのセットが更新されても、そのファイルを使用するアセンブリを再コンパイルせずに、コンテンツ ファイルを使用する必要があります。  
  
### <a name="configuring-content-files"></a>コンテンツ ファイルの構成  
 プロジェクトにコンテンツ ファイルを追加するには、アプリケーション データ ファイルとして含まれているにする必要があります、`Content`項目。 さらに、コンテンツ ファイルがアセンブリに直接コンパイルされていないために設定する必要が、 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory`メタデータを指定する要素、コンテンツ ファイルがビルドされたアセンブリに対応する場所にコピーします。 プロジェクトがビルドされるたびに、ビルド出力フォルダーにコピーするリソースに該当する場合は、設定する、`CopyToOutputDirectory`メタデータ要素で、`Always`値。 使用して、ビルド出力フォルダーに、リソースの最新のバージョンのみがコピーされることを確認するそれ以外の場合、`PreserveNewest`値。  
  
 次に示すファイルは、新しいバージョンのリソースがプロジェクトに追加された場合にのみビルド出力フォルダーにコピーされるコンテンツ ファイルとして構成されています。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、ファイルをプロジェクトの設定を追加して、コンテンツ ファイルを作成するその`Build Action`に`Content`、設定とその`Copy to Output Directory`に`Copy always`(と同じ`Always`) および`Copy if newer`(と同じ`PreserveNewest`)。  
  
 プロジェクトのビルド時に、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性は各コンテンツ ファイルのアセンブリのメタデータにコンパイルします。  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 値、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>プロジェクト内の位置に対してコンテンツのファイルへのパスを意味します。 たとえば、ある場合は、コンテンツ ファイルがプロジェクトのサブフォルダーに、追加パス情報に組み込む、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>値。  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>値もビルド出力フォルダー内のコンテンツのファイルへのパスの値。  
  
### <a name="using-content-files"></a>コンテンツ ファイルの使用  
 コンテンツ ファイルを読み込むには、呼び出すことができます、<xref:System.Windows.Application.GetContentStream%2A>のメソッド、<xref:System.Windows.Application>を渡して、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]目的のコンテンツ ファイルを識別します。 <xref:System.Windows.Application.GetContentStream%2A> 返します、<xref:System.Windows.Resources.StreamResourceInfo>として、コンテンツ ファイルを公開するオブジェクト、<xref:System.IO.Stream>とそのコンテンツの種類について説明します。  
  
 たとえば、次のコードが使用する方法を示します<xref:System.Windows.Application.GetContentStream%2A>を読み込む、<xref:System.Windows.Controls.Page>ファイルのコンテンツのコンテンツとして設定し、 <xref:System.Windows.Controls.Frame> (`pageFrame`)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 呼び出し中に<xref:System.Windows.Application.GetContentStream%2A>にアクセスすること、<xref:System.IO.Stream>を設定します、プロパティの型への変換の追加の作業を実行する必要があります。 代わりに、できる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の開始タグと変換するように注意、<xref:System.IO.Stream>直接コードを使用して型のプロパティにリソース ファイルを読み込む。  
  
 次の例を読み込む方法を示しています、<xref:System.Windows.Controls.Page>に直接、 <xref:System.Windows.Controls.Frame> (`pageFrame`) コードを使用します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>起点サイト ファイル  
 リソース ファイルがによって定義された、と共に配布されるアセンブリとの明示的なリレーションシップを持つ、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>です。 ただし、アセンブリとアプリケーション データ ファイル間に暗黙的な関係を持たせる、または関係を持たせない場合があります。たとえば次のような場合です。  
  
-   コンパイル時にファイルが存在しない場合。  
  
-   アセンブリが必要とするファイルが、実行時までわからない場合。  
  
-   関連付けられているアセンブリを再コンパイルせずにファイルを更新可能にする場合。  
  
-   オーディオやビデオなど大容量のデータ ファイルを使用するアプリケーションで、ユーザーが選択した場合にのみファイルをダウンロードする場合。  
  
 これらの種類を使用して従来のファイルの読み込みが可能である[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]file:/// http:// 方式などのスキーム。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 ただし、file:/// スキームや http:// スキームを使用する場合は、アプリケーションに完全信頼が必要です。 アプリケーションの場合、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]ですが、インターネットまたはイントラネットから起動して、ルース ファイルしか読み込めません原点 (アプリケーションのサイトからこれらの場所から起動したアプリケーションで許可される権限のセットのみを要求場所の起動)。 このようなファイルと呼びます*元のサイト*ファイル。  
  
 起点サイト ファイルは部分信頼アプリケーションの唯一のオプションですが、部分信頼アプリケーション以外でも使用できます。 完全信頼アプリケーションでも、読み込むアプリケーション データ ファイルがビルド時点では不明な場合があります。完全信頼アプリケーションでは file:/// を使用できますが、アプリケーション データ ファイルがアプリケーション アセンブリと同じフォルダーにインストールされることも、サブフォルダーにインストールされることも考えられます。 この場合は、起点サイト参照を使用する方が、file:/// を使用するよりも簡単です。file:/// を使用するには、ファイルの完全パスを指定する必要があるためです。  
  
> [!NOTE]
>  ファイルがキャッシュされていない元のサイト、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]をクライアント コンピューターは、コンテンツ ファイルの中でします。 したがって、起点サイト ファイルは明確に要求されたときにのみダウンロードされます。 場合、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]アプリケーションが大規模なメディア ファイルをサイト元ファイルの初期のアプリケーションの起動がはるかに高速、および要求時にファイルのダウンロードのみの手段として構成することです。  
  
### <a name="configuring-site-of-origin-files"></a>起点サイト ファイルの構成  
 従来の配置を使用する必要がある場合は、サイトの元のファイルの存在しないまたは不明なコンパイル時に、いずれかの使用など、実行時に、必要なファイルを確保するための機構を使用できます、`XCopy`コマンド ライン プログラムや、 [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 わかっている場合はコンパイル時にファイルを元のサイトに配置されるけれどもまだ明示的な依存関係を回避するにそれらのファイルを追加することができます、[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]としてプロジェクト`None`項目。 コンテンツのファイルで設定する必要がある、 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory`元のファイルのサイトがいずれかを指定することによってビルドされたアセンブリに対応する場所にコピーされていることを指定する属性、`Always`値または`PreserveNewest`値。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、ファイルをプロジェクトの設定を追加して元のファイルのサイトを作成するその`Build Action`に`None`です。  
  
 プロジェクトのビルド時に[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]ビルド出力フォルダーに指定されたファイルをコピーします。  
  
### <a name="using-site-of-origin-files"></a>起点サイト ファイルの使用  
 元のファイルのサイトを読み込むには、呼び出すことができます、<xref:System.Windows.Application.GetRemoteStream%2A>のメソッド、<xref:System.Windows.Application>を渡して、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]元のファイルの目的のサイトを識別します。 <xref:System.Windows.Application.GetRemoteStream%2A> 返します、<xref:System.Windows.Resources.StreamResourceInfo>として元のファイルのサイトを公開するオブジェクト、<xref:System.IO.Stream>とそのコンテンツの種類について説明します。  
  
 例として、次のコードが使用する方法を示します<xref:System.Windows.Application.GetRemoteStream%2A>を読み込む、<xref:System.Windows.Controls.Page>元のサイトのコンテンツとして設定し、ファイル、 <xref:System.Windows.Controls.Frame> (`pageFrame`)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 呼び出し中に<xref:System.Windows.Application.GetRemoteStream%2A>にアクセスすること、<xref:System.IO.Stream>を設定します、プロパティの型への変換の追加の作業を実行する必要があります。 代わりに、できる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の開始タグと変換するように注意、<xref:System.IO.Stream>直接コードを使用して型のプロパティにリソース ファイルを読み込む。  
  
 次の例を読み込む方法を示しています、<xref:System.Windows.Controls.Page>に直接、 <xref:System.Windows.Controls.Frame> (`pageFrame`) コードを使用します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>ビルドの種類を変更した後のリビルド  
 アプリケーション データ ファイルのビルドの種類を変更した後は、変更を確実に反映するためにアプリケーション全体をリビルドする必要があります。 アプリケーションのみをビルドしても、変更は適用されません。  
  
## <a name="see-also"></a>関連項目  
 [WPF におけるパッケージの URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
