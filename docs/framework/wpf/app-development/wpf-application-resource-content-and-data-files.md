---
title: "WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 284c3b6788fd43a10d65cfa8bd6c032e4b1e1cd6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="e9fdd-102">WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル</span><span class="sxs-lookup"><span data-stu-id="e9fdd-102">WPF Application Resource, Content, and Data Files</span></span>
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]<span data-ttu-id="e9fdd-103">データを含む実行可能でないなどのファイルに多くの場合、依存するアプリケーション[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]イメージ、ビデオ、およびオーディオです。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-103"> applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]<span data-ttu-id="e9fdd-104"> には、アプリケーション データ ファイルと呼ばれるこれらの種類のデータ ファイルを構成、識別、および使用するための特殊なサポート機能があります。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-104"> offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="e9fdd-105">このサポートの中心となるのは、次のような特定のアプリケーション データ ファイルの種類のセットです。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
-   <span data-ttu-id="e9fdd-106">**リソース ファイル**: 実行可能ファイルまたはライブラリにコンパイルされるデータ ファイル[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-106">**Resource Files**: Data files that are compiled into either an executable or library [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
-   <span data-ttu-id="e9fdd-107">**コンテンツ ファイル**: スタンドアロンのデータ ファイルを実行可能ファイルとの明示的な関連付けを持つ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-107">**Content Files**: Standalone data files that have an explicit association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
-   <span data-ttu-id="e9fdd-108">**配信元のファイルのサイト**: スタンドアロンのデータ ファイルを実行可能ファイルとの関連付けを持たない[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-108">**Site of Origin Files**: Standalone data files that have no association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
 <span data-ttu-id="e9fdd-109">これらの 3 種類のファイルの重要な違いは、リソース ファイルとコンテンツ ファイルはビルド時に認識されるという点です。アセンブリは、これらを明確に認識します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="e9fdd-110">配信元のファイルのサイトのただし、アセンブリがあります認識したり、または暗黙的なナレッジ パックを[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]参照。 後者の場合の元のファイルの参照先のサイトが実際に存在するという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="e9fdd-111">アプリケーション データ ファイルを参照する[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]、パックを使用して[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]で詳しく説明されているスキーム[WPF のパック Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md))。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-111">To reference application data files, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] uses the Pack [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Scheme, which is described in detail in [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="e9fdd-112">このトピックでは、アプリケーション データ ファイルを構成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-112">This topic describes how to configure and use application data files.</span></span>  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a><span data-ttu-id="e9fdd-113">リソース ファイル (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="e9fdd-113">Resource Files</span></span>  
 <span data-ttu-id="e9fdd-114">アプリケーション データ ファイルを常にアプリケーションで使用可能にするには、コンパイルしてアプリケーションのメイン実行可能アセンブリまたはその参照アセンブリの 1 つに組み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="e9fdd-115">この種類のアプリケーション データ ファイルと呼ばれる、*リソース ファイル*です。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="e9fdd-116">リソース ファイルは、次のときに使用します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-116">You should use resource files when:</span></span>  
  
-   <span data-ttu-id="e9fdd-117">コンパイルしてアセンブリに組み込んだ後に、リソース ファイルのコンテンツを更新する必要がない。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
-   <span data-ttu-id="e9fdd-118">ファイルの依存関係の数を減らして、アプリケーション配布の複雑さを軽減する必要がある。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
-   <span data-ttu-id="e9fdd-119">アプリケーション データ ファイルをローカライズする必要があります (を参照してください[WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9fdd-120">このセクションで説明されているリソース ファイルは、リソース ファイルの記載と異なる[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)しで説明されている埋め込みまたはリンクされたリソースとは異なる[を管理するアプリケーションのリソース (.NET)](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).</span><span class="sxs-lookup"><span data-stu-id="e9fdd-120">The resource files described in this section are different than the resource files described in [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) and different than the embedded or linked resources described in [Managing Application Resources (.NET)](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="e9fdd-121">リソース ファイルの構成</span><span class="sxs-lookup"><span data-stu-id="e9fdd-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="e9fdd-122">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、リソース ファイルに含まれているファイルとは、[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]としてプロジェクト、`Resource`項目。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a resource file is a file that is included in an [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] project as a `Resource` item.</span></span>  
  
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
>  <span data-ttu-id="e9fdd-123">[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、ファイルをプロジェクトの設定を追加して、リソース ファイルを作成するその`Build Action`に`Resource`です。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-123">In [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="e9fdd-124">プロジェクトのビルド時に[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]アセンブリにリソースをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-124">When the project is built, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="e9fdd-125">リソース ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="e9fdd-125">Using Resource Files</span></span>  
 <span data-ttu-id="e9fdd-126">リソース ファイルを読み込むには、呼び出すことができます、<xref:System.Windows.Application.GetResourceStream%2A>のメソッド、<xref:System.Windows.Application>を渡して、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]目的のリソース ファイルを識別します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that identifies the desired resource file.</span></span> <span data-ttu-id="e9fdd-127"><xref:System.Windows.Application.GetResourceStream%2A>返します、<xref:System.Windows.Resources.StreamResourceInfo>として、リソース ファイルを公開するオブジェクト、<xref:System.IO.Stream>とそのコンテンツの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="e9fdd-128">たとえば、次のコードが使用する方法を示します<xref:System.Windows.Application.GetResourceStream%2A>を読み込む、<xref:System.Windows.Controls.Page>リソース ファイルのコンテンツとして設定し、 <xref:System.Windows.Controls.Frame> (`pageFrame`)。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="e9fdd-129">呼び出し中に<xref:System.Windows.Application.GetResourceStream%2A>にアクセスすること、<xref:System.IO.Stream>を設定します、プロパティの型への変換の追加の作業を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="e9fdd-130">代わりに、できる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の開始タグと変換するように注意、<xref:System.IO.Stream>直接コードを使用して型のプロパティにリソース ファイルを読み込む。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-130">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="e9fdd-131">次の例を読み込む方法を示しています、<xref:System.Windows.Controls.Page>に直接、 <xref:System.Windows.Controls.Frame> (`pageFrame`) コードを使用します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="e9fdd-132">次の例は、上の例と同じ意味のマークアップです。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="e9fdd-133">リソース ファイルとしてのアプリケーション コード ファイル</span><span class="sxs-lookup"><span data-stu-id="e9fdd-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="e9fdd-134">特殊な一連の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]パックを使用してアプリケーション コード ファイルを参照できる[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]windows、ページ、フロー ドキュメントのリソース ディクショナリなど、します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-134">A special set of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application code files can be referenced using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="e9fdd-135">たとえば、設定、<xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>のパック プロパティ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]ウィンドウまたはアプリケーションの起動時にロードしたいページを参照します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="e9fdd-136">場合に、このを行うことができます、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]でファイルが含まれています、[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]としてプロジェクト、`Page`項目。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-136">You can do this when a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is included in an [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] project as a `Page` item.</span></span>  
  
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
>  <span data-ttu-id="e9fdd-137">[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、追加<xref:System.Windows.Window>、 <xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.FlowDocument>、または<xref:System.Windows.ResourceDictionary>、プロジェクトに、`Build Action`マークアップのファイルは既定で`Page`です。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-137">In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="e9fdd-138">ときに使用したプロジェクトの`Page`項目をコンパイルすると、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目がバイナリ形式に変換され、関連するアセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="e9fdd-139">したがって、これらのファイルは、通常のリソース ファイルと同様に使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9fdd-140">場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]としてファイルが構成されている、`Resource`項目、および生の分離コード ファイルがない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は生のバイナリのバージョンではなく、アセンブリにコンパイルされて[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a><span data-ttu-id="e9fdd-141">コンテンツ ファイル</span><span class="sxs-lookup"><span data-stu-id="e9fdd-141">Content Files</span></span>  
 <span data-ttu-id="e9fdd-142">A*コンテンツ ファイル*と共に実行可能アセンブリの loose ファイルとして配布されます。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="e9fdd-143">コンテンツ ファイルはコンパイルされてアセンブリに組み込まれるのではありませんが、アセンブリのコンパイル時に、各コンテンツ ファイルとの関連付けを確立するメタデータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="e9fdd-144">アプリケーションに必要な特定のアプリケーション データ ファイルのセットが更新されても、そのファイルを使用するアセンブリを再コンパイルせずに、コンテンツ ファイルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="e9fdd-145">コンテンツ ファイルの構成</span><span class="sxs-lookup"><span data-stu-id="e9fdd-145">Configuring Content Files</span></span>  
 <span data-ttu-id="e9fdd-146">プロジェクトにコンテンツ ファイルを追加するには、アプリケーション データ ファイルとして含まれているにする必要があります、`Content`項目。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="e9fdd-147">さらに、コンテンツ ファイルがアセンブリに直接コンパイルされていないために設定する必要が、 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory`メタデータを指定する要素、コンテンツ ファイルがビルドされたアセンブリに対応する場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="e9fdd-148">プロジェクトがビルドされるたびに、ビルド出力フォルダーにコピーするリソースに該当する場合は、設定する、`CopyToOutputDirectory`メタデータ要素で、`Always`値。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="e9fdd-149">使用して、ビルド出力フォルダーに、リソースの最新のバージョンのみがコピーされることを確認するそれ以外の場合、`PreserveNewest`値。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="e9fdd-150">次に示すファイルは、新しいバージョンのリソースがプロジェクトに追加された場合にのみビルド出力フォルダーにコピーされるコンテンツ ファイルとして構成されています。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
>  <span data-ttu-id="e9fdd-151">[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、ファイルをプロジェクトの設定を追加して、コンテンツ ファイルを作成するその`Build Action`に`Content`、設定とその`Copy to Output Directory`に`Copy always`(と同じ`Always`) および`Copy if newer`(と同じ`PreserveNewest`)。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-151">In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="e9fdd-152">プロジェクトのビルド時に、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性は各コンテンツ ファイルのアセンブリのメタデータにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="e9fdd-153">値、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>プロジェクト内の位置に対してコンテンツのファイルへのパスを意味します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="e9fdd-154">たとえば、ある場合は、コンテンツ ファイルがプロジェクトのサブフォルダーに、追加パス情報に組み込む、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>値。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="e9fdd-155"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>値もビルド出力フォルダー内のコンテンツのファイルへのパスの値。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="e9fdd-156">コンテンツ ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="e9fdd-156">Using Content Files</span></span>  
 <span data-ttu-id="e9fdd-157">コンテンツ ファイルを読み込むには、呼び出すことができます、<xref:System.Windows.Application.GetContentStream%2A>のメソッド、<xref:System.Windows.Application>を渡して、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]目的のコンテンツ ファイルを識別します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that identifies the desired content file.</span></span> <span data-ttu-id="e9fdd-158"><xref:System.Windows.Application.GetContentStream%2A>返します、<xref:System.Windows.Resources.StreamResourceInfo>として、コンテンツ ファイルを公開するオブジェクト、<xref:System.IO.Stream>とそのコンテンツの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="e9fdd-159">たとえば、次のコードが使用する方法を示します<xref:System.Windows.Application.GetContentStream%2A>を読み込む、<xref:System.Windows.Controls.Page>ファイルのコンテンツのコンテンツとして設定し、 <xref:System.Windows.Controls.Frame> (`pageFrame`)。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="e9fdd-160">呼び出し中に<xref:System.Windows.Application.GetContentStream%2A>にアクセスすること、<xref:System.IO.Stream>を設定します、プロパティの型への変換の追加の作業を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="e9fdd-161">代わりに、できる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の開始タグと変換するように注意、<xref:System.IO.Stream>直接コードを使用して型のプロパティにリソース ファイルを読み込む。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-161">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="e9fdd-162">次の例を読み込む方法を示しています、<xref:System.Windows.Controls.Page>に直接、 <xref:System.Windows.Controls.Frame> (`pageFrame`) コードを使用します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="e9fdd-163">次の例は、上の例と同じ意味のマークアップです。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a><span data-ttu-id="e9fdd-164">起点サイト ファイル</span><span class="sxs-lookup"><span data-stu-id="e9fdd-164">Site of Origin Files</span></span>  
 <span data-ttu-id="e9fdd-165">リソース ファイルがによって定義された、と共に配布されるアセンブリとの明示的なリレーションシップを持つ、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>です。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="e9fdd-166">ただし、アセンブリとアプリケーション データ ファイル間に暗黙的な関係を持たせる、または関係を持たせない場合があります。たとえば次のような場合です。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
-   <span data-ttu-id="e9fdd-167">コンパイル時にファイルが存在しない場合。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-167">A file doesn't exist when at compile time.</span></span>  
  
-   <span data-ttu-id="e9fdd-168">アセンブリが必要とするファイルが、実行時までわからない場合。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-168">You don't know what files your assembly will require until run time.</span></span>  
  
-   <span data-ttu-id="e9fdd-169">関連付けられているアセンブリを再コンパイルせずにファイルを更新可能にする場合。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
-   <span data-ttu-id="e9fdd-170">オーディオやビデオなど大容量のデータ ファイルを使用するアプリケーションで、ユーザーが選択した場合にのみファイルをダウンロードする場合。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="e9fdd-171">これらの種類を使用して従来のファイルの読み込みが可能である[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]file:/// http:// 方式などのスキーム。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-171">It is possible to load these types of files by using traditional [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="e9fdd-172">ただし、file:/// スキームや http:// スキームを使用する場合は、アプリケーションに完全信頼が必要です。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="e9fdd-173">アプリケーションの場合、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]ですが、インターネットまたはイントラネットから起動して、ルース ファイルしか読み込めません原点 (アプリケーションのサイトからこれらの場所から起動したアプリケーションで許可される権限のセットのみを要求場所の起動)。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-173">If your application is a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="e9fdd-174">このようなファイルと呼びます*元のサイト*ファイル。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="e9fdd-175">起点サイト ファイルは部分信頼アプリケーションの唯一のオプションですが、部分信頼アプリケーション以外でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="e9fdd-176">完全信頼アプリケーションでも、読み込むアプリケーション データ ファイルがビルド時点では不明な場合があります。完全信頼アプリケーションでは file:/// を使用できますが、アプリケーション データ ファイルがアプリケーション アセンブリと同じフォルダーにインストールされることも、サブフォルダーにインストールされることも考えられます。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="e9fdd-177">この場合は、起点サイト参照を使用する方が、file:/// を使用するよりも簡単です。file:/// を使用するには、ファイルの完全パスを指定する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9fdd-178">ファイルがキャッシュされていない元のサイト、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]をクライアント コンピューターは、コンテンツ ファイルの中でします。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-178">Site of origin files are not cached with an [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] on a client machine, while content files are.</span></span> <span data-ttu-id="e9fdd-179">したがって、起点サイト ファイルは明確に要求されたときにのみダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="e9fdd-180">場合、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]アプリケーションが大規模なメディア ファイルをサイト元ファイルの初期のアプリケーションの起動がはるかに高速、および要求時にファイルのダウンロードのみの手段として構成することです。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-180">If an [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="e9fdd-181">起点サイト ファイルの構成</span><span class="sxs-lookup"><span data-stu-id="e9fdd-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="e9fdd-182">従来の配置を使用する必要がある場合は、サイトの元のファイルの存在しないまたは不明なコンパイル時に、いずれかの使用など、実行時に、必要なファイルを確保するための機構を使用できます、`XCopy`コマンド ライン プログラムや、 [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9fdd-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].</span></span>  
  
 <span data-ttu-id="e9fdd-183">わかっている場合はコンパイル時にファイルを元のサイトに配置されるけれどもまだ明示的な依存関係を回避するにそれらのファイルを追加することができます、[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]としてプロジェクト`None`項目。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] project as `None` item.</span></span> <span data-ttu-id="e9fdd-184">コンテンツのファイルで設定する必要がある、 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory`元のファイルのサイトがいずれかを指定することによってビルドされたアセンブリに対応する場所にコピーされていることを指定する属性、`Always`値または`PreserveNewest`値。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-184">As with content files, you need to set the [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
>  <span data-ttu-id="e9fdd-185">[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、ファイルをプロジェクトの設定を追加して元のファイルのサイトを作成するその`Build Action`に`None`です。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-185">In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="e9fdd-186">プロジェクトのビルド時に[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]ビルド出力フォルダーに指定されたファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-186">When the project is built, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="e9fdd-187">起点サイト ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="e9fdd-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="e9fdd-188">元のファイルのサイトを読み込むには、呼び出すことができます、<xref:System.Windows.Application.GetRemoteStream%2A>のメソッド、<xref:System.Windows.Application>を渡して、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]元のファイルの目的のサイトを識別します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that identifies the desired site of origin file.</span></span> <span data-ttu-id="e9fdd-189"><xref:System.Windows.Application.GetRemoteStream%2A>返します、<xref:System.Windows.Resources.StreamResourceInfo>として元のファイルのサイトを公開するオブジェクト、<xref:System.IO.Stream>とそのコンテンツの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="e9fdd-190">例として、次のコードが使用する方法を示します<xref:System.Windows.Application.GetRemoteStream%2A>を読み込む、<xref:System.Windows.Controls.Page>元のサイトのコンテンツとして設定し、ファイル、 <xref:System.Windows.Controls.Frame> (`pageFrame`)。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="e9fdd-191">呼び出し中に<xref:System.Windows.Application.GetRemoteStream%2A>にアクセスすること、<xref:System.IO.Stream>を設定します、プロパティの型への変換の追加の作業を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="e9fdd-192">代わりに、できる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の開始タグと変換するように注意、<xref:System.IO.Stream>直接コードを使用して型のプロパティにリソース ファイルを読み込む。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-192">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="e9fdd-193">次の例を読み込む方法を示しています、<xref:System.Windows.Controls.Page>に直接、 <xref:System.Windows.Controls.Frame> (`pageFrame`) コードを使用します。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="e9fdd-194">次の例は、上の例と同じ意味のマークアップです。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="e9fdd-195">ビルドの種類を変更した後のリビルド</span><span class="sxs-lookup"><span data-stu-id="e9fdd-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="e9fdd-196">アプリケーション データ ファイルのビルドの種類を変更した後は、変更を確実に反映するためにアプリケーション全体をリビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="e9fdd-197">アプリケーションのみをビルドしても、変更は適用されません。</span><span class="sxs-lookup"><span data-stu-id="e9fdd-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9fdd-198">参照</span><span class="sxs-lookup"><span data-stu-id="e9fdd-198">See Also</span></span>  
 [<span data-ttu-id="e9fdd-199">WPF におけるパッケージの URI</span><span class="sxs-lookup"><span data-stu-id="e9fdd-199">Pack URIs in WPF</span></span>](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
