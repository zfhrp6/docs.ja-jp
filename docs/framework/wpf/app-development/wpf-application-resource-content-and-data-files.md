---
title: "WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル | Microsoft Docs"
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
  - "アプリケーション開発 [WPF], files"
  - "アプリケーション管理 [WPF]"
  - "コンテンツ ファイル [WPF]"
  - "埋め込みリソース [WPF]"
  - "ファイル [WPF]"
  - "制約が緩いリソース [WPF]"
  - "参照元アプリケーション ファイル [WPF]"
  - "リモート ファイル [WPF]"
  - "リソース ファイル [WPF]"
  - "起点サイト ファイル [WPF]"
  - "WPF アプリケーション, files"
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] アプリケーションは、多くの場面で、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、イメージ、ビデオ、オーディオなどの実行可能ではないデータを格納したファイルを必要とします。  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] には、アプリケーション データ ファイルと呼ばれるこれらの種類のデータ ファイルを設定、指定、および使用するための特殊なサポート機能があります。  このサポートの中心となるのは、次の種類のアプリケーション データ ファイルです。  
  
-   **リソース ファイル** : コンパイルして実行可能またはライブラリ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アセンブリを作成するためのデータ ファイル。  
  
-   **コンテンツ ファイル** : 実行可能 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アセンブリとの明示的な関連付けを持つスタンドアロン データ ファイル。  
  
-   **起点サイト ファイル** : 実行可能 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アセンブリとの関連付けを持たないスタンドアロン データ ファイル。  
  
 この 3 種類のファイルの重要な違いは、リソース ファイルとコンテンツ ファイルはビルド時に認識されるという点です。アセンブリは、これらを明確に認識します。  起点サイト ファイルについては、アセンブリはまったく認識しないか、パッケージの[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 参照を通して暗黙的に認識します。後者の場合、参照される起点サイト ファイルが実際に存在することは保証されません。  
  
 アプリケーション データ ファイルを参照するために、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] はパッケージの[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] スキームを使用します。このスキームについては、「[WPF におけるパッケージの URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)」で詳しく説明します。  
  
 ここでは、アプリケーション データ ファイルを設定および使用する方法について説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Resource_Files"></a>   
## リソース ファイル  
 特定のアプリケーション データ ファイルを常にアプリケーションで使用できるようにするには、コンパイルしてアプリケーションのメイン実行可能アセンブリまたはその参照アセンブリの 1 つに組み込む必要があります。  この種類のアプリケーション データ ファイルを、*リソース ファイル*と呼びます。  
  
 リソース ファイルは、次のときに使用します。  
  
-   コンパイルしてアセンブリに組み込んだ後に、リソース ファイルのコンテンツを更新する必要がない。  
  
-   アプリケーション配布の複雑さを軽減するために、ファイルの依存関係の数を減らす必要がある。  
  
-   アプリケーション データ ファイルをローカライズ可能にする必要がある \(「[WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)」を参照\)。  
  
> [!NOTE]
>  ここで説明するリソース ファイルは [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md) で説明した埋め込まれるとは別の [アプリケーション リソースの管理 \(.NET\)](../Topic/Managing%20Application%20Resources%20\(.NET\).md) のリソース ファイルまたはリンク リソースとは異なります。  
  
### リソース ファイルの構成  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、リソース ファイルとは次に示すように [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] プロジェクトに `Resource` 項目としてインクルードされるファイルです。  
  
```  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] では、リソース ファイルを作成するにはファイルをプロジェクトに追加し、その `Build Action` を `Resource` に設定します。  
  
 プロジェクトをビルドするときに、[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] によってリソースがコンパイルされ、アセンブリに組み込まれます。  
  
### リソース ファイルの使用  
 リソース ファイルを読み込むには、<xref:System.Windows.Application> クラスの <xref:System.Windows.Application.GetResourceStream%2A> メソッドを呼び出し、目的のリソース ファイルを表すパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を渡します。  <xref:System.Windows.Application.GetResourceStream%2A> からは、<xref:System.Windows.Resources.StreamResourceInfo> オブジェクトが返されます。このオブジェクトによってリソース ファイルが <xref:System.IO.Stream> として公開され、そのコンテンツ タイプが記述されます。  
  
 次に示すコードの例では、<xref:System.Windows.Application.GetResourceStream%2A> を使用して <xref:System.Windows.Controls.Page> リソース ファイルを読み込み、<xref:System.Windows.Controls.Frame> \(`pageFrame`\) のコンテンツとして設定する方法を示します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <xref:System.Windows.Application.GetResourceStream%2A> を呼び出すと<xref:System.IO.Stream> にアクセスできますが、そのストリームを、設定に使用するプロパティの型に変換する追加作業が必要になります。  代わりに、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用して、コードでリソース ファイルをある型のプロパティに直接読み込むことによって <xref:System.IO.Stream> を開いたり変換したりできます。  
  
 次の例は、コードを使用して <xref:System.Windows.Controls.Page> を直接 <xref:System.Windows.Controls.Frame> \(`pageFrame`\) に読み込む方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### リソース ファイルとしてのアプリケーション コード ファイル  
 ウィンドウ、ページ、フロー ドキュメント、リソース ディクショナリなどのパッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を使用して参照できる、特殊な [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーション コード ファイルがあります。  たとえば、ウィンドウやページを参照するパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を使用して <xref:System.Windows.Application.StartupUri%2A?displayProperty=fullName> プロパティを設定すると、アプリケーションの起動時にそのウィンドウまたはページを読み込むことができます。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 これを実行できるのは、次に示すように [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルが [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] プロジェクトに `Page` 項目としてインクルードされている場合です。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] では、新しい <xref:System.Windows.Window>、<xref:System.Windows.Navigation.NavigationWindow>、<xref:System.Windows.Controls.Page>、<xref:System.Windows.Documents.FlowDocument>、または <xref:System.Windows.ResourceDictionary> をプロジェクトに追加したときの、マークアップ ファイルの `Build Action` の既定値は `Page` です。  
  
 `Page` 項目を持つプロジェクトがコンパイルされるときに、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 項目はバイナリ形式に変換され、コンパイルされて対応するアセンブリに組み込まれます。  したがって、これらのファイルは、通常のリソース ファイルと同様に使用できます。  
  
> [!NOTE]
>  `Resource` 項目として構成されている [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルに分離コード ファイルがない場合は、元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] をバイナリに変換したものではなく、元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] がコンパイルされてアセンブリに組み込まれます。  
  
<a name="Content_Files"></a>   
## コンテンツ ファイル  
 *コンテンツ ファイル*は、実行可能アセンブリと共に圧縮しないファイルとして配布されます。  コンテンツ ファイルはコンパイルされてアセンブリに組み込まれるのではありませんが、アセンブリのコンパイル時に、各コンテンツ ファイルとの関連付けを確立するメタデータが使用されます。  
  
 アプリケーションに必要な特定のアプリケーション データ ファイルが更新されても、そのファイルを使用するアセンブリを再コンパイルしなくて済むようにするには、コンテンツ ファイルを使用します。  
  
### コンテンツ ファイルの構成  
 コンテンツ ファイルをプロジェクトに追加するには、アプリケーション データ ファイルを `Content` 項目としてインクルードする必要があります。  さらに、コンテンツ ファイルはコンパイルされて直接アセンブリに組み込まれるものではないので、ビルド アセンブリからの相対的な場所にコンテンツ ファイルがコピーされることを指定するために [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]```CopyToOutputDirectory` メタデータ要素を設定する必要があります。  プロジェクトがビルドされるたびにビルド出力フォルダーにリソースがコピーされるようにするには、`CopyToOutputDirectory` メタデータ要素の設定値を `Always` とします。  それ以外の場合は、リソースの最新バージョンだけがビルド出力フォルダーにコピーされるように、`PreserveNewest` 値を使用して設定します。  
  
 次に示すファイルは、新しいバージョンのリソースがプロジェクトに追加された場合にのみビルド出力フォルダーにコピーされるコンテンツ ファイルとして構成されています。  
  
```  
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
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] では、コンテンツ ファイルを作成するにはファイルをプロジェクトに追加し、その `Build Action` を `Content` に設定します。また、`Copy to Output Directory` を `Copy always` \(`Always` と同じ\) および `Copy if newer` \(`PreserveNewest` と同じ\) に設定します。  
  
 プロジェクトがビルドされるときに、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 属性はコンパイルされて次のように各コンテンツ ファイルのアセンブリのメタデータとなります。  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 値の意味は、プロジェクト内のコンテンツ ファイルの位置を表す相対パスです。  たとえば、コンテンツ ファイルがプロジェクト サブフォルダー内にある場合は、追加のパス情報が次のように <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 値に組み込まれます。  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 値は、ビルド出力フォルダー内のコンテンツ ファイルへのパスの値でもあります。  
  
### コンテンツ ファイルの使用  
 コンテンツ ファイルを読み込むには、<xref:System.Windows.Application> クラスの <xref:System.Windows.Application.GetContentStream%2A> メソッドを呼び出し、目的のコンテンツ ファイルを表すパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を渡します。  <xref:System.Windows.Application.GetContentStream%2A> からは、<xref:System.Windows.Resources.StreamResourceInfo> オブジェクトが返されます。このオブジェクトによってコンテンツ ファイルが <xref:System.IO.Stream> として公開され、そのコンテンツ タイプが記述されます。  
  
 次に示すコードの例では、<xref:System.Windows.Application.GetContentStream%2A> を使用して <xref:System.Windows.Controls.Page> コンテンツ ファイルを読み込み、<xref:System.Windows.Controls.Frame> \(`pageFrame`\) のコンテンツとして設定する方法を示します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <xref:System.Windows.Application.GetContentStream%2A> を呼び出すと<xref:System.IO.Stream> にアクセスできますが、そのストリームを、設定に使用するプロパティの型に変換する追加作業が必要になります。  代わりに、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用して、コードでリソース ファイルをある型のプロパティに直接読み込むことによって <xref:System.IO.Stream> を開いたり変換したりできます。  
  
 次の例は、コードを使用して <xref:System.Windows.Controls.Page> を直接 <xref:System.Windows.Controls.Frame> \(`pageFrame`\) に読み込む方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## 起点サイト ファイル  
 リソース ファイルは、共に配布されるアセンブリとの間に明示的な関係を持っており、この関係は <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> で定義されます。  ただし、実際のアプリケーション開発では、アセンブリとアプリケーション データ ファイル間に暗黙的な関係を持たせる、あるいは関係を持たせないようにすることがあります。たとえば次のような場合です。  
  
-   コンパイル時にファイルが存在しない場合。  
  
-   アセンブリが必要とするファイルが、実行時までわからない場合。  
  
-   関連付けられているアセンブリを再コンパイルせずにファイルを更新できるようにする場合。  
  
-   オーディオやビデオなど大容量のデータ ファイルを使用するアプリケーションで、ユーザーが選択した場合にのみファイルがダウンロードされるようにする場合。  
  
 このような種類のファイルを、file:\/\/\/ スキームや http:\/\/ スキームなど、従来の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] スキームを使用して読み込むこともできます。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 ただし、file:\/\/\/ スキームや http:\/\/ スキームを使用する場合は、アプリケーションに完全信頼が必要です。  アプリケーションが、インターネットまたはイントラネットから起動された [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] であり、その場所から起動されたアプリケーションに対して許可されるアクセス許可のみをアプリケーションが要求する場合は、アプリケーションの起点サイト \(起動場所\) からのみ圧縮しないファイルを読み込むことができます。  このようなファイルを、*起点サイト ファイル*と呼びます。  
  
 起点サイト ファイルは部分信頼アプリケーションの唯一のオプションですが、部分信頼アプリケーション以外でも使用できます。  完全信頼アプリケーションでも、読み込むアプリケーション データ ファイルがビルド時点では不明な場合があります。完全信頼アプリケーションでは file:\/\/\/ を使用できますが、アプリケーション データ ファイルがアプリケーション アセンブリと同じフォルダーにインストールされることも、サブフォルダーにインストールされることも考えられます。  この場合は、起点サイト参照を使用する方が、file:\/\/\/ を使用するよりも簡単です。file:\/\/\/ を使用するには、ファイルの完全パスを指定する必要があるからです。  
  
> [!NOTE]
>  起点サイト ファイルは、コンテンツ ファイルとは異なり、クライアント コンピューターの [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] でキャッシュされません。  したがって、起点サイト ファイルは明確に要求されたときにのみダウンロードされます。  [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] アプリケーションで使用する大容量のメディア ファイルを起点サイト ファイルとして構成すると、アプリケーションの最初の起動時間が大幅に短縮され、ファイルは要求されたときにのみダウンロードされるようになります。  
  
### 起点サイト ファイルの構成  
 起点サイト ファイルがコンパイル時に存在しない場合や不明な場合は、従来の配置機構 \(`XCopy` コマンド ライン プログラム、[!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)] など\) を使用して、必要なファイルが実行時には使用可能になっているようにする必要があります。  
  
 起点サイトに配置されるファイルがコンパイル時にわかっているけれども、明示的な依存関係を持たせないようにするには、そのファイルを [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] プロジェクトに `None` 項目として追加します。  コンテンツ ファイルと同様に、[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] の `CopyToOutputDirectory` 属性を設定して、ビルド アセンブリからの相対位置に起点サイト ファイルがコピーされることを指定する必要があります。値は、`Always` または `PreserveNewest` を指定します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] では、起点サイト ファイルを作成するにはファイルをプロジェクトに追加し、その `Build Action` を `None` に設定します。  
  
 プロジェクトをビルドするときに、指定したファイルが [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] によってビルド出力フォルダーにコピーされます。  
  
### 起点サイト ファイルの使用  
 起点サイト ファイルを読み込むには、<xref:System.Windows.Application> クラスの <xref:System.Windows.Application.GetRemoteStream%2A> メソッドを呼び出し、目的の起点サイト ファイルを表すパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を渡します。  <xref:System.Windows.Application.GetRemoteStream%2A> からは、<xref:System.Windows.Resources.StreamResourceInfo> オブジェクトが返されます。このオブジェクトによって起点サイト ファイルが <xref:System.IO.Stream> として公開され、そのコンテンツ タイプが記述されます。  
  
 次に示すコードの例では、<xref:System.Windows.Application.GetRemoteStream%2A> を使用して <xref:System.Windows.Controls.Page> 起点サイト ファイルを読み込み、<xref:System.Windows.Controls.Frame> \(`pageFrame`\) のコンテンツとして設定する方法を示します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <xref:System.Windows.Application.GetRemoteStream%2A> を呼び出すと<xref:System.IO.Stream> にアクセスできますが、そのストリームを、設定に使用するプロパティの型に変換する追加作業が必要になります。  代わりに、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用して、コードでリソース ファイルをある型のプロパティに直接読み込むことによって <xref:System.IO.Stream> を開いたり変換したりできます。  
  
 次の例は、コードを使用して <xref:System.Windows.Controls.Page> を直接 <xref:System.Windows.Controls.Frame> \(`pageFrame`\) に読み込む方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## ビルド タイプ変更後の再ビルド  
 アプリケーション データ ファイルのビルド タイプを変更した後は、変更を確実に反映するためにアプリケーション全体を再ビルドする必要があります。  アプリケーションのみをビルドしても、変更は適用されません。  
  
## 参照  
 [WPF におけるパッケージの URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)