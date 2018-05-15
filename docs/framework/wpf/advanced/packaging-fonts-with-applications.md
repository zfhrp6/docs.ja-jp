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
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="92205-102">アプリケーションでのフォントのパッケージング</span><span class="sxs-lookup"><span data-stu-id="92205-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="92205-103">このトピックでは、パッケージで使用するフォントの方法の概要、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="92205-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92205-104">多くの種類のソフトウェアと同様に、フォント ファイルは、販売されるのではなくライセンスされます。</span><span class="sxs-lookup"><span data-stu-id="92205-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="92205-105">フォントの使用を管理するライセンス異なるベンダーが、一般にフォントをカバーするものを含め、ほとんどのライセンス[!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)]アプリケーションに提供し、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]フォントをアプリケーション内で埋め込みまたはそれ以外の場合に許可しません。再配布します。</span><span class="sxs-lookup"><span data-stu-id="92205-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] supplies with applications and [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="92205-106">したがって、開発者としては、フォントをアプリケーション内に埋め込む場合や別の方法でフォントを再頒布する場合、それらフォントに必要なライセンス権限を取得する責任があります。</span><span class="sxs-lookup"><span data-stu-id="92205-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="92205-107">フォントのパッケージングの概要</span><span class="sxs-lookup"><span data-stu-id="92205-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="92205-108">簡単にパッケージ化して、フォント内でリソースとして、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ベースのアプリケーションにユーザー インターフェイス テキストとその他の種類のテキストを表示するコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="92205-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="92205-109">フォントは、アプリケーションのアセンブリ ファイルと別にすることも、その中に埋め込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="92205-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="92205-110">アプリケーションから参照できる、リソース専用のフォント ライブラリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="92205-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]<span data-ttu-id="92205-111"> および[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]フォントにライセンスを埋め込むフォントのフォントの権限を示すすれば、型フラグが含まれています。</span><span class="sxs-lookup"><span data-stu-id="92205-111"> and [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="92205-112">しかし、この型フラグはドキュメントに格納された埋め込みフォントのみを参照し、アプリケーションに埋め込まれたフォントは参照しません。</span><span class="sxs-lookup"><span data-stu-id="92205-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="92205-113">作成することで、フォントの権利を埋め込むフォントを取得することができます、<xref:System.Windows.Media.GlyphTypeface>オブジェクトおよび参照するその<xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="92205-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="92205-114">「OS/2 および Windows メトリック」セクションを参照してください、 [OpenType 仕様](http://www.microsoft.com/typography/otspec/os2.htm)すればフラグについての詳細。</span><span class="sxs-lookup"><span data-stu-id="92205-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](http://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="92205-115">[Microsoft タイポグラフィ](http://www.microsoft.com/typography/links/)Web サイトには、特定のフォントの仕入先を検索またはカスタムの作業のフォントの製造元を検索するのに役立つ連絡先の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="92205-115">The [Microsoft Typography](http://www.microsoft.com/typography/links/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="92205-116">コンテンツ項目としてのフォントの追加</span><span class="sxs-lookup"><span data-stu-id="92205-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="92205-117">フォントは、アプリケーションのアセンブリ ファイルとは別のプロジェクト コンテンツ項目としてアプリケーションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="92205-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="92205-118">つまり、コンテンツ項目はアセンブリ内にリソースとして埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="92205-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="92205-119">コンテンツ項目を定義する方法を次のプロジェクト ファイル例に示します。</span><span class="sxs-lookup"><span data-stu-id="92205-119">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="92205-120">アプリケーションが実行時にフォントを使用できるようにするには、アプリケーションの展開ディレクトリでフォントをアクセス可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="92205-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="92205-121">`<CopyToOutputDirectory>`アプリケーションのプロジェクト ファイル内の要素では、ビルド処理中に、フォントをアプリケーションの配置ディレクトリに自動的にコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="92205-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="92205-122">展開ディレクトリにフォントをコピーする方法を次のプロジェクト ファイル例に示します。</span><span class="sxs-lookup"><span data-stu-id="92205-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="92205-123">次のコード例は、アプリケーションのフォントをコンテンツ項目として参照する方法を示しています。参照されるコンテンツ項目は、アプリケーションのアセンブリ ファイルと同じディレクトリ内に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92205-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="92205-124">リソース項目としてのフォントの追加</span><span class="sxs-lookup"><span data-stu-id="92205-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="92205-125">フォントは、アプリケーションのアセンブリ ファイルに埋め込まれたプロジェクト リソース項目としてアプリケーションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="92205-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="92205-126">リソース用として別のサブディレクトリを使用することは、アプリケーションのプロジェクト ファイルの整理に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="92205-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="92205-127">フォントを別サブディレクトリ内のリソース項目として定義する方法を、次のプロジェクト ファイル例に示します。</span><span class="sxs-lookup"><span data-stu-id="92205-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
>  <span data-ttu-id="92205-128">アプリケーションにリソースとしてフォントを追加するときを設定することを確認してください、`<Resource>`要素、および not、`<EmbeddedResource>`アプリケーションのプロジェクト ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="92205-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="92205-129">`<EmbeddedResource>`ビルド アクションの要素がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="92205-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="92205-130">アプリケーションのフォント リソースを参照する方法を次のマークアップ例に示します。</span><span class="sxs-lookup"><span data-stu-id="92205-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="92205-131">コードからのフォント リソース項目の参照</span><span class="sxs-lookup"><span data-stu-id="92205-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="92205-132">コードからフォント リソース項目を参照するためには、2 つの部分のフォント リソースへの参照を指定する必要があります。 基本[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; とフォントの場所の参照。</span><span class="sxs-lookup"><span data-stu-id="92205-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; and the font location reference.</span></span> <span data-ttu-id="92205-133">これらの値がのパラメーターとして使用される、<xref:System.Windows.Media.FontFamily.%23ctor%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="92205-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="92205-134">次のコード例と呼ばれるプロジェクトのサブディレクトリに、アプリケーションのフォントのリソースを参照する方法を示しています。`resources`です。</span><span class="sxs-lookup"><span data-stu-id="92205-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="92205-135">基本[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]フォント リソースが存在する、アプリケーションのサブディレクトリを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="92205-135">The base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="92205-136">この場合、フォントの場所の参照は、ディレクトリを指定する必要はありませんが、先頭を含める必要があります"`./`"、フォント リソースを示しますが、ベースで指定された同じディレクトリに[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="92205-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="92205-137">次のコード例は、フォント リソース項目を参照する別の方法を示しています。これは前のコード例と同等です。</span><span class="sxs-lookup"><span data-stu-id="92205-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="92205-138">同じアプリケーション サブディレクトリからのフォントの参照</span><span class="sxs-lookup"><span data-stu-id="92205-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="92205-139">アプリケーションのコンテンツとリソース ファイルは、アプリケーション プロジェクトのユーザー定義の同じサブディレクトリに配置できます。</span><span class="sxs-lookup"><span data-stu-id="92205-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="92205-140">同じサブディレクトリで定義されたコンテンツ ページとフォント リソースを次のプロジェクト ファイル例に示します。</span><span class="sxs-lookup"><span data-stu-id="92205-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="92205-141">アプリケーション コンテンツとフォントが同じサブディレクトリ内にあるので、フォント参照はアプリケーション コンテンツから見た相対参照となります。</span><span class="sxs-lookup"><span data-stu-id="92205-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="92205-142">次の例では、フォントがアプリケーションと同じディレクトリ内にある場合にアプリケーションのフォント リソースを参照する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="92205-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="92205-143">アプリケーションでのフォントの列挙</span><span class="sxs-lookup"><span data-stu-id="92205-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="92205-144">フォントを列挙する、アプリケーション内のリソース項目として、いずれかの操作を使用して、<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>または<xref:System.Windows.Media.Fonts.GetTypefaces%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="92205-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="92205-145">次の例を使用する方法を示しています、<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>のコレクションを返すメソッドを<xref:System.Windows.Media.FontFamily>アプリケーション フォントの場所からのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="92205-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="92205-146">ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="92205-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="92205-147">次の例を使用する方法を示しています、<xref:System.Windows.Media.Fonts.GetTypefaces%2A>のコレクションを返すメソッドを<xref:System.Windows.Media.Typeface>アプリケーション フォントの場所からのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="92205-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="92205-148">ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="92205-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="92205-149">フォント リソース ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="92205-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="92205-150">フォントのみを含むリソース専用ライブラリを作成できます。この種類のライブラリ プロジェクトにはコードは含まれません。</span><span class="sxs-lookup"><span data-stu-id="92205-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="92205-151">リソース専用ライブラリの作成は、リソースを使用するアプリケーション コードからリソースを切り離すための一般的な手法です。</span><span class="sxs-lookup"><span data-stu-id="92205-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="92205-152">また、これにより、複数のアプリケーション プロジェクトでこのライブラリ アセンブリを組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="92205-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="92205-153">次のプロジェクト ファイル例に、リソース専用ライブラリ プロジェクトの主要部分を示します。</span><span class="sxs-lookup"><span data-stu-id="92205-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="92205-154">リソース ライブラリ内のフォントの参照</span><span class="sxs-lookup"><span data-stu-id="92205-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="92205-155">アプリケーションからリソース ライブラリ内のフォントを参照するには、フォント参照の前にライブラリ アセンブリの名前を付加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92205-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="92205-156">ここでは、フォント リソース アセンブリは "FontLibrary" です。</span><span class="sxs-lookup"><span data-stu-id="92205-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="92205-157">アセンブリ名をアセンブリ内の参照と区切るために、';' 文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="92205-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="92205-158">キーワード "Component" の後にフォント名への参照を続けて追加すると、フォント ライブラリのリソースへの完全参照が完成します。</span><span class="sxs-lookup"><span data-stu-id="92205-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="92205-159">次のコード例では、リソース ライブラリ アセンブリ内のフォントを参照する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="92205-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  <span data-ttu-id="92205-160">この SDK には、サンプルのセットが含まれています。[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]とともに使用できるフォント[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="92205-160">This SDK contains a set of sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="92205-161">フォントはリソース専用ライブラリで定義されています。</span><span class="sxs-lookup"><span data-stu-id="92205-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="92205-162">詳細については、「[OpenType フォント パックのサンプル](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="92205-162">For more information, see [Sample OpenType Font Pack](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a><span data-ttu-id="92205-163">フォントの使用に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="92205-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="92205-164">次のリストは、パッケージおよび内のフォントの使用に関するいくつかの制限を説明[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="92205-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
-   <span data-ttu-id="92205-165">**フォント埋め込みアクセス許可ビット:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションはフォント埋め込みアクセス許可ビットのチェックも確認もしません。</span><span class="sxs-lookup"><span data-stu-id="92205-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="92205-166">参照してください、[パッケージングの概要フォント](#introduction_to_packaging_fonts)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="92205-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
-   <span data-ttu-id="92205-167">**配信元のフォントのサイト:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、http または ftp にフォントへの参照を許可しない[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="92205-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
-   <span data-ttu-id="92205-168">**パックを使用して絶対 URI: 表記:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション作成することはできません、<xref:System.Windows.Media.FontFamily>オブジェクトを使用してプログラムで"pack:"、絶対パスの一部として[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]フォントへの参照。</span><span class="sxs-lookup"><span data-stu-id="92205-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference to a font.</span></span> <span data-ttu-id="92205-169">たとえば、`"pack://application:,,,/resources/#Pericles Light"`無効なフォント参照します。</span><span class="sxs-lookup"><span data-stu-id="92205-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
-   <span data-ttu-id="92205-170">**自動フォント埋め込み:** デザイン時に、アプリケーションのフォントの使用を検索したり、アプリケーションのリソースにフォントを自動的に埋め込んだりすることはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="92205-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
-   <span data-ttu-id="92205-171">**フォント サブセット:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、固定ドキュメント以外でフォント サブセットの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="92205-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
-   <span data-ttu-id="92205-172">正しくない参照がある場合、アプリケーションは使用可能なフォントの使用に戻ります。</span><span class="sxs-lookup"><span data-stu-id="92205-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92205-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="92205-173">See Also</span></span>  
 <xref:System.Windows.Documents.Typography>  
 <xref:System.Windows.Media.FontFamily>  
 [<span data-ttu-id="92205-174">Microsoft の文字体裁: リンク、ニュース、および連絡先</span><span class="sxs-lookup"><span data-stu-id="92205-174">Microsoft Typography: Links, News, and Contacts</span></span>](http://www.microsoft.com/typography/links/)  
 [<span data-ttu-id="92205-175">OpenType の仕様</span><span class="sxs-lookup"><span data-stu-id="92205-175">OpenType Specification</span></span>](http://www.microsoft.com/typography/otspec/)  
 [<span data-ttu-id="92205-176">OpenType フォントの機能</span><span class="sxs-lookup"><span data-stu-id="92205-176">OpenType Font Features</span></span>](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [<span data-ttu-id="92205-177">OpenType フォント パックのサンプル</span><span class="sxs-lookup"><span data-stu-id="92205-177">Sample OpenType Font Pack</span></span>](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
