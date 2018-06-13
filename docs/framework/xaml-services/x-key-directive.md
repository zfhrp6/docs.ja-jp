---
title: x:Key ディレクティブ
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: 511721c3ffffb3b80b339c4671ad99e16bafda93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565900"
---
# <a name="xkey-directive"></a><span data-ttu-id="4937d-102">x:Key ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="4937d-102">x:Key Directive</span></span>
<span data-ttu-id="4937d-103">XAML で定義されたディクショナリで作成および参照される要素を一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="4937d-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="4937d-104">`x:Key` 値を XAML オブジェクトに追加するのは、リソース ディクショナリ (<xref:System.Windows.ResourceDictionary> など) のリソースを識別するための最も一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="4937d-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4937d-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="4937d-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="4937d-106">XAML 属性の使用方法 (WPF 固有)</span><span class="sxs-lookup"><span data-stu-id="4937d-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4937d-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="4937d-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="4937d-108">キーとして使用するテキスト文字列。</span><span class="sxs-lookup"><span data-stu-id="4937d-108">A text string to use as a key.</span></span> <span data-ttu-id="4937d-109">テキスト文字列に準拠する必要があります、 [XamlName の文法](../../../docs/framework/xaml-services/xamlname-grammar.md)です。</span><span class="sxs-lookup"><span data-stu-id="4937d-109">The text string must conform to the [XamlName Grammar](../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="4937d-110">マークアップ拡張機能の区切り文字で{}、マークアップ拡張機能の使用をキーとして使用するオブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="4937d-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="4937d-111">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4937d-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4937d-112">コメント</span><span class="sxs-lookup"><span data-stu-id="4937d-112">Remarks</span></span>  
 <span data-ttu-id="4937d-113">`x:Key` は XAML のリソース ディクショナリの概念をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4937d-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="4937d-114">言語としての XAML ではリソース ディクショナリの実装は定義されていません。特定の UI フレーム ワークによって定義されています。</span><span class="sxs-lookup"><span data-stu-id="4937d-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="4937d-115">Wpf XAML リソース ディクショナリを実装する方法の詳細については、次を参照してください。 [XAML リソース](../../../docs/framework/wpf/advanced/xaml-resources.md)です。</span><span class="sxs-lookup"><span data-stu-id="4937d-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="4937d-116">XAML 2006 および WPF では、`x:Key`属性として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4937d-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="4937d-117">文字列ではないキーも使用できますが、文字列ではない値を属性形式で提供するためには、マークアップ拡張機能を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4937d-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="4937d-118">XAML 2009 を使用している場合`x:Key`マークアップ拡張機能の仲介を必要とせず、文字列以外のオブジェクトの種類をキーとするディクショナリを明示的にサポートを要素として指定できます。</span><span class="sxs-lookup"><span data-stu-id="4937d-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="4937d-119">このトピックの「XAML 2009」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4937d-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="4937d-120">「解説」セクションの残りの部分は、特定 XAML 2006 の実装に適用します。</span><span class="sxs-lookup"><span data-stu-id="4937d-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="4937d-121">属性値`x:Key`任意の文字列で定義できる、 [XamlName の文法](../../../docs/framework/xaml-services/xamlname-grammar.md)マークアップ拡張機能によって評価されるオブジェクトであることができます。</span><span class="sxs-lookup"><span data-stu-id="4937d-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](../../../docs/framework/xaml-services/xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="4937d-122">WPF の例については、「WPF の使用上の注意」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4937d-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="4937d-123">通常、<xref:System.Collections.IDictionary> の実装である親要素の子要素には、そのディクショナリ内の一意のキー値を指定する `x:Key` 属性を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="4937d-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="4937d-124">フレームワークでは、特定の型の `x:Key` を代用するために、エイリアス化されたキー プロパティを実装する場合があります。このようなプロパティを定義する型には、<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4937d-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="4937d-125">`x:Key` の指定に相当するコードは、基になる <xref:System.Collections.IDictionary> で使用されるキーです。</span><span class="sxs-lookup"><span data-stu-id="4937d-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="4937d-126">たとえば、マークアップで適用される WPF のリソースの `x:Key` は、コードでリソースを WPF の `key` に追加する場合、<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> の <xref:System.Windows.ResourceDictionary> パラメーターの値と同等です。</span><span class="sxs-lookup"><span data-stu-id="4937d-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="4937d-127">WPF の使用上の注意</span><span class="sxs-lookup"><span data-stu-id="4937d-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="4937d-128">通常、WPF の <xref:System.Collections.IDictionary> などの <xref:System.Windows.ResourceDictionary> の実装である親オブジェクトの子オブジェクトには、`x:Key` 属性を含める必要があります。また、キー値は、そのディクショナリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4937d-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="4937d-129">ただし、次のように 2 つの重要な例外があります。</span><span class="sxs-lookup"><span data-stu-id="4937d-129">There are two notable exceptions:</span></span>  
  
-   <span data-ttu-id="4937d-130">一部の WPF 型は、ディクショナリの使用に対して暗黙のキーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="4937d-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="4937d-131">たとえば、<xref:System.Windows.Style> が設定された <xref:System.Windows.Style.TargetType%2A> や、<xref:System.Windows.DataTemplate> が設定された <xref:System.Windows.DataTemplate.DataType%2A> は、<xref:System.Windows.ResourceDictionary> に格納して、暗黙のキーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4937d-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
-   <span data-ttu-id="4937d-132">WPF は、マージされたリソース ディクショナリの概念をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4937d-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="4937d-133">キーは、マージされたディクショナリ間で共有できます。また、共有されたキーの動作には、<xref:System.Windows.FrameworkContentElement.FindResource%2A> を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4937d-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="4937d-134">詳細については、「[Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4937d-134">For more information, see [Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
 <span data-ttu-id="4937d-135">通常、WPF XAML の実装およびアプリケーション モデルでは、キーの一意性が XAML マークアップ コンパイラによってチェックされることはありません。</span><span class="sxs-lookup"><span data-stu-id="4937d-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="4937d-136">その代わり、`x:Key` 値が指定されていない場合や一意でない場合は、読み込み時に XAML パーサー エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4937d-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="4937d-137">ただし、wpf のディクショナリの Visual Studio 処理できます多くの場合、このようなエラー、設計フェーズで。</span><span class="sxs-lookup"><span data-stu-id="4937d-137">However, Visual Studio handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="4937d-138">ここに示す構文において、<xref:System.Windows.ResourceDictionary> オブジェクトは WPF XAML プロセッサが <xref:System.Windows.FrameworkElement.Resources%2A> コレクションを取得するためのコレクションを生成する方法を暗黙的に決定することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4937d-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="4937d-139"><xref:System.Windows.ResourceDictionary> は、通常はマークアップで要素として明示的に指定されませんが、わかりやすくするために必要に応じて明示的に指定することもできます (その場合、このオブジェクトは、<xref:System.Windows.FrameworkElement.Resources%2A> プロパティ要素とディクショナリに設定される項目間のコレクション オブジェクト要素になります)。</span><span class="sxs-lookup"><span data-stu-id="4937d-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="4937d-140">なぜ、コレクション オブジェクトはほとんどの場合、暗黙的なマークアップで要素については、次を参照してください。 [XAML 構文の詳細](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)です。</span><span class="sxs-lookup"><span data-stu-id="4937d-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
 <span data-ttu-id="4937d-141">WPF XAML 実装では、リソース ディクショナリ キーの処理は、<xref:System.Windows.ResourceKey> 抽象クラスによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="4937d-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="4937d-142">ただし、WPF XAML プロセッサは、使用方法に基づいてキーごとに別の基になる拡張型を生成します。</span><span class="sxs-lookup"><span data-stu-id="4937d-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="4937d-143">たとえば、<xref:System.Windows.DataTemplate> または任意の派生クラスのキーは個別に処理され、異なる <xref:System.Windows.DataTemplateKey> オブジェクトを生成します。</span><span class="sxs-lookup"><span data-stu-id="4937d-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="4937d-144">基本的な XAML 定義では、キーと名前で異なるディレクティブと言語要素 (`x:Key` と `x:Name`) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4937d-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="4937d-145">また、キーと名前は、それらの概念の WPF 定義およびアプリケーションにより異なる状況において使用されます。</span><span class="sxs-lookup"><span data-stu-id="4937d-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="4937d-146">詳細については、「 [WPF XAML 名前スコープ](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)です。</span><span class="sxs-lookup"><span data-stu-id="4937d-146">For details, see [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).</span></span>  
  
 <span data-ttu-id="4937d-147">既に説明したように、キー値はマークアップ拡張機能によって指定され、文字列値以外になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4937d-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="4937d-148">WPF シナリオの例は、の値を提供する`x:Key`可能性があります、[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md)です。</span><span class="sxs-lookup"><span data-stu-id="4937d-148">An example WPF scenario is that the value of `x:Key` may be a[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).</span></span> <span data-ttu-id="4937d-149">特定のコントロールでは、スタイルを完全に置き換えることなく、そのコントロールの外観と動作の一部に影響を与えるカスタム スタイル リソースの型に対応するスタイル キーが公開されます。</span><span class="sxs-lookup"><span data-stu-id="4937d-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="4937d-150">このようなキーの例として、<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="4937d-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="4937d-151">WPF のマージされたディクショナリ機能では、キーの一意性およびキーの検索動作について考慮を要する点があります。</span><span class="sxs-lookup"><span data-stu-id="4937d-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="4937d-152">詳細については、「[Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4937d-152">For more information, see [Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="4937d-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="4937d-153">XAML 2009</span></span>  
 <span data-ttu-id="4937d-154">XAML 2009 は、制限を緩和する`x:Key`常に、属性の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="4937d-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="4937d-155">WPF では、マークアップ コンパイルされていない XAML にについては、XAML 2009 の機能を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4937d-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="4937d-156">WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4937d-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="4937d-157">XAML 2009 でを指定できます`x:Key`次の使用法を使用して要素。</span><span class="sxs-lookup"><span data-stu-id="4937d-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="4937d-158">XAML 要素の使用 (XAML 2009 のみ)</span><span class="sxs-lookup"><span data-stu-id="4937d-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="4937d-159">XAML 値</span><span class="sxs-lookup"><span data-stu-id="4937d-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="4937d-160">専用のディクショナリで指定された `object` のキーとして使用されるオブジェクトの、オブジェクト要素。</span><span class="sxs-lookup"><span data-stu-id="4937d-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
-   <span data-ttu-id="4937d-161">この種類の使用方法のコンテナー/親は、ここには示しません。</span><span class="sxs-lookup"><span data-stu-id="4937d-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="4937d-162">`object` は、専用のディクショナリの実装を表すオブジェクト要素の子であると想定されます。</span><span class="sxs-lookup"><span data-stu-id="4937d-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="4937d-163">`keyObject` は、その専用のディクショナリの実装のキーとして適切なオブジェクト インスタンス (または値の型の値) であると想定されます。</span><span class="sxs-lookup"><span data-stu-id="4937d-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
-   <span data-ttu-id="4937d-164">WPF は、この使用方法を必要とするディクショナリを実装しません。</span><span class="sxs-lookup"><span data-stu-id="4937d-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="4937d-165">オブジェクト キーは XAML 言語のより一般的な機能であり、カスタム ディクショナリのシナリオで XAML でのディクショナリ作成が望まれる場合に有益であることがあります。</span><span class="sxs-lookup"><span data-stu-id="4937d-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="4937d-166">リソースに対して文字列以外のキーを使用する暗黙的なスタイルなどの WPF 機能については、別の方法によってキーを確立、または指定することができるので、オブジェクト キーを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4937d-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
-   <span data-ttu-id="4937d-167">*keyObject*直接オブジェクト インスタンスではなく、オブジェクト要素の形式でマークアップ拡張機能の使用可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4937d-167">*keyObject* could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="4937d-168">Silverlight の使用上の注意</span><span class="sxs-lookup"><span data-stu-id="4937d-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="4937d-169">Silverlight 用の `x:Key` に関しては、別途ドキュメントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4937d-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="4937d-170">詳細については、次を参照してください[XAML Namespace (x:)。言語機能 (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081)です。</span><span class="sxs-lookup"><span data-stu-id="4937d-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4937d-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="4937d-171">See Also</span></span>  
 [<span data-ttu-id="4937d-172">XAML リソース</span><span class="sxs-lookup"><span data-stu-id="4937d-172">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="4937d-173">リソースとコード</span><span class="sxs-lookup"><span data-stu-id="4937d-173">Resources and Code</span></span>](../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="4937d-174">StaticResource のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="4937d-174">StaticResource Markup Extension</span></span>](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
