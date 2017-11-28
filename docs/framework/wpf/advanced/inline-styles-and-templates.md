---
title: "インライン スタイルおよびテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2acb455db8f8bdc5a95bfd2462b651cebbb692c3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="9fa23-102">インライン スタイルおよびテンプレート</span><span class="sxs-lookup"><span data-stu-id="9fa23-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="9fa23-103">提供<xref:System.Windows.Style>オブジェクトとテンプレートのオブジェクト (<xref:System.Windows.FrameworkTemplate>サブクラス)、リソースで要素の外観を定義する手段として使用できるように複数回です。</span><span class="sxs-lookup"><span data-stu-id="9fa23-103"> provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="9fa23-104">このため、属性で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]型を受け取る<xref:System.Windows.Style>と<xref:System.Windows.FrameworkTemplate>新しいものをインラインで定義するのではなく、ほとんどの場合の既存のスタイルとテンプレートにリソース参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="9fa23-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="9fa23-105">インライン スタイルとテンプレートの制限事項</span><span class="sxs-lookup"><span data-stu-id="9fa23-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="9fa23-106">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]スタイルとテンプレートのプロパティは、2 つの方法のいずれかで技術的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="9fa23-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="9fa23-107">たとえば、リソース内で定義されたスタイルを参照する属性の構文を使用できます`<`*オブジェクト*`Style="{StaticResource`*myResourceKey*`}" .../>`です。</span><span class="sxs-lookup"><span data-stu-id="9fa23-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="9fa23-108">または、スタイルをインラインのインスタンスを定義するプロパティ要素構文を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9fa23-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="9fa23-109">`<`*object*`>`</span><span class="sxs-lookup"><span data-stu-id="9fa23-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="9fa23-110">`<`*object*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="9fa23-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="9fa23-111">`<` `Style`  `.../>`</span><span class="sxs-lookup"><span data-stu-id="9fa23-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="9fa23-112">`</`*object*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="9fa23-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="9fa23-113">`</`*object*`>`</span><span class="sxs-lookup"><span data-stu-id="9fa23-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="9fa23-114">属性の使用方法は、はるかに一般的です。</span><span class="sxs-lookup"><span data-stu-id="9fa23-114">The attribute usage is much more common.</span></span> <span data-ttu-id="9fa23-115">インラインで定義され、リソースではない定義でスタイルを含む要素のみを対象とするとは限りません、再使用できませんように簡単にリソース キーがあるないためです。</span><span class="sxs-lookup"><span data-stu-id="9fa23-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="9fa23-116">一般にリソース定義のスタイル汎用性と、有用であり、一般的な高く[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]プログラミング モデルの方針のマークアップでのデザイン コードでのプログラム ロジックを分離することです。</span><span class="sxs-lookup"><span data-stu-id="9fa23-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="9fa23-117">通常必要はありませんスタイルまたはテンプレートのインラインを設定する場合でも、その場所にそのスタイルまたはテンプレートを使用するだけです。</span><span class="sxs-lookup"><span data-stu-id="9fa23-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="9fa23-118">スタイルまたはテンプレートが実行できるほとんどの要素は、コンテンツのプロパティとコンテンツ モデルもサポートします。</span><span class="sxs-lookup"><span data-stu-id="9fa23-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="9fa23-119">論理ツリーをのみを使用している場合は、1 回スタイルまたはテンプレートで作成するは、さらに簡単に直接的なマークアップでの同等の子要素のコンテンツ プロパティを塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="9fa23-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="9fa23-120">これは、バイパス スタイルとテンプレート メカニズム完全します。</span><span class="sxs-lookup"><span data-stu-id="9fa23-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="9fa23-121">オブジェクトを返すマークアップ拡張機能を有効になっている他の構文もスタイルとテンプレートの考えられます。</span><span class="sxs-lookup"><span data-stu-id="9fa23-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="9fa23-122">可能なシナリオがあるこのような 2 つの拡張機能を含める[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)と<xref:System.Windows.Data.Binding>です。</span><span class="sxs-lookup"><span data-stu-id="9fa23-122">Two such extensions that have possible scenarios include [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa23-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fa23-123">See Also</span></span>  
 [<span data-ttu-id="9fa23-124">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="9fa23-124">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
