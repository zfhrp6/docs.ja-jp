---
title: "ComponentResourceKey マークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7f959318c5991fea2df92ff8000e85345fb35ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="b8a06-102">ComponentResourceKey マークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="b8a06-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="b8a06-103">定義し、外部アセンブリから読み込まれているリソースのキーを参照します。</span><span class="sxs-lookup"><span data-stu-id="b8a06-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="b8a06-104">これには、アセンブリまたはクラスでは、明示的なリソース ディクショナリではなく、アセンブリのターゲットの種類を指定するリソースの参照が使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8a06-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="b8a06-105">XAML 属性の使用 (設定キー、compact)</span><span class="sxs-lookup"><span data-stu-id="b8a06-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="b8a06-106">XAML 属性の使用方法の (設定キー、詳細)</span><span class="sxs-lookup"><span data-stu-id="b8a06-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="b8a06-107">XAML 属性の使用方法 (要求しているリソース、compact)</span><span class="sxs-lookup"><span data-stu-id="b8a06-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="b8a06-108">XAML 属性の使用 (リソース要求、詳細)</span><span class="sxs-lookup"><span data-stu-id="b8a06-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b8a06-109">XAML 値</span><span class="sxs-lookup"><span data-stu-id="b8a06-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="b8a06-110">パブリック名[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]リソース アセンブリに定義されている型。</span><span class="sxs-lookup"><span data-stu-id="b8a06-110">The name of the public [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="b8a06-111">リソースのキー。</span><span class="sxs-lookup"><span data-stu-id="b8a06-111">The key for the resource.</span></span> <span data-ttu-id="b8a06-112">リソースの問い合わせがあったときに`targetID`に似てなります、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)リソースのです。</span><span class="sxs-lookup"><span data-stu-id="b8a06-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8a06-113">コメント</span><span class="sxs-lookup"><span data-stu-id="b8a06-113">Remarks</span></span>  
 <span data-ttu-id="b8a06-114">使用法、上記のような {`ComponentResourceKey`} マークアップ拡張機能の使用が 2 つの場所が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="b8a06-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
-   <span data-ttu-id="b8a06-115">コントロールの作成者によって提供されるよう、テーマのリソース ディクショナリ内のキーの定義。</span><span class="sxs-lookup"><span data-stu-id="b8a06-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
-   <span data-ttu-id="b8a06-116">テーマ リソースにアクセスするアセンブリから、ときに、コントロール テンプレートを再設定が、コントロールのテーマによって提供されるリソースからのプロパティの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8a06-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="b8a06-117">テーマに由来するコンポーネントのリソースを参照するには、一般にお勧めを使用すること`{DynamicResource}`なく`{StaticResource}`です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="b8a06-118">これは、使用法に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8a06-118">This is shown in the usages.</span></span> <span data-ttu-id="b8a06-119">`{DynamicResource}`ユーザーがそれ自体のテーマを変更できるためお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b8a06-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="b8a06-120">コンポーネント リソース、テーマをサポートするためのコントロールの作成者の目的に最も一致する場合は、動的でもあるコンポーネント リソース参照を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a06-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="b8a06-121"><xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>リソースが実際に定義されているターゲット アセンブリに存在する型を識別します。</span><span class="sxs-lookup"><span data-stu-id="b8a06-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="b8a06-122">A`ComponentResourceKey`定義され、正確に知ることとは無関係に使用できる場所、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>定義されますが、最終的に参照されたアセンブリから型を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a06-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="b8a06-123">一般的な使用法<xref:System.Windows.ComponentResourceKey>クラスのメンバーとして、公開されているキーを定義することです。</span><span class="sxs-lookup"><span data-stu-id="b8a06-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="b8a06-124">この使用法を使用して、<xref:System.Windows.ComponentResourceKey>クラスのコンス トラクター、マークアップ拡張機能ではありません。</span><span class="sxs-lookup"><span data-stu-id="b8a06-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="b8a06-125">詳細については、次を参照してください。 <xref:System.Windows.ComponentResourceKey>、または、このトピックの"と参照するキーのテーマ リソースの定義"セクション[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="b8a06-126">属性構文は、一般に使用するキーを確立してを参照するキーを持つリソース、用、`ComponentResourceKey`マークアップ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="b8a06-127">Compact の構文に依存、<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>コンス トラクターのシグネチャと、マークアップ拡張機能の位置指定パラメーターの使用法。</span><span class="sxs-lookup"><span data-stu-id="b8a06-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="b8a06-128">順序、`targetTypeName`と`targetID`が指定されたことが重要です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="b8a06-129">冗語構文に依存、<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>既定のコンス トラクターとし、セット、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>と<xref:System.Windows.ComponentResourceKey.ResourceId%2A>ことが、オブジェクト要素の場合は true。 属性の構文に似ています。</span><span class="sxs-lookup"><span data-stu-id="b8a06-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> default constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="b8a06-130">詳細な構文では、プロパティが設定されている順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="b8a06-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="b8a06-131">リレーションシップとこれら 2 つの選択肢 (compact と詳細な) メカニズムが詳しく説明のトピックで[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="b8a06-132">値では技術的には、`targetID`任意のオブジェクト、文字列であることがないです。</span><span class="sxs-lookup"><span data-stu-id="b8a06-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="b8a06-133">WPF で最も一般的な使用法が位置を揃える、`targetID`値、文字列であるし、このような文字列はで有効な形式を[XamlName の文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="b8a06-134">`ComponentResourceKey`オブジェクトの要素の構文で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8a06-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="b8a06-135">この場合、両方の値を指定する、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>と<xref:System.Windows.ComponentResourceKey.ResourceId%2A>プロパティは、拡張機能を正しく初期化するために必要です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="b8a06-136">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]リーダー実装では、このマークアップ拡張機能の処理はによって定義された、<xref:System.Windows.ComponentResourceKey>クラスです。</span><span class="sxs-lookup"><span data-stu-id="b8a06-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="b8a06-137">`ComponentResourceKey` はマークアップ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="b8a06-138">一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="b8a06-139">すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{、}、規則は、それぞれの属性構文内の文字、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、マークアップ拡張機能が、属性を処理する必要がありますを認識します。</span><span class="sxs-lookup"><span data-stu-id="b8a06-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="b8a06-140">詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8a06-140">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a06-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8a06-141">See Also</span></span>  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="b8a06-142">コントロールの作成の概要</span><span class="sxs-lookup"><span data-stu-id="b8a06-142">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [<span data-ttu-id="b8a06-143">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="b8a06-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="b8a06-144">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="b8a06-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
