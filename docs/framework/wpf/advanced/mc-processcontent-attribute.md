---
title: mc:ProcessContent 属性
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 2e93734b8ab4aefca080736db3a512f272625271
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545254"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="82191-102">mc:ProcessContent 属性</span><span class="sxs-lookup"><span data-stu-id="82191-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="82191-103">指定する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素必要がありますもコンテンツがある関連する親要素によって処理される場合でも、直接の親要素を無視できます、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサを指定することにより[mc: Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="82191-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span></span> <span data-ttu-id="82191-104">`mc:ProcessContent`属性は、カスタム名前空間のマッピングとのマークアップの互換性をサポートしている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]バージョン管理します。</span><span class="sxs-lookup"><span data-stu-id="82191-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="82191-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="82191-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="82191-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="82191-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82191-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="82191-107">*ignorablePrefix*</span></span>|<span data-ttu-id="82191-108">有効なプレフィックス、任意の文字列、XML 1.0 仕様に準拠します。</span><span class="sxs-lookup"><span data-stu-id="82191-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="82191-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="82191-109">*ignorableUri*</span></span>|<span data-ttu-id="82191-110">XML 1.0 仕様あたり、名前空間を指定する有効な URI です。</span><span class="sxs-lookup"><span data-stu-id="82191-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="82191-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="82191-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="82191-112">要素が無視することができる[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]プロセッサの実装、基になる型は解決できない場合。</span><span class="sxs-lookup"><span data-stu-id="82191-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="82191-113">*[コンテンツ]*</span><span class="sxs-lookup"><span data-stu-id="82191-113">*[content]*</span></span>|<span data-ttu-id="82191-114">*ThisElementCanBeIgnored*無視とマークされています。</span><span class="sxs-lookup"><span data-stu-id="82191-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="82191-115">プロセッサが、その要素を無視する場合 *[コンテンツ]* によって処理される*オブジェクト*です。</span><span class="sxs-lookup"><span data-stu-id="82191-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82191-116">コメント</span><span class="sxs-lookup"><span data-stu-id="82191-116">Remarks</span></span>  
 <span data-ttu-id="82191-117">既定では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ無視された要素内のコンテンツは無視されます。</span><span class="sxs-lookup"><span data-stu-id="82191-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="82191-118">特定の要素を指定できます`mc:ProcessContent`、および[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサが無視された要素内のコンテンツの処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="82191-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="82191-119">これは通常される使用、コンテンツがいくつかのタグ、うち少なくとも 1 つが無視できるとうち少なくとも 1 つは無視内で入れ子になった場合。</span><span class="sxs-lookup"><span data-stu-id="82191-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="82191-120">たとえば、スペース区切り記号を使用して、属性に複数のプレフィックスを指定できます:`mc:ProcessContent="ignore:Element1 ignore:Element2"`です。</span><span class="sxs-lookup"><span data-stu-id="82191-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="82191-121">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]名前空間は、他の要素とのこの領域に記載されていない属性を定義、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="82191-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="82191-122">詳細については、次を参照してください。 [XML マークアップ互換性仕様](http://go.microsoft.com/fwlink/?LinkId=73824)です。</span><span class="sxs-lookup"><span data-stu-id="82191-122">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82191-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="82191-123">See Also</span></span>  
 [<span data-ttu-id="82191-124">mc:Ignorable 属性</span><span class="sxs-lookup"><span data-stu-id="82191-124">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [<span data-ttu-id="82191-125">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="82191-125">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
