---
title: "XAML 2009 言語機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 447ba37330e8027d86fd24239a8aca2461dce8d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-2009-language-features"></a><span data-ttu-id="5be76-102">XAML 2009 言語機能</span><span class="sxs-lookup"><span data-stu-id="5be76-102">XAML 2009 Language Features</span></span>
<span data-ttu-id="5be76-103">XAML 2009 とは、既存の XAML 言語仕様を拡張した、XAML の新しい言語機能の短縮名です。</span><span class="sxs-lookup"><span data-stu-id="5be76-103">XAML 2009 is the shorthand term for new XAML language features that extend the existing XAML language specification.</span></span> <span data-ttu-id="5be76-104">XAML 2009 には、いくつかの新しいディレクティブとコンストラクトが導入されています。</span><span class="sxs-lookup"><span data-stu-id="5be76-104">XAML 2009 introduces several new directives and constructs.</span></span> <span data-ttu-id="5be76-105">たとえば、[x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md)、 [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md)、 [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md)、 [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)、共通言語プリミティブの組み込み型 ( `x:Char`など) があります。</span><span class="sxs-lookup"><span data-stu-id="5be76-105">These include the[x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md); the [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md); the [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md); the [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md); and built-in types for common language primitives (for example `x:Char`).</span></span>  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a><span data-ttu-id="5be76-106">XAML 2009 は、WPF および Visual Studio でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5be76-106">XAML 2009 Support in WPF and Visual Studio</span></span>  
 <span data-ttu-id="5be76-107">WPF では XAML 2009 の機能を使用できますが、WPF マークアップ コンパイルされていない XAML に限定されます。</span><span class="sxs-lookup"><span data-stu-id="5be76-107">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="5be76-108">マークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 言語のキーワードと機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5be76-108">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>  
  
 <span data-ttu-id="5be76-109">なお、WPF に Loose XAML を読み込むための既存の方法には、CLR 型および型システムに対するセキュリティ制限およびアクセス制限が課されていることがあります。この制限は、マークアップ コンパイルされた XAML に対する制限よりも限定的です。</span><span class="sxs-lookup"><span data-stu-id="5be76-109">Note that existing techniques for loading loose XAML in WPF also have possible security and access restrictions to CLR types and the type system that are more restrictive than for markup-compiled XAML.</span></span> <span data-ttu-id="5be76-110">詳細については、「 [セキュリティ (WPF)](../../../docs/framework/wpf/security-wpf.md) 」または「 [WPF のセキュリティ方針 - プラットフォーム セキュリティ](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5be76-110">For more information, see [Security (WPF)](../../../docs/framework/wpf/security-wpf.md) or [WPF Security Strategy - Platform Security](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).</span></span>  
  
 <span data-ttu-id="5be76-111">また、XAML 2009 では、以前の XAML 2006 構造を変更するか、または基本的なマークアップ形式を変更する、追加機能も導入されました。</span><span class="sxs-lookup"><span data-stu-id="5be76-111">XAML 2009 also introduces additional features that either modify the previous XAML 2006 constructs or that modify the basic markup forms.</span></span>  
  
### <a name="xkey-as-an-object-element"></a><span data-ttu-id="5be76-112">オブジェクトの要素としての x:Key</span><span class="sxs-lookup"><span data-stu-id="5be76-112">x:Key as an Object Element</span></span>  
 <span data-ttu-id="5be76-113">XAML 2009 では `x:Key` をオブジェクト (オブジェクト要素値を持つプロパティ要素) としてサポートできます。XAML 2006 では、 `x:Key` は属性としてのみサポートされていました。</span><span class="sxs-lookup"><span data-stu-id="5be76-113">XAML 2009 can support `x:Key` as an object (a property element that has object element value); however, XAML 2006 only supported `x:Key` as an attribute.</span></span> <span data-ttu-id="5be76-114">「 [x:Key Directive](../../../docs/framework/xaml-services/x-key-directive.md)」の「XAML 2009」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5be76-114">See the "XAML 2009" section of [x:Key Directive](../../../docs/framework/xaml-services/x-key-directive.md).</span></span>  
  
### <a name="xmlns-on-property-elements"></a><span data-ttu-id="5be76-115">プロパティ要素の xmlns</span><span class="sxs-lookup"><span data-stu-id="5be76-115">xmlns on Property Elements</span></span>  
 <span data-ttu-id="5be76-116">XAML 2009 は、プロパティ要素に対する XAML 名前空間 (xmlns) の定義をサポートできます。XAML 2006 では、オブジェクト要素に対してのみ xmlns 定義をサポートしていました。</span><span class="sxs-lookup"><span data-stu-id="5be76-116">XAML 2009 can support XAML namespace (xmlns) definitions on property elements; however, XAML 2006 only supports xmlns definitions on object elements.</span></span>  
  
### <a name="event-attributes"></a><span data-ttu-id="5be76-117">イベント属性</span><span class="sxs-lookup"><span data-stu-id="5be76-117">Event Attributes</span></span>  
 <span data-ttu-id="5be76-118">イベントによってサポートされる属性については、XAML 2006 ではマークアップ コンパイルが関係していると仮定されて、イベントはマークアップ コンパイルに送信されます。</span><span class="sxs-lookup"><span data-stu-id="5be76-118">For attributes that are backed by events, XAML 2006 presumes that markup compilation is involved and submits the events to markup compilation.</span></span> <span data-ttu-id="5be76-119">XAML 2009 はマークアップ拡張機能に似たマークアップ形式をサポートします。このマークアップ形式は、XAML のランタイム解析と読み込みが行われるまでイベント接続を遅延します。</span><span class="sxs-lookup"><span data-stu-id="5be76-119">XAML 2009 supports a markup form that resembles a markup extension, which defers the event wiring until run-time parsing and loading of the XAML.</span></span> <span data-ttu-id="5be76-120">ただし、WPF アプリケーション、および WPF の UI の XAML シナリオでは、一般にこの機能は使用しません。</span><span class="sxs-lookup"><span data-stu-id="5be76-120">However, WPF applications and XAML scenarios for WPF UI generally do not use this capability.</span></span> <span data-ttu-id="5be76-121">WPF およびその XAML 2006 の実装では、イベント属性処理の大部分に対し、 <xref:System.Windows.UIElement> レベルで定義されたルーティング イベントのイベント ハンドラー接続と、そのマークアップ コンパイラ手順の組み合わせを使用します。</span><span class="sxs-lookup"><span data-stu-id="5be76-121">WPF and its XAML 2006 implementation uses the combination of event handler wiring for routed events defined at the <xref:System.Windows.UIElement> level and its markup compiler step for much of its event attribute processing.</span></span> <span data-ttu-id="5be76-122">マークアップ コンパイラは、XAML 内に見つかるすべてのイベント属性を事前に処理し、マークアップ コンパイラが使用されることがビルド アクションによって宣言されます。</span><span class="sxs-lookup"><span data-stu-id="5be76-122">The markup compiler also preprocesses any event attributes found in XAML where the build actions declare that the markup compiler is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be76-123">参照</span><span class="sxs-lookup"><span data-stu-id="5be76-123">See Also</span></span>  
 [<span data-ttu-id="5be76-124">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="5be76-124">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
