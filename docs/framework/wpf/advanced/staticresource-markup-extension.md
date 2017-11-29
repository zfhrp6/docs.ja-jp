---
title: "StaticResource のマークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 821cd152ccb7a02dda5338d6a3ec44d6625c0097
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="b3667-102">StaticResource のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="b3667-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="b3667-103">いずれかの値を提供[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義済みのリソースへの参照の検索プロパティの属性です。</span><span class="sxs-lookup"><span data-stu-id="b3667-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="b3667-104">そのリソースの検索動作が読み込み時の検索は、現在のマークアップから以前に読み込まれたリソースを検索に似ています[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]だけでなく、他のアプリケーションのソース ページし、としてそのリソースの値を生成します実行時のオブジェクトのプロパティ値です。</span><span class="sxs-lookup"><span data-stu-id="b3667-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b3667-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="b3667-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="b3667-106">XAML オブジェクト要素の使用方法</span><span class="sxs-lookup"><span data-stu-id="b3667-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b3667-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="b3667-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="b3667-108">要求されたリソースのキー。</span><span class="sxs-lookup"><span data-stu-id="b3667-108">The key for the requested resource.</span></span> <span data-ttu-id="b3667-109">によってこのキーに割り当てられた最初に、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)リソースがマークアップでは、作成されたまたはが指定されているかどうか、`key`パラメーターを呼び出すときに<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>リソースは、コードで作成された場合。</span><span class="sxs-lookup"><span data-stu-id="b3667-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3667-110">コメント</span><span class="sxs-lookup"><span data-stu-id="b3667-110">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3667-111">A`StaticResource`定義されているリソースへの前方参照を作成する必要がありますしない内で構文的にさらに、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル。</span><span class="sxs-lookup"><span data-stu-id="b3667-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="b3667-112">これを実行しようとすることはサポートされていませんと場合でも、このような参照は失敗しません前方参照しようとすると、パフォーマンスが低下ロード時間時を表す内部ハッシュ テーブル、<xref:System.Windows.ResourceDictionary>が検索されます。</span><span class="sxs-lookup"><span data-stu-id="b3667-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="b3667-113">最良の結果を前方参照を回避できるように、リソース ディクショナリの構成を調整します。</span><span class="sxs-lookup"><span data-stu-id="b3667-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="b3667-114">前方参照を回避することはできない場合を使用して[DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="b3667-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="b3667-115">指定した<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>で識別される、既存のリソースに対応する必要があります、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)ページ、アプリケーション、使用可能なコントロールのテーマと外部リソースは、またはシステム リソースのいくつかのレベルでします。</span><span class="sxs-lookup"><span data-stu-id="b3667-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="b3667-116">リソースの検索は、その順序で発生します。</span><span class="sxs-lookup"><span data-stu-id="b3667-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="b3667-117">静的および動的なリソースのリソースの検索の動作の詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3667-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="b3667-118">リソース キーは、任意の文字列で定義されている、 [XamlName の文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3667-118">A resource key can be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="b3667-119">リソース キーことができます、他のオブジェクトの種類など、<xref:System.Type>です。</span><span class="sxs-lookup"><span data-stu-id="b3667-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="b3667-120">A<xref:System.Type>キーがどのようにコントロール スタイルを設定できるのテーマで暗黙的なスタイル キーを使用するときの基礎です。</span><span class="sxs-lookup"><span data-stu-id="b3667-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="b3667-121">詳しくは、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3667-121">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="b3667-122">リソースを参照するための代替宣言的な手段は、 [DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)します。</span><span class="sxs-lookup"><span data-stu-id="b3667-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="b3667-123">属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。</span><span class="sxs-lookup"><span data-stu-id="b3667-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="b3667-124">`StaticResource` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 拡張クラスの <xref:System.Windows.StaticResourceExtension> 値として割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b3667-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="b3667-125">`StaticResource`オブジェクトの要素の構文で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b3667-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="b3667-126">この例では、値を指定する、<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>プロパティは必須です。</span><span class="sxs-lookup"><span data-stu-id="b3667-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="b3667-127">`StaticResource` は、<xref:System.Windows.StaticResourceExtension.ResourceKey%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="b3667-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="b3667-128">詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b3667-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="b3667-129">`StaticResource` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。</span><span class="sxs-lookup"><span data-stu-id="b3667-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="b3667-130">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装でこのマークアップ拡張機能の処理が定義されている、<xref:System.Windows.StaticResourceExtension>クラスです。</span><span class="sxs-lookup"><span data-stu-id="b3667-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="b3667-131">`StaticResource` はマークアップ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b3667-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="b3667-132">一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。</span><span class="sxs-lookup"><span data-stu-id="b3667-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="b3667-133">すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{、}、規則は、それぞれの属性構文内の文字、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、マークアップ拡張機能が、属性を処理する必要がありますを認識します。</span><span class="sxs-lookup"><span data-stu-id="b3667-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="b3667-134">詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3667-134">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3667-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3667-135">See Also</span></span>  
 [<span data-ttu-id="b3667-136">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="b3667-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="b3667-137">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="b3667-137">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="b3667-138">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="b3667-138">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="b3667-139">XAML リソース</span><span class="sxs-lookup"><span data-stu-id="b3667-139">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="b3667-140">リソースとコード</span><span class="sxs-lookup"><span data-stu-id="b3667-140">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)
