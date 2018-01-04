---
title: "x:Shared 属性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9cc5e2bff9cc2591c7a12630da5422dbf73713a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xshared-attribute"></a><span data-ttu-id="21a4b-102">x:Shared 属性</span><span class="sxs-lookup"><span data-stu-id="21a4b-102">x:Shared Attribute</span></span>
<span data-ttu-id="21a4b-103">設定すると`false`、WPF リソース検索の動作を変更して、属性付きのリソースに対して要求が、同じインスタンスのすべての要求を共有することがなく各要求の新しいインスタンスを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="21a4b-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="21a4b-104">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="21a4b-104">XAML Attribute Usage</span></span>  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a><span data-ttu-id="21a4b-105">コメント</span><span class="sxs-lookup"><span data-stu-id="21a4b-105">Remarks</span></span>  
 <span data-ttu-id="21a4b-106">`x:Shared`XAML 言語の XAML 名前空間にマップされは、.NET Framework XAML サービスおよびその XAML リーダーによって、有効な XAML 言語要素として認識します。</span><span class="sxs-lookup"><span data-stu-id="21a4b-106">`x:Shared` is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET Framework XAML Services and its XAML readers.</span></span> <span data-ttu-id="21a4b-107">ただし、示された機能`x:Shared`WPF アプリケーションと WPF XAML パーサーは、関連するだけです。</span><span class="sxs-lookup"><span data-stu-id="21a4b-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="21a4b-108">WPF では、`x:Shared`は WPF 内に存在するオブジェクトに適用された場合のみ、属性として使用<xref:System.Windows.ResourceDictionary>です。</span><span class="sxs-lookup"><span data-stu-id="21a4b-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="21a4b-109">他の使用法は解析例外やその他のエラーをスローしませんが、効果はありません。</span><span class="sxs-lookup"><span data-stu-id="21a4b-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>  
  
 <span data-ttu-id="21a4b-110">意味`x:Shared`XAML 言語仕様で指定されていません。</span><span class="sxs-lookup"><span data-stu-id="21a4b-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="21a4b-111">.NET Framework XAML サービスに基づいて構築されるなど、他の XAML 実装は、必ずしもリソース共有のサポートを提供しません。</span><span class="sxs-lookup"><span data-stu-id="21a4b-111">Other XAML implementations, such as those that build on .NET Framework XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="21a4b-112">このような XAML 実装でも使用されているサポート framework で同様の動作を提供できます`x:Shared`値。</span><span class="sxs-lookup"><span data-stu-id="21a4b-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>  
  
 <span data-ttu-id="21a4b-113">WPF では、既定値`x:Shared`リソースに対する`true`です。</span><span class="sxs-lookup"><span data-stu-id="21a4b-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="21a4b-114">この条件は、任意の特定のリソース要求が同じインスタンスを常を返すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="21a4b-114">This condition means that any given resource request always returns the same instance.</span></span>  
  
 <span data-ttu-id="21a4b-115">など、API、リソースを使用して返されるオブジェクトを変更した<xref:System.Windows.FrameworkElement.FindResource%2A>、内で直接オブジェクトを変更するか、 <xref:System.Windows.ResourceDictionary>、元のリソースを変更します。</span><span class="sxs-lookup"><span data-stu-id="21a4b-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="21a4b-116">そのリソースへの参照が動的リソース参照と、そのリソースの消費者は、変更されたリソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="21a4b-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>  
  
 <span data-ttu-id="21a4b-117">リソースへの参照が、静的リソース参照、に対する変更により、リソース[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]処理時間は、関係ありません。</span><span class="sxs-lookup"><span data-stu-id="21a4b-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="21a4b-118">動的リソース参照と静的の詳細については、次を参照してください。 [XAML リソース](../../../docs/framework/wpf/advanced/xaml-resources.md)です。</span><span class="sxs-lookup"><span data-stu-id="21a4b-118">For more information about static versus dynamic resource references, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="21a4b-119">明示的に指定する`x:Shared="true"`はあまり一般的には、既定ではないためです。</span><span class="sxs-lookup"><span data-stu-id="21a4b-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="21a4b-120">直接コードに相当`x:Shared`WPF でオブジェクト モデルこれは、XAML の使用方法を指定するだけ処理する必要が既定の WPF 動作するか、読み込みパスでの中間の XAML ノード ストリームで .NET Framework XAML Se を使用して処理する場合。ターゲット、およびその XAML リーダー。</span><span class="sxs-lookup"><span data-stu-id="21a4b-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET Framework XAML Services and its XAML readers.</span></span>  
  
 <span data-ttu-id="21a4b-121">シナリオ`x:Shared="false"`定義するかどうかは、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>リソースとしてのクラスを派生し、コンテンツ モデルに要素のリソースを導入します。</span><span class="sxs-lookup"><span data-stu-id="21a4b-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> <span data-ttu-id="21a4b-122">`x:Shared="false"`複数回、同じコレクションに導入する、要素のリソースを有効に (など、 <xref:System.Windows.Controls.UIElementCollection>)。</span><span class="sxs-lookup"><span data-stu-id="21a4b-122">`x:Shared="false"` enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="21a4b-123">せず`x:Shared="false"`これは無効なコレクションには、その内容の一意性が強制されるためです。</span><span class="sxs-lookup"><span data-stu-id="21a4b-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="21a4b-124">ただし、`x:Shared="false"`動作は同じインスタンスを返す代わりに、リソースの別の同一インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="21a4b-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>  
  
 <span data-ttu-id="21a4b-125">別のシナリオとして`x:Shared="false"`を使用するかどうか、<xref:System.Windows.Freezable>アニメーション値がアニメーションあたりごとにリソースを変更するリソース。</span><span class="sxs-lookup"><span data-stu-id="21a4b-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>  
  
 <span data-ttu-id="21a4b-126">文字列の処理`false`大文字小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="21a4b-126">The string handling of `false` is not case sensitive.</span></span>  
  
 <span data-ttu-id="21a4b-127">WPF では、`x:Shared`のみ、次の条件下で有効です。</span><span class="sxs-lookup"><span data-stu-id="21a4b-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>  
  
-   <span data-ttu-id="21a4b-128"><xref:System.Windows.ResourceDictionary>で項目を含む`x:Shared`コンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="21a4b-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="21a4b-129"><xref:System.Windows.ResourceDictionary> Loose XAML 内にすることはできませんまたはテーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="21a4b-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>  
  
-   <span data-ttu-id="21a4b-130"><xref:System.Windows.ResourceDictionary> 、項目を含む他の中で入れ子にする必要がありますいない<xref:System.Windows.ResourceDictionary>です。</span><span class="sxs-lookup"><span data-stu-id="21a4b-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="21a4b-131">たとえば、使用することはできません`x:Shared`内のアイテム、<xref:System.Windows.ResourceDictionary>内にある、<xref:System.Windows.Style>にではない、<xref:System.Windows.ResourceDictionary>項目。</span><span class="sxs-lookup"><span data-stu-id="21a4b-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a4b-132">参照</span><span class="sxs-lookup"><span data-stu-id="21a4b-132">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 [<span data-ttu-id="21a4b-133">XAML リソース</span><span class="sxs-lookup"><span data-stu-id="21a4b-133">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="21a4b-134">基本要素</span><span class="sxs-lookup"><span data-stu-id="21a4b-134">Base Elements</span></span>](../../../docs/framework/wpf/advanced/base-elements.md)
