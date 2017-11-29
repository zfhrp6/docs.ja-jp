---
title: "XAML 名前空間および WPF XAML の名前空間の割り当て"
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
- custom classes [WPF], mapping namespaces to
- XAML [WPF], namespaces
- namespace mapping [WPF]
- assemblies [WPF], mapping namespaces to
- mapping namespaces [WPF]
- XAML [WPF], namespace mapping
- classes [WPF], mapping namespaces to
- namespaces [WPF]
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2798659d3b53cb32af8e5976d4fee69780266633
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a><span data-ttu-id="19b48-102">XAML 名前空間および WPF XAML の名前空間の割り当て</span><span class="sxs-lookup"><span data-stu-id="19b48-102">XAML Namespaces and Namespace Mapping for WPF XAML</span></span>
<span data-ttu-id="19b48-103">さらに、このトピックでは、存在と WPF XAML ファイルのルート タグにある多くの場合、2 つの XAML 名前空間のマッピングの目的について説明します。</span><span class="sxs-lookup"><span data-stu-id="19b48-103">This topic further explains the presence and purpose of the two XAML namespace mappings as often found in the root tag of a WPF XAML file.</span></span> <span data-ttu-id="19b48-104">独自のコード内や個別のアセンブリ内で定義されている要素を使用するためのようなマッピングを生成する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="19b48-104">It also describes how to produce similar mappings for using elements that are defined in your own code, and/or within separate assemblies.</span></span>  
  
  
## <a name="what-is-a-xaml-namespace"></a><span data-ttu-id="19b48-105">XAML Namespace とは何ですか。</span><span class="sxs-lookup"><span data-stu-id="19b48-105">What is a XAML Namespace?</span></span>  
 <span data-ttu-id="19b48-106">XAML 名前空間は、実際には、XML 名前空間の概念の拡張です。</span><span class="sxs-lookup"><span data-stu-id="19b48-106">A XAML namespace is really an extension of the concept of an XML namespace.</span></span> <span data-ttu-id="19b48-107">XAML 名前空間を指定するための手法を使用して、XML 名前空間の構文、Uri を使用して、同じのマークアップのソースから複数の名前空間を参照する手段を提供するプレフィックスを使用して、名前空間の識別子としての規約に依存して、。</span><span class="sxs-lookup"><span data-stu-id="19b48-107">The techniques of specifying a XAML namespace rely on the XML namespace syntax, the convention of using URIs as namespace identifiers, using prefixes to provide a means to reference multiple namespaces from the same markup source, and so on.</span></span> <span data-ttu-id="19b48-108">XML 名前空間の XAML 定義に追加される主要な概念は XAML 名前空間が両方の一意性のスコープ マークアップの使用を意味し、マークアップのエンティティが可能性のある特定の CLR 名前空間によってバックアップされ参照方法にも影響アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="19b48-108">The primary concept that is added to the XAML definition of the XML namespace is that a XAML namespace implies both a scope of uniqueness for the markup usages, and also influences how markup entities are potentially backed by specific CLR namespaces and referenced assemblies.</span></span> <span data-ttu-id="19b48-109">後者の考慮事項は、XAML スキーマ コンテキストの概念の影響も受けます。</span><span class="sxs-lookup"><span data-stu-id="19b48-109">This latter consideration is also influenced by the concept of a XAML schema context.</span></span> <span data-ttu-id="19b48-110">XAML 名前空間での WPF の連携のため、こともできる一般に既定の XAML 名前空間、言語の XAML 名前空間、および、さらに XAML 名前空間として特定のバッキング CLR に直接、XAML マークアップでマップされている面での XAML 名前空間の名前空間と参照先アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="19b48-110">But for purposes of how WPF works with XAML namespaces, you can generally think of XAML namespaces in terms of a default XAML namespace, the XAML language namespace, and any further XAML namespaces as mapped by your XAML markup directly to specific backing CLR namespaces and referenced assemblies.</span></span>  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a><span data-ttu-id="19b48-111">WPF および XAML Namespace 宣言</span><span class="sxs-lookup"><span data-stu-id="19b48-111">The WPF and XAML Namespace Declarations</span></span>  
 <span data-ttu-id="19b48-112">多くの XAML ファイルのルート タグである名前空間宣言内では、2 つの XML 名前空間宣言が通常表示されます。</span><span class="sxs-lookup"><span data-stu-id="19b48-112">Within the namespace declarations in the root tag of many XAML files, you will see that there are typically two XML namespace declarations.</span></span> <span data-ttu-id="19b48-113">最初の宣言では、マップ全体の WPF クライアント/既定値としてフレームワークの XAML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="19b48-113">The first declaration maps the overall WPF client / framework XAML namespace as the default:</span></span>  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 <span data-ttu-id="19b48-114">2 番目の宣言 (通常) にマップすること、別の XAML 名前空間をマップする、`x:`プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="19b48-114">The second declaration maps a separate XAML namespace, mapping it (typically) to the `x:` prefix.</span></span>  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 <span data-ttu-id="19b48-115">これらの宣言の間のリレーションシップは、`x:`プレフィックスのマッピングは、XAML 言語の定義の一部である組み込みをサポートしていると[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]言語としての XAML を使用しのボキャブラリを定義する 1 つの実装は、そのXAML のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="19b48-115">The relationship between these declarations is that the `x:` prefix mapping supports the intrinsics that are part of the XAML language definition, and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] is one implementation that uses XAML as a language and defines a vocabulary of its objects for XAML.</span></span> <span data-ttu-id="19b48-116">あるため、WPF ボキャブラリの使用法が XAML の組み込みの使用方法よりもはるかに一般的、WPF ボキャブラリは、既定値としてマップされます。</span><span class="sxs-lookup"><span data-stu-id="19b48-116">Because the WPF vocabulary's usages will be far more common than the XAML intrinsics usages, the WPF vocabulary is mapped as the default.</span></span>  
  
 <span data-ttu-id="19b48-117">`x:`プレフィックス規約のプロジェクト テンプレートの後に、XAML 言語の組み込みサポートをマッピングするサンプル コード、および言語のドキュメントの機能[!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="19b48-117">The `x:` prefix convention for mapping the XAML language intrinsics support is followed by project templates, sample code, and the documentation of language features within this [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)].</span></span> <span data-ttu-id="19b48-118">XAML 名前空間では、基本的な WPF アプリケーションにも必要なは一般的に使用される多くの機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="19b48-118">The XAML namespace defines many commonly-used features that are necessary even for basic WPF  applications.</span></span> <span data-ttu-id="19b48-119">たとえば、分離コードを部分クラスを使用して XAML ファイルを結合するのに名前を付けてとそのクラス、`x:Class`関連する XAML ファイルのルート要素の属性です。</span><span class="sxs-lookup"><span data-stu-id="19b48-119">For instance, in order to join any code-behind to a XAML file through a partial class, you must name that class as the `x:Class` attribute in the root element of the relevant XAML file.</span></span> <span data-ttu-id="19b48-120">または、キー付きのリソースには、アクセスする XAML ページで定義されているいずれかの要素、`x:Key`属性が「対象の要素に設定します。</span><span class="sxs-lookup"><span data-stu-id="19b48-120">Or, any element as defined in a XAML page that you wish to access as a keyed resource should have the `x:Key` attribute set on the element in question.</span></span> <span data-ttu-id="19b48-121">これらおよびその他の XAML の詳細については「 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)または[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)です。</span><span class="sxs-lookup"><span data-stu-id="19b48-121">For more information on these and other aspects of XAML see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) or [XAML Syntax In Detail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a><span data-ttu-id="19b48-122">カスタム クラスやアセンブリへのマッピング</span><span class="sxs-lookup"><span data-stu-id="19b48-122">Mapping to Custom Classes and Assemblies</span></span>  
 <span data-ttu-id="19b48-123">XML 名前空間をマップするには、一連の内のトークンを使用してアセンブリを`xmlns`プレフィックス宣言、プレフィックスを標準的な WPF と XAML 組み込み XAML 名前空間をマップする方法に似ています。</span><span class="sxs-lookup"><span data-stu-id="19b48-123">You can map XML namespaces to assemblies using a series of tokens within an `xmlns` prefix declaration, similar to how the standard WPF and XAML-intrinsics XAML namespaces are mapped to prefixes.</span></span>  
  
 <span data-ttu-id="19b48-124">構文には、次の名前のトークンと次の値。</span><span class="sxs-lookup"><span data-stu-id="19b48-124">The syntax takes the following possible named tokens and following values:</span></span>  
  
 <span data-ttu-id="19b48-125">`clr-namespace:`CLR 名前空間は要素として公開するパブリック型を格納するアセンブリ内で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="19b48-125">`clr-namespace:` The CLR namespace declared within the assembly that contains the public types to expose as elements.</span></span>  
  
 <span data-ttu-id="19b48-126">`assembly=`参照先の一部またはすべてを含むアセンブリ[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]名前空間。</span><span class="sxs-lookup"><span data-stu-id="19b48-126">`assembly=` The assembly that contains some or all of the referenced [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace.</span></span> <span data-ttu-id="19b48-127">この値は、パスではなく、アセンブリの名前だけでは通常、(.dll または .exe) など、拡張機能は含まれません。</span><span class="sxs-lookup"><span data-stu-id="19b48-127">This value is typically just the name of the assembly, not the path, and does not include the extension (such as .dll or .exe).</span></span> <span data-ttu-id="19b48-128">マップしようとして XAML を含むプロジェクト ファイル内のプロジェクト参照としては、そのアセンブリへのパスを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b48-128">The path to that assembly must be established as a project reference in the project file that contains the XAML you are trying to map.</span></span> <span data-ttu-id="19b48-129">バージョン管理とを厳密な名前の署名を反映するために、`assembly`値で定義されている文字列であることができます<xref:System.Reflection.AssemblyName>、単純な文字列名ではなくです。</span><span class="sxs-lookup"><span data-stu-id="19b48-129">In order to incorporate versioning and strong-name signing, the `assembly` value can be a string as defined by <xref:System.Reflection.AssemblyName>, rather than the simple string name.</span></span>  
  
 <span data-ttu-id="19b48-130">文字を分離することに注意してください、`clr-namespace`値からトークンがありますが、コロン (:) 文字の分離、`assembly`値からトークンが等号 (=)。</span><span class="sxs-lookup"><span data-stu-id="19b48-130">Note that the character separating the `clr-namespace` token from its value is a colon (:) whereas the character separating the `assembly` token from its value is an equals sign (=).</span></span> <span data-ttu-id="19b48-131">これら 2 つのトークンの間で使用する文字は、セミコロンです。</span><span class="sxs-lookup"><span data-stu-id="19b48-131">The character to use between these two tokens is a semicolon.</span></span> <span data-ttu-id="19b48-132">またの空白任意の場所に含めない宣言します。</span><span class="sxs-lookup"><span data-stu-id="19b48-132">Also, do not include any whitespace anywhere in the declaration.</span></span>  
  
### <a name="a-basic-custom-mapping-example"></a><span data-ttu-id="19b48-133">基本的なカスタム マッピング例</span><span class="sxs-lookup"><span data-stu-id="19b48-133">A Basic Custom Mapping Example</span></span>  
 <span data-ttu-id="19b48-134">次のコードでは、サンプルのカスタム クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="19b48-134">The following code defines an example custom class:</span></span>  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 <span data-ttu-id="19b48-135">その後、このカスタム クラスは、プロジェクトの設定 (非表示) と呼ばれる、ライブラリにコンパイル`SDKSampleLibrary`です。</span><span class="sxs-lookup"><span data-stu-id="19b48-135">This custom class is then compiled into a library, which per the project settings (not shown) is named `SDKSampleLibrary`.</span></span>  
  
 <span data-ttu-id="19b48-136">このカスタム クラスを参照するようにする必要がありますは、現在のプロジェクトへの参照として含める Visual Studio のソリューション エクスプ ローラーの UI を使用します。</span><span class="sxs-lookup"><span data-stu-id="19b48-136">In order to reference this custom class, you also need to include it as a reference for your current project, which you would typically do using the Solution Explorer UI in Visual Studio.</span></span>  
  
 <span data-ttu-id="19b48-137">これで、クラス、およびプロジェクトの設定への参照を含むライブラリがある場合は、XAML のルート要素の一部として次のプレフィックスのマッピングを追加できます。</span><span class="sxs-lookup"><span data-stu-id="19b48-137">Now that you have a library containing a class, and a reference to it in project settings, you can add the following prefix mapping as part of your root element in XAML:</span></span>  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 <span data-ttu-id="19b48-138">すべて同時に言うと、ルート タグに、一般的な既定値と共にカスタム マッピングおよび x: マッピングが含まれていますし、プレフィックス付きの参照を使用してインスタンス化する XAML を次に示します`ExampleClass`その UI で。</span><span class="sxs-lookup"><span data-stu-id="19b48-138">To put it all together, the following is XAML that includes the custom mapping along with the typical default and x: mappings in the root tag, then uses a prefixed reference to instantiate `ExampleClass` in that UI:</span></span>  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### <a name="mapping-to-current-assemblies"></a><span data-ttu-id="19b48-139">現在のアセンブリへのマッピング</span><span class="sxs-lookup"><span data-stu-id="19b48-139">Mapping to Current Assemblies</span></span>  
 <span data-ttu-id="19b48-140">`assembly`場合は省略可能、`clr-namespace`参照先は、カスタム クラスを参照しているアプリケーション コードと同じアセンブリ内で定義されています。</span><span class="sxs-lookup"><span data-stu-id="19b48-140">`assembly` can be omitted if the `clr-namespace` referenced is being defined within the same assembly as the application code that is referencing the custom classes.</span></span> <span data-ttu-id="19b48-141">この場合の同等の構文を指定するか、 `assembly=`、なし文字列トークンを等号の後にします。</span><span class="sxs-lookup"><span data-stu-id="19b48-141">Or, an equivalent syntax for this case is to specify `assembly=`, with no string token following the equals sign.</span></span>  
  
 <span data-ttu-id="19b48-142">カスタム クラスは、同じアセンブリで定義されている場合は、ページのルート要素として使用できません。</span><span class="sxs-lookup"><span data-stu-id="19b48-142">Custom classes cannot be used as the root element of a page if defined in the same assembly.</span></span> <span data-ttu-id="19b48-143">部分クラスが割り当てる必要はありません。アプリケーションが必要となる xaml 要素として参照する場合にマップするページの部分クラスではないクラスのみです。</span><span class="sxs-lookup"><span data-stu-id="19b48-143">Partial classes do not need to be mapped; only classes that are not the partial class of a page in your application need to be mapped if you intend to reference them as elements in XAML.</span></span>  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a><span data-ttu-id="19b48-144">アセンブリ内の XML 名前空間への CLR 名前空間のマッピング</span><span class="sxs-lookup"><span data-stu-id="19b48-144">Mapping CLR Namespaces to XML Namespaces in an Assembly</span></span>  
 <span data-ttu-id="19b48-145">WPF では、単一の XAML 名前空間に複数の CLR 名前空間をマップするために、XAML プロセッサによって使用される CLR 属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="19b48-145">WPF defines a CLR attribute that is consumed by XAML processors in order to map multiple CLR namespaces to a single XAML namespace.</span></span> <span data-ttu-id="19b48-146">この属性は、<xref:System.Windows.Markup.XmlnsDefinitionAttribute>アセンブリを生成するソース コードにアセンブリ レベルで配置されます。</span><span class="sxs-lookup"><span data-stu-id="19b48-146">This attribute, <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, is placed at the assembly level in the source code that produces the assembly.</span></span> <span data-ttu-id="19b48-147">WPF アセンブリのソース コードでは、この属性を使用して、、さまざまな一般的な名前空間をマップ<xref:System.Windows>と<xref:System.Windows.Controls>を[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]名前空間。</span><span class="sxs-lookup"><span data-stu-id="19b48-147">The WPF assembly source code uses this attribute to map the various common namespaces, such as <xref:System.Windows> and <xref:System.Windows.Controls>, to the [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] namespace.</span></span>  
  
 <span data-ttu-id="19b48-148"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> 2 つのパラメーター: XML と XAML 名前空間の名前と CLR 名前空間の名前。</span><span class="sxs-lookup"><span data-stu-id="19b48-148">The <xref:System.Windows.Markup.XmlnsDefinitionAttribute> takes two parameters: the XML/XAML namespace name, and the CLR namespace name.</span></span> <span data-ttu-id="19b48-149">1 つ以上<xref:System.Windows.Markup.XmlnsDefinitionAttribute>同じ XML 名前空間に複数の CLR 名前空間をマップする存在できます。</span><span class="sxs-lookup"><span data-stu-id="19b48-149">More than one <xref:System.Windows.Markup.XmlnsDefinitionAttribute> can exist to map multiple CLR namespaces to the same XML namespace.</span></span> <span data-ttu-id="19b48-150">マップされると、それらの名前空間のメンバーも参照できます完全修飾せず、適切な提供することによって必要な場合は`using`部分クラスの分離コード ページ内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="19b48-150">Once mapped, members of those namespaces can also be referenced without full qualification if desired by providing the appropriate `using` statement in the partial-class code-behind page.</span></span> <span data-ttu-id="19b48-151">詳細については、「<xref:System.Windows.Markup.XmlnsDefinitionAttribute>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b48-151">For more details, see <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span></span>  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a><span data-ttu-id="19b48-152">デザイナーの名前空間と XAML テンプレートから他のプレフィックス</span><span class="sxs-lookup"><span data-stu-id="19b48-152">Designer Namespaces and Other Prefixes From XAML Templates</span></span>  
 <span data-ttu-id="19b48-153">XAML の WPF の開発環境やデザイン ツールを使用している、する可能性がありますがわかりますがある他の定義済みの XAML 名前空間プレフィックスの XAML マークアップで/です。</span><span class="sxs-lookup"><span data-stu-id="19b48-153">If you are working with development environments and/or design tools for WPF XAML, you may notice that there are other defined XAML namespaces / prefixes within the XAML markup.</span></span>  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]<span data-ttu-id="19b48-154">通常、プレフィックスにマップされるデザイナー名前空間を使用して`d:`です。</span><span class="sxs-lookup"><span data-stu-id="19b48-154"> uses a designer namespace that is typically mapped to the prefix `d:`.</span></span> <span data-ttu-id="19b48-155">WPF のプロジェクト テンプレートをより新しい場合があります、XAML との間のやり取りをサポートするためにこの XAML 名前空間をマップして事前[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]およびその他のデザイン環境です。</span><span class="sxs-lookup"><span data-stu-id="19b48-155">More recent project templates for WPF might pre-map this XAML namespace to support interchange of the XAML between [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] and other design environments.</span></span> <span data-ttu-id="19b48-156">この設計の XAML 名前空間は、ラウンドト リップ、デザイナーで XAML ベースの UI の中にデザインの状態を永続化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="19b48-156">This design XAML namespace is used to perpetuate design state while roundtripping XAML-based UI in the designer.</span></span> <span data-ttu-id="19b48-157">使用機能のように`d:IsDataSource`デザイナーでデータ ソースのランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="19b48-157">It is also used for features such as `d:IsDataSource`, which enable runtime data sources in a designer.</span></span>  
  
 <span data-ttu-id="19b48-158">マップされている別のプレフィックスが表示されて`mc:`です。</span><span class="sxs-lookup"><span data-stu-id="19b48-158">Another prefix you might see mapped is `mc:`.</span></span> <span data-ttu-id="19b48-159">`mc:`マークアップ互換性のためと、必ずしも XAML に固有ではないマークアップ互換性パターンを活用することができます。</span><span class="sxs-lookup"><span data-stu-id="19b48-159">`mc:` is for markup compatibility, and is leveraging a markup compatibility pattern that is not necessarily XAML-specific.</span></span> <span data-ttu-id="19b48-160">ある程度はマークアップ互換性フレームワーク間またはその他の境界、補助的な実装の間で XAML を交換する機能を使用することができます XAML スキーマ コンテキスト間で作業デザイナーでは、制限付きのモードの互換性を提供され、します。</span><span class="sxs-lookup"><span data-stu-id="19b48-160">To some extent, the markup compatibility features can be used to exchange XAML between frameworks or across other boundaries of backing implementation, work between XAML schema contexts, provide compatibility for limited modes in designers, and so on.</span></span> <span data-ttu-id="19b48-161">マークアップ互換性概念と WPF に関連付ける方法の詳細については、次を参照してください[マークアップの互換性 (mc:)。言語機能](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md)します。</span><span class="sxs-lookup"><span data-stu-id="19b48-161">For more information on markup compatibility concepts and how they relate to WPF, see  [Markup Compatibility (mc:) Language Features](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md).</span></span>  
  
## <a name="wpf-and-assembly-loading"></a><span data-ttu-id="19b48-162">WPF およびアセンブリの読み込み</span><span class="sxs-lookup"><span data-stu-id="19b48-162">WPF and Assembly Loading</span></span>  
 <span data-ttu-id="19b48-163">WPF の XAML スキーマ コンテキスト 'æ˜aœg' の CLR で定義された概念を順番に使用して、WPF アプリケーション モデル、<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="19b48-163">The XAML schema context for WPF integrates with the WPF application model, which in turn uses the CLR-defined concept of <xref:System.AppDomain>.</span></span> <span data-ttu-id="19b48-164">次の順序は、XAML スキーマ コンテキストがアセンブリを読み込むかの WPF の使用状況に基づいて実行時またはデザイン時に、型を検出する方法をどのように解釈する方法について説明します<xref:System.AppDomain>およびその他の要因です。</span><span class="sxs-lookup"><span data-stu-id="19b48-164">The following sequence describes how XAML schema context interprets how to either load assemblies or find types at run time or design time, based on the WPF use of <xref:System.AppDomain> and other factors.</span></span>  
  
1.  <span data-ttu-id="19b48-165">反復処理する、<xref:System.AppDomain>名前のすべての側面に一致する読み込み済みアセンブリを探して、読み込まれたアセンブリを最も最近から開始します。</span><span class="sxs-lookup"><span data-stu-id="19b48-165">Iterate through the <xref:System.AppDomain>, looking for an already-loaded assembly that matches all aspects of the name, starting from the most recently loaded assembly.</span></span>  
  
2.  <span data-ttu-id="19b48-166">名前修飾する場合は、呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名にします。</span><span class="sxs-lookup"><span data-stu-id="19b48-166">If the name is qualified, call <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> on the qualified name.</span></span>  
  
3.  <span data-ttu-id="19b48-167">短い名前と修飾名の公開キー トークンは、マークアップから読み込まれたアセンブリに一致すると、そのアセンブリを返します。</span><span class="sxs-lookup"><span data-stu-id="19b48-167">If the short name + public key token of a qualified name matches the assembly that the markup was loaded from, return that assembly.</span></span>  
  
4.  <span data-ttu-id="19b48-168">短い名前と公開キー トークンを使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="19b48-168">Use the short name + public key token to call <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.</span></span>  
  
5.  <span data-ttu-id="19b48-169">名前が修飾されていない場合は、呼び出す<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="19b48-169">If the name is unqualified, call <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="19b48-170">Loose XAML は、手順 3; を使用しません読み込まれたアセンブリが存在しません。</span><span class="sxs-lookup"><span data-stu-id="19b48-170">Loose XAML does not use Step 3; there is no loaded-from assembly.</span></span>  
  
 <span data-ttu-id="19b48-171">WPF (XamlBuildTask を経由して生成される) にコンパイルされた XAML がから既に読み込まれているアセンブリを使用していない<xref:System.AppDomain>(ステップ 1)。</span><span class="sxs-lookup"><span data-stu-id="19b48-171">Compiled XAML for WPF (generated via XamlBuildTask) does not use the already-loaded assemblies from <xref:System.AppDomain> (Step 1).</span></span> <span data-ttu-id="19b48-172">また、名前する必要がありますしない XamlBuildTask 出力から修飾されていないため、手順 5 が適用されません。</span><span class="sxs-lookup"><span data-stu-id="19b48-172">Also, the name should never be unqualified from XamlBuildTask output, so Step 5 does not apply.</span></span>  
  
 <span data-ttu-id="19b48-173">BAML も含めることはできませんの非修飾アセンブリ名が、コンパイル済みの BAML (PresentationBuildTask 経由で生成) はすべての手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="19b48-173">Compiled BAML (generated via PresentationBuildTask) uses all steps, although BAML also should not contain unqualified assembly names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b48-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="19b48-174">See Also</span></span>  
 [<span data-ttu-id="19b48-175">XML 名前空間を理解します。</span><span class="sxs-lookup"><span data-stu-id="19b48-175">Understanding XML Namespaces</span></span>](http://go.microsoft.com/fwlink/?LinkId=98069)  
 [<span data-ttu-id="19b48-176">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="19b48-176">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
