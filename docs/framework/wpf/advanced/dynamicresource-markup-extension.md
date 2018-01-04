---
title: "DynamicResource のマークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f6c8500f9b9cd6d617789a2da3444519971ae81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="95dae-102">DynamicResource のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="95dae-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="95dae-103">いずれかの値を提供[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義されているリソースへの参照にするには、その値を遅らせることで、プロパティの属性です。</span><span class="sxs-lookup"><span data-stu-id="95dae-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="95dae-104">そのリソースに対する検索の動作は、実行時の参照に似ています。</span><span class="sxs-lookup"><span data-stu-id="95dae-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="95dae-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="95dae-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="95dae-106">XAML プロパティ要素の使用</span><span class="sxs-lookup"><span data-stu-id="95dae-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="95dae-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="95dae-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="95dae-108">要求されたリソースのキー。</span><span class="sxs-lookup"><span data-stu-id="95dae-108">The key for the requested resource.</span></span> <span data-ttu-id="95dae-109">によってこのキーに割り当てられた最初に、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)リソースがマークアップでは、作成されたまたはが指定されているかどうか、`key`パラメーターを呼び出すときに<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>リソースは、コードで作成された場合。</span><span class="sxs-lookup"><span data-stu-id="95dae-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95dae-110">コメント</span><span class="sxs-lookup"><span data-stu-id="95dae-110">Remarks</span></span>  
 <span data-ttu-id="95dae-111">A`DynamicResource`最初のコンパイル中に一時的な式を作成し、要求されたリソースの値が実際にオブジェクトを構築するために必要になるまで遅延リソースの参照。</span><span class="sxs-lookup"><span data-stu-id="95dae-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="95dae-112">後にこの可能性があります、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="95dae-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="95dae-113">リソースの値はに対する現在のページ範囲から始まるすべてのアクティブなリソース ディクショナリのキーの検索に基づくありコンパイルのプレース ホルダーの式と置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="95dae-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="95dae-114">依存関係プロパティの優先順位の観点から、`DynamicResource`式は、動的リソース参照が適用される位置に相当します。</span><span class="sxs-lookup"><span data-stu-id="95dae-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="95dae-115">プロパティを持っていたのローカル値を設定したかどうか、 `DynamicResource` 、ローカルの値として式、`DynamicResource`が完全に削除します。</span><span class="sxs-lookup"><span data-stu-id="95dae-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="95dae-116">詳細については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95dae-116">For details, see [Dependency Property Value Precedence](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="95dae-117">特定のリソース アクセスのシナリオに適した特に`DynamicResource`はなく、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)します。</span><span class="sxs-lookup"><span data-stu-id="95dae-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span> <span data-ttu-id="95dae-118">参照してください[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)、相対的な利点とパフォーマンスに及ぼす影響の詳細については`DynamicResource`と`StaticResource`です。</span><span class="sxs-lookup"><span data-stu-id="95dae-118">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="95dae-119">指定した<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>によって既存のリソースに対応する[X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)ページ、アプリケーション、使用可能なコントロールのテーマと外部リソースは、またはシステム リソースのいくつかのレベルで、リソースの検索は、その順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="95dae-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="95dae-120">静的および動的なリソースのリソースの検索の詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。</span><span class="sxs-lookup"><span data-stu-id="95dae-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="95dae-121">リソース キーの任意の文字列で定義されている可能性があります、 [XamlName の文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)です。</span><span class="sxs-lookup"><span data-stu-id="95dae-121">A resource key may be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="95dae-122">リソース キーもあります他のオブジェクトの種類など、<xref:System.Type>です。</span><span class="sxs-lookup"><span data-stu-id="95dae-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="95dae-123">A<xref:System.Type>キーがコントロールをテーマ スタイル設定するための基礎です。</span><span class="sxs-lookup"><span data-stu-id="95dae-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="95dae-124">詳しくは、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95dae-124">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]<span data-ttu-id="95dae-125">リソースの値の検索など<xref:System.Windows.FrameworkElement.FindResource%2A>で使用されると同じリソースの検索ロジックに従います`DynamicResource`です。</span><span class="sxs-lookup"><span data-stu-id="95dae-125"> for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="95dae-126">リソースを参照するための代替宣言的な手段は、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)します。</span><span class="sxs-lookup"><span data-stu-id="95dae-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="95dae-127">属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。</span><span class="sxs-lookup"><span data-stu-id="95dae-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="95dae-128">`DynamicResource` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 拡張クラスの <xref:System.Windows.DynamicResourceExtension> 値として割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="95dae-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="95dae-129">`DynamicResource`オブジェクトの要素の構文で使用できます。</span><span class="sxs-lookup"><span data-stu-id="95dae-129">`DynamicResource` can be used in object element syntax.</span></span> <span data-ttu-id="95dae-130">この例では、値を指定する、<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>プロパティは必須です。</span><span class="sxs-lookup"><span data-stu-id="95dae-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="95dae-131">`DynamicResource` は、<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="95dae-131">`DynamicResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="95dae-132">詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="95dae-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="95dae-133">`DynamicResource` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。</span><span class="sxs-lookup"><span data-stu-id="95dae-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="95dae-134">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装でこのマークアップ拡張機能の処理が定義されている、<xref:System.Windows.DynamicResourceExtension>クラスです。</span><span class="sxs-lookup"><span data-stu-id="95dae-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 <span data-ttu-id="95dae-135">`DynamicResource` はマークアップ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="95dae-135">`DynamicResource` is a markup extension.</span></span> <span data-ttu-id="95dae-136">一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。</span><span class="sxs-lookup"><span data-stu-id="95dae-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="95dae-137">すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{、}、規則は、それぞれの属性構文内の文字、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、マークアップ拡張機能が、属性を処理する必要がありますを認識します。</span><span class="sxs-lookup"><span data-stu-id="95dae-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="95dae-138">詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="95dae-138">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95dae-139">参照</span><span class="sxs-lookup"><span data-stu-id="95dae-139">See Also</span></span>  
 [<span data-ttu-id="95dae-140">XAML リソース</span><span class="sxs-lookup"><span data-stu-id="95dae-140">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="95dae-141">リソースとコード</span><span class="sxs-lookup"><span data-stu-id="95dae-141">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="95dae-142">x:Key ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="95dae-142">x:Key Directive</span></span>](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [<span data-ttu-id="95dae-143">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="95dae-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="95dae-144">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="95dae-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="95dae-145">StaticResource のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="95dae-145">StaticResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [<span data-ttu-id="95dae-146">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="95dae-146">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
