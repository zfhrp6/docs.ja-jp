---
title: "x:Type マークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d645d5c953c0ff33435a5648024ace099455e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="3c342-102">x:Type マークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="3c342-102">x:Type Markup Extension</span></span>
<span data-ttu-id="3c342-103">CLR の提供<xref:System.Type>指定の XAML 型の基になる型であるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3c342-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3c342-104">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="3c342-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="3c342-105">XAML オブジェクト要素の使用方法</span><span class="sxs-lookup"><span data-stu-id="3c342-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3c342-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="3c342-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="3c342-107">任意。</span><span class="sxs-lookup"><span data-stu-id="3c342-107">Optional.</span></span> <span data-ttu-id="3c342-108">既定以外の XAML 名前空間にマップされるプレフィックス。</span><span class="sxs-lookup"><span data-stu-id="3c342-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="3c342-109">プレフィックスを指定する多くの場合必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3c342-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="3c342-110">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c342-110">See Remarks.</span></span>|  
|`typeNameValue`|<span data-ttu-id="3c342-111">必須。</span><span class="sxs-lookup"><span data-stu-id="3c342-111">Required.</span></span> <span data-ttu-id="3c342-112">現在既定の XAML 名前空間以外に解決可能な型名指定した場合はマップのプレフィックスまたは`prefix`を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c342-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c342-113">コメント</span><span class="sxs-lookup"><span data-stu-id="3c342-113">Remarks</span></span>  
 <span data-ttu-id="3c342-114">`x:Type`マークアップ拡張機能と同様の機能は、`typeof()`で演算子[!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)]または`GetType`で演算子[!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="3c342-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] or the `GetType` operator in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span></span>  
  
 <span data-ttu-id="3c342-115">`x:Type`マークアップ拡張機能は、種類を取得するプロパティの文字列から変換動作を提供<xref:System.Type>です。</span><span class="sxs-lookup"><span data-stu-id="3c342-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="3c342-116">入力は、XAML の型です。</span><span class="sxs-lookup"><span data-stu-id="3c342-116">The input is a XAML type.</span></span> <span data-ttu-id="3c342-117">入力 XAML の型と CLR の出力間のリレーションシップ<xref:System.Type>出力される<xref:System.Type>は、<xref:System.Xaml.XamlType.UnderlyingType%2A>入力の<xref:System.Xaml.XamlType>、必要なを検索した後<xref:System.Xaml.XamlType>XAML スキーマ コンテキストと、に基づいて<xref:System.Windows.Markup.IXamlTypeResolver>サービス コンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="3c342-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="3c342-118">.NET Framework XAML サービスで、このマークアップ拡張機能の処理がによって定義された、<xref:System.Windows.Markup.TypeExtension>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3c342-118">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>  
  
 <span data-ttu-id="3c342-119">実装では特定のフレームワーク、いくつかのプロパティを受け取る<xref:System.Type>ように、値は、型の名前を直接受け入れることができます (型の文字列値`Name`)。</span><span class="sxs-lookup"><span data-stu-id="3c342-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="3c342-120">ただし、この動作を実装することは、複雑なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="3c342-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="3c342-121">例については、次の「WPF の使用上の注意」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c342-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>  
  
 <span data-ttu-id="3c342-122">属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。</span><span class="sxs-lookup"><span data-stu-id="3c342-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="3c342-123">`x:Type` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 拡張クラスの <xref:System.Windows.Markup.TypeExtension> 値として割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3c342-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="3c342-124">CLR 型に基づいている .NET Framework XAML サービスの既定の XAML スキーマ コンテキスト下でこの属性の値は、いずれか、<xref:System.Reflection.MemberInfo.Name%2A>の目的の型を格納または<xref:System.Reflection.MemberInfo.Name%2A>既定以外の XAML 名前空間のプレフィックスに続くマッピングです。</span><span class="sxs-lookup"><span data-stu-id="3c342-124">Under the default XAML schema context for .NET Framework XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>  
  
 <span data-ttu-id="3c342-125">`x:Type`オブジェクト要素の構文でマークアップ拡張機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c342-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="3c342-126">ここでは、値を指定する、<xref:System.Windows.Markup.TypeExtension.TypeName%2A>プロパティは、拡張機能を正しく初期化するために必要です。</span><span class="sxs-lookup"><span data-stu-id="3c342-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="3c342-127">`x:Type`マークアップ拡張機能は、verbose 属性としても使用できますただしこの使用法は一般的な: `<``object` 。`property``="{x:Type TypeName=``typeNameValue``}" .../>`</span><span class="sxs-lookup"><span data-stu-id="3c342-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="3c342-128">WPF の使用上の注意</span><span class="sxs-lookup"><span data-stu-id="3c342-128">WPF Usage Notes</span></span>  
  
### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="3c342-129">既定の XAML Namespace と型のマッピング</span><span class="sxs-lookup"><span data-stu-id="3c342-129">Default XAML Namespace and Type Mapping</span></span>  
 <span data-ttu-id="3c342-130">WPF のプログラミングの既定の XAML 名前空間には、通常の XAML シナリオに必要な XAML 型の大部分が含まれていますそのため、XAML 型の値を参照するときに、多くの場合、プレフィックスを回避することができます。</span><span class="sxs-lookup"><span data-stu-id="3c342-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="3c342-131">カスタム アセンブリから、または既定の XAML 名前空間にマッピングされませんでした、CLR 名前空間からは、WPF アセンブリ内に存在する型の型を参照している場合、プレフィックスをマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c342-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="3c342-132">プレフィックス、XAML 名前空間と CLR 名前空間のマッピングに関する詳細については、次を参照してください。 [XAML 名前空間と WPF XAML 向け Namespace マッピング](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c342-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="3c342-133">プロパティをサポート Typename としての文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="3c342-133">Type Properties That Support Typename-as-String</span></span>  
 <span data-ttu-id="3c342-134">WPF でサポートされる型の一部のプロパティの値を指定できるようにする手法<xref:System.Type>を必要とせず、`x:Type`マークアップ拡張機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c342-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="3c342-135">代わりに、型に名前を文字列として値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3c342-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="3c342-136">この機能にはの例として<xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType>と<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="3c342-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3c342-137">この動作のサポートは、型コンバーターまたはマークアップ拡張機能のどちらかを通じて提供されていません。</span><span class="sxs-lookup"><span data-stu-id="3c342-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="3c342-138">これによって実装され、遅延の動作は、代わりに、<xref:System.Windows.FrameworkElementFactory>です。</span><span class="sxs-lookup"><span data-stu-id="3c342-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>  
  
 <span data-ttu-id="3c342-139">Silverlight は、同様の規則をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3c342-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="3c342-140">実際には、Silverlight はサポートされていません`{x:Type}`、XAML 言語のサポートでは受け付けられません`{x:Type}`WPF Silverlight の XAML の移行をサポートするものでは、いくつかの状況の外部で使用します。</span><span class="sxs-lookup"><span data-stu-id="3c342-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="3c342-141">したがって、typename-文字列としての動作はすべて Silverlight ネイティブ プロパティの評価に組み込まれている、<xref:System.Type>値です。</span><span class="sxs-lookup"><span data-stu-id="3c342-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="3c342-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="3c342-142">XAML 2009</span></span>  
 <span data-ttu-id="3c342-143">XAML 2009 はジェネリック型し、の機能の動作が変更の追加サポートを提供`x:TypeArguments`と`x:Type`このサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="3c342-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>  
  
-   <span data-ttu-id="3c342-144">`x:TypeArguments`汎用オブジェクトのインスタンス化に関連付けられているオブジェクトの要素がルート以外の要素にあることができます。</span><span class="sxs-lookup"><span data-stu-id="3c342-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="3c342-145">詳細については、「XAML 2009」のセクションを参照してください。 [X:typearguments ディレクティブ](../../../docs/framework/xaml-services/x-typearguments-directive.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c342-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
-   <span data-ttu-id="3c342-146">XAML 2009 では、マークアップでジェネリック型の制約を指定する構文をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3c342-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="3c342-147">によって使用されるこの`x:TypeArguments`により、 `x:Type`、または組み合わせで 2 つの機能です。</span><span class="sxs-lookup"><span data-stu-id="3c342-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>  
  
-   <span data-ttu-id="3c342-148">XAML の WPF 実装の負荷では、暗黙の型変換動作の種類を使用する特定のフレームワーク プロパティにこの機能が追加されても、XAML 2009 を処理するときに<xref:System.Type>です。</span><span class="sxs-lookup"><span data-stu-id="3c342-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="3c342-149">WPF では、loose XAML (XAML をマークアップ コンパイルされていない) については、XAML 2009 の機能を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3c342-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="3c342-150">WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3c342-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c342-151">参照</span><span class="sxs-lookup"><span data-stu-id="3c342-151">See Also</span></span>  
 <xref:System.Windows.Style>  
 [<span data-ttu-id="3c342-152">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="3c342-152">Styling and Templating</span></span>](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3c342-153">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="3c342-153">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="3c342-154">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="3c342-154">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
