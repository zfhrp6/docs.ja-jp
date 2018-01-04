---
title: "x:Array のマークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc2304ba68956b705904c72e29a17bdac4536c79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="29aa3-102">x:Array のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="29aa3-102">x:Array Markup Extension</span></span>
<span data-ttu-id="29aa3-103">マークアップ拡張機能によって、XAML でのオブジェクトの配列には、一般的なサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="29aa3-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="29aa3-104">これに対応して、 `x:ArrayExtension` [MS-XAML] の XAML の型。</span><span class="sxs-lookup"><span data-stu-id="29aa3-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="29aa3-105">XAML オブジェクト要素の使用方法</span><span class="sxs-lookup"><span data-stu-id="29aa3-105">XAML Object Element Usage</span></span>  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="29aa3-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="29aa3-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="29aa3-107">型の名前を`x:Array`が含まれます。</span><span class="sxs-lookup"><span data-stu-id="29aa3-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="29aa3-108">`typeName`可能性があります (および多くの場合) を含む XAML 名前空間は XAML のプレフィックス定義を入力します。</span><span class="sxs-lookup"><span data-stu-id="29aa3-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="29aa3-109">組み込みに割り当てられている項目コンテンツ`ArrayExtension.Items`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="29aa3-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="29aa3-110">通常、これらの項目が内に含まれる 1 つまたは複数のオブジェクト要素として指定、`x:Array`タグと終了タグ。</span><span class="sxs-lookup"><span data-stu-id="29aa3-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="29aa3-111">指定したオブジェクトはここで含められるはずで指定された XAML 型に割り当てることができる`typeName`です。</span><span class="sxs-lookup"><span data-stu-id="29aa3-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29aa3-112">コメント</span><span class="sxs-lookup"><span data-stu-id="29aa3-112">Remarks</span></span>  
 <span data-ttu-id="29aa3-113">`Type`すべての必須の属性は、 `x:Array` object 要素。</span><span class="sxs-lookup"><span data-stu-id="29aa3-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="29aa3-114">A`Type`パラメーターの値が使用する必要はありません、`x:Type`マークアップ拡張機能です。 短い型の名前は XAML 型の型を文字列として指定することができます。</span><span class="sxs-lookup"><span data-stu-id="29aa3-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="29aa3-115">入力 XAML の型と CLR の出力の間の関係、.NET Framework XAML サービス実装で<xref:System.Type>作成された配列のサービス コンテキストのマークアップ拡張機能によって影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="29aa3-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="29aa3-116">出力<xref:System.Type>は、 <xref:System.Xaml.XamlType.UnderlyingType%2A> 、必要なを検索した後、入力の XAML 型の<xref:System.Xaml.XamlType>XAML スキーマ コンテキストに基づいて、<xref:System.Windows.Markup.IXamlTypeResolver>サービス コンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="29aa3-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="29aa3-117">配列の内容に割り当てられた、処理されるときに、`ArrayExtension.Items`組み込みプロパティです。</span><span class="sxs-lookup"><span data-stu-id="29aa3-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="29aa3-118"><xref:System.Windows.Markup.ArrayExtension>実装では、これは、によって表される<xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="29aa3-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="29aa3-119">.NET Framework XAML サービス実装では、このマークアップ拡張機能の処理がによって定義された、<xref:System.Windows.Markup.ArrayExtension>クラスです。</span><span class="sxs-lookup"><span data-stu-id="29aa3-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="29aa3-120"><xref:System.Windows.Markup.ArrayExtension>封印されていないと、カスタムの配列型のマークアップ拡張機能の実装の基礎として使用できます。</span><span class="sxs-lookup"><span data-stu-id="29aa3-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="29aa3-121">`x:Array`以上の目的の一般的な XAML の言語拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="29aa3-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="29aa3-122">しかし、`x:Array`にも特定のプロパティの構造化プロパティ コンテンツとして XAML でサポートされているコレクションを取得する XAML の値を指定するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="29aa3-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="29aa3-123">内容を指定するなど、<xref:System.Collections.IEnumerable>を持つプロパティ、`x:Array`使用量。</span><span class="sxs-lookup"><span data-stu-id="29aa3-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="29aa3-124">`x:Array` はマークアップ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="29aa3-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="29aa3-125">一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。</span><span class="sxs-lookup"><span data-stu-id="29aa3-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="29aa3-126">`x:Array`その規則の例外では部分的に代替の属性値の処理を提供する代わりに`x:Array`その内部のテキスト コンテンツの代替の処理を提供します。</span><span class="sxs-lookup"><span data-stu-id="29aa3-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="29aa3-127">この動作により、型を配列にグループ化して、名前付きの配列へのアクセスを後で分離コード内で参照する既存のコンテンツ モデルでサポートされていない可能性があります。呼び出すことができます<xref:System.Array>を個々 の配列項目を取得するメソッド。</span><span class="sxs-lookup"><span data-stu-id="29aa3-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="29aa3-128">XAML でのすべてのマークアップ拡張機能は、かっこを使用して ({、}`)`それぞれ属性の構文では、マークアップ拡張機能が属性値を処理する必要がありますを XAML プロセッサが認識される規約。</span><span class="sxs-lookup"><span data-stu-id="29aa3-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="29aa3-129">一般にマークアップ拡張機能の詳細については、次を参照してください。[型コンバーターと XAML のマークアップ拡張機能](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)します。</span><span class="sxs-lookup"><span data-stu-id="29aa3-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="29aa3-130">XAML 2009 で`x:Array`マークアップ拡張機能ではなくプリミティブ言語として定義されます。</span><span class="sxs-lookup"><span data-stu-id="29aa3-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="29aa3-131">詳細については、次を参照してください。[共通の XAML 言語プリミティブの組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)です。</span><span class="sxs-lookup"><span data-stu-id="29aa3-131">For more information, see [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="29aa3-132">WPF の使用上の注意</span><span class="sxs-lookup"><span data-stu-id="29aa3-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="29aa3-133">通常、オブジェクトの要素を設定する、`x:Array`に存在する要素ではない、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]の XAML 名前空間を既定以外の XAML 名前空間プレフィックスのマッピングを必要とします。</span><span class="sxs-lookup"><span data-stu-id="29aa3-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="29aa3-134">例を次に示します、単純な 2 つの文字列の配列で、`sys`プレフィックス (も`x`) 配列のレベルで定義します。</span><span class="sxs-lookup"><span data-stu-id="29aa3-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
 <span data-ttu-id="29aa3-135">[xaml]</span><span class="sxs-lookup"><span data-stu-id="29aa3-135">[xaml]</span></span>  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 <span data-ttu-id="29aa3-136">配列の要素として使用されるカスタム型、クラスは、xaml オブジェクト要素としてインスタンス化の要件をサポートもする必要があります。</span><span class="sxs-lookup"><span data-stu-id="29aa3-136">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="29aa3-137">詳細については、次を参照してください。 [XAML と WPF のカスタム クラス](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)です。</span><span class="sxs-lookup"><span data-stu-id="29aa3-137">For more information, see [XAML and Custom Classes for WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29aa3-138">参照</span><span class="sxs-lookup"><span data-stu-id="29aa3-138">See Also</span></span>  
 [<span data-ttu-id="29aa3-139">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="29aa3-139">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="29aa3-140">WPF から System.Xaml に移行した型</span><span class="sxs-lookup"><span data-stu-id="29aa3-140">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
