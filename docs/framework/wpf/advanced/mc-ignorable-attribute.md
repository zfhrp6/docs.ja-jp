---
title: "mc:Ignorable 属性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3be5949ee26fbb21d913a7aefe2664202c5bef38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="a234e-102">mc:Ignorable 属性</span><span class="sxs-lookup"><span data-stu-id="a234e-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="a234e-103">指定する[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]がマークアップ ファイルで発生した名前空間プレフィックスを無視する場合があります、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ。</span><span class="sxs-lookup"><span data-stu-id="a234e-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="a234e-104">`mc:Ignorable`属性は、カスタム名前空間のマッピングとのマークアップの互換性をサポートしている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]バージョン管理します。</span><span class="sxs-lookup"><span data-stu-id="a234e-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="a234e-105">XAML 属性の使用方法 (1 つのプレフィックス)</span><span class="sxs-lookup"><span data-stu-id="a234e-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="a234e-106">XAML 属性の使用方法 (2 つのプレフィックス)</span><span class="sxs-lookup"><span data-stu-id="a234e-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="a234e-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="a234e-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a234e-108">*ignorablePrefix、ignorablePrefix1 などです。*</span><span class="sxs-lookup"><span data-stu-id="a234e-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="a234e-109">有効なプレフィックス、任意の文字列、XML 1.0 仕様に準拠します。</span><span class="sxs-lookup"><span data-stu-id="a234e-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="a234e-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="a234e-110">*ignorableUri*</span></span>|<span data-ttu-id="a234e-111">XML 1.0 仕様あたり、名前空間を指定する有効な URI です。</span><span class="sxs-lookup"><span data-stu-id="a234e-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="a234e-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="a234e-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="a234e-113">要素が無視することができる[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]プロセッサの実装、基になる型は解決できない場合。</span><span class="sxs-lookup"><span data-stu-id="a234e-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a234e-114">コメント</span><span class="sxs-lookup"><span data-stu-id="a234e-114">Remarks</span></span>  
 <span data-ttu-id="a234e-115">`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]名前空間プレフィックスは、マッピング時に使用する、推奨されるプレフィックス規則、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]互換性名前空間[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="a234e-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="a234e-116">要素または属性として、要素名のプレフィックスの部分を識別する、`mc:Ignorable`によって処理されるときにエラーを生成しませんが、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ。</span><span class="sxs-lookup"><span data-stu-id="a234e-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="a234e-117">その属性を基になる型またはプログラミング構成要素を解決できませんでした、その要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="a234e-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="a234e-118">ただし、無視された要素が処理されていないその要素の副作用は、追加の要素の要件の追加の解析エラーを生成する可能性がありますも。</span><span class="sxs-lookup"><span data-stu-id="a234e-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="a234e-119">たとえば、特定の要素のコンテンツ モデル可能性がありますが必要なときに指定された子要素が 1 つの子要素、`mc:Ignorable`プレフィックス、および指定した子要素を型に解決できませんでした、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ可能性がありますエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a234e-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="a234e-120">`mc:Ignorable`識別子の文字列に名前空間のマッピングにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="a234e-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="a234e-121">`mc:Ignorable`名前空間のマッピングに指定のアセンブリには適用されません、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]名前空間とアセンブリ (または、現在の実行可能ファイル、アセンブリと既定)。</span><span class="sxs-lookup"><span data-stu-id="a234e-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="a234e-122">実装する場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ、プロセッサの実装する必要がありますいないを発生させる解析または任意の要素またはとして識別されるプレフィックスで修飾された属性の型解決についてのエラーを処理`mc:Ignorable`です。</span><span class="sxs-lookup"><span data-stu-id="a234e-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="a234e-123">プロセッサの実装の読み込みまたは前に示した例では、1 つの子要素などの処理に失敗している、要素のセカンダリの結果は、例外が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="a234e-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="a234e-124">既定では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ無視された要素内のコンテンツは無視されます。</span><span class="sxs-lookup"><span data-stu-id="a234e-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="a234e-125">ただし、追加の属性を指定できます[mc:ProcessContent 属性](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)、無視された要素を次の使用可能な親要素内のコンテンツの継続的な処理を要求するようにします。</span><span class="sxs-lookup"><span data-stu-id="a234e-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="a234e-126">たとえば、区切り記号として 1 つ以上の空白文字を使用して、属性に複数のプレフィックスを指定できます:`mc:Ignorable="ignore1 ignore2"`です。</span><span class="sxs-lookup"><span data-stu-id="a234e-126">Multiple prefixes can be specified in the attribute, using one or more whitespace characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  
  
 <span data-ttu-id="a234e-127">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]名前空間は、他の要素とのこの領域に記載されていない属性を定義、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="a234e-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="a234e-128">詳細については、次を参照してください。 [XML マークアップ互換性仕様](http://go.microsoft.com/fwlink/?LinkId=73824)です。</span><span class="sxs-lookup"><span data-stu-id="a234e-128">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a234e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a234e-129">See Also</span></span>  
 <xref:System.Windows.Markup.XamlReader>  
 [<span data-ttu-id="a234e-130">PresentationOptions:Freeze 属性</span><span class="sxs-lookup"><span data-stu-id="a234e-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [<span data-ttu-id="a234e-131">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="a234e-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="a234e-132">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="a234e-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
