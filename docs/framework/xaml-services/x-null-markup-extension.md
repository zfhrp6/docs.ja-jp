---
title: x:Null のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: 94cfaee9a0a9a9f3892b9df50ac59103709a3b14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562350"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="d5ad3-102">x:Null のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="d5ad3-102">x:Null Markup Extension</span></span>
<span data-ttu-id="d5ad3-103">指定`null`XAML メンバーに対する値として。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="d5ad3-104">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="d5ad3-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="d5ad3-105">コメント</span><span class="sxs-lookup"><span data-stu-id="d5ad3-105">Remarks</span></span>  
 <span data-ttu-id="d5ad3-106">C# の場合は null 参照用のキーワードと[!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)]が null です。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-106">The keyword for a null reference in C# and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="d5ad3-107">Null 参照の Microsoft Visual Basic キーワードは、 `Nothing`、常に使用するが、 `{x:Null}` XAML の使用方法に関係なく、XAML と関連付けた分離コード言語として。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="d5ad3-108">`x:Null`マークアップ拡張機能には設定可能なプロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="d5ad3-109">Null の使用状況は、XAML メンバーの公開を CLR に関連付けられて多くの場合、<xref:System.Nullable%601>値。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="d5ad3-110">`x:Null`マークアップ拡張機能のすべての XAML マークアップ拡張機能と同様に、中かっこを使用して (`{,}`) 以外のリテラルまたはイベント ハンドラーの参照を属性値の処理をエスケープします。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="d5ad3-111">属性構文では、このマークアップ拡張機能で最も頻繁に使用される構文です。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="d5ad3-112">オブジェクトの要素の構文`<x:Null />`技術的に可能ですが、めったに使用されないため、`x:Null`マークアップ拡張機能には、位置指定パラメーター、または構築引数はありません。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="d5ad3-113">マークアップ拡張機能の概要については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="d5ad3-114">.NET Framework XAML サービスで、このマークアップ拡張機能の処理がによって定義された、<xref:System.Windows.Markup.NullExtension>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="d5ad3-115">WPF の使用上の注意</span><span class="sxs-lookup"><span data-stu-id="d5ad3-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="d5ad3-116">なお`null`必ずしも参照型の依存関係プロパティの初期設定されていない値ではありません。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="d5ad3-117">既定の初期値は、依存関係プロパティごとに異なることができ、プロパティ固有のメタデータに基づくことができます。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="d5ad3-118">多くの依存関係プロパティを受け入れない`null`マークアップまたはコードの検証コールバックの実装のための値として。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="d5ad3-119">依存関係プロパティの詳細については、次を参照してください。[依存関係プロパティの概要](../../../docs/framework/wpf/advanced/dependency-properties-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5ad3-119">For more information about dependency properties, see [Dependency Properties Overview](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ad3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5ad3-120">See Also</span></span>  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [<span data-ttu-id="d5ad3-121">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="d5ad3-121">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="d5ad3-122">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="d5ad3-122">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
