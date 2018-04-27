---
title: XAML のジェネリック
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e64224edcb49d5040332b7cef9649c98cf26798b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="generics-in-xaml"></a><span data-ttu-id="1733c-102">XAML のジェネリック</span><span class="sxs-lookup"><span data-stu-id="1733c-102">Generics in XAML</span></span>
<span data-ttu-id="1733c-103">System.Xaml に実装されている .NET Framework XAML サービスでは、CLR 型のジェネリック型を使用するためのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="1733c-103">The .NET Framework XAML Services as implemented in System.Xaml provides support for using generic CLR types.</span></span> <span data-ttu-id="1733c-104">このサポートには、引数の型としてジェネリックの制約を指定して、適切な呼び出しによって、制約の適用が含まれます。`Add`メソッドのジェネリック コレクションの場合。</span><span class="sxs-lookup"><span data-stu-id="1733c-104">This support includes specifying the constraints of generics as a type argument and enforcing the constraint by calling the appropriate `Add` method for generic collection cases.</span></span> <span data-ttu-id="1733c-105">このトピックを使用して、XAML でのジェネリック型の参照の側面について説明します。</span><span class="sxs-lookup"><span data-stu-id="1733c-105">This topic describes aspects of using and referencing generic types in XAML.</span></span>  
  
## <a name="xtypearguments"></a><span data-ttu-id="1733c-106">x: TypeArguments</span><span class="sxs-lookup"><span data-stu-id="1733c-106">x:TypeArguments</span></span>  
 <span data-ttu-id="1733c-107">`x:TypeArguments` ディレクティブは、XAML 言語によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="1733c-107">`x:TypeArguments` is a directive defined by the XAML language.</span></span> <span data-ttu-id="1733c-108">ジェネリック型によってバックアップされている XAML 型のメンバーとして使用されているときに`x:TypeArguments`型のバッキング コンス トラクターに、ジェネリック引数を渡すの制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="1733c-108">When it is used as a member of a XAML type that is backed by a generic type, `x:TypeArguments` passes constraining type arguments of the generic to the backing constructor.</span></span> <span data-ttu-id="1733c-109">.NET Framework XAML サービスに関連する参照構文の使用`x:TypeArguments`、構文の例を含むを参照してください[X:typearguments ディレクティブ](../../../docs/framework/xaml-services/x-typearguments-directive.md)です。</span><span class="sxs-lookup"><span data-stu-id="1733c-109">For reference syntax that pertains to .NET Framework XAML Services use of `x:TypeArguments`, which includes syntax examples, see [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
 <span data-ttu-id="1733c-110">`x:TypeArguments`文字列を受け取り、型コンバーター バッキングの場合は通常、属性として XAML の使用方法で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="1733c-110">Because `x:TypeArguments` takes a string, and has type converter backing, it is typically declared in XAML usage as an attribute.</span></span>  
  
 <span data-ttu-id="1733c-111">によって、XAML ノード ストリームで、情報が宣言されている`x:TypeArguments`から取得できる<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>で、`StartObject`ノード ストリーム内の位置。</span><span class="sxs-lookup"><span data-stu-id="1733c-111">In the XAML node stream, the information declared by `x:TypeArguments` can be obtained from <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> at a `StartObject` position in the node stream.</span></span> <span data-ttu-id="1733c-112">戻り値<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>の一覧を示します<xref:System.Xaml.XamlType>値。</span><span class="sxs-lookup"><span data-stu-id="1733c-112">The return value of <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> is a list of <xref:System.Xaml.XamlType> values.</span></span> <span data-ttu-id="1733c-113">呼び出して、XAML の型がジェネリック型を表すかどうかの決定ができる<xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="1733c-113">Determination of whether a XAML type represents a generic type can be made by calling <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a><span data-ttu-id="1733c-114">ルールおよび XAML におけるジェネリックの構文表記規則</span><span class="sxs-lookup"><span data-stu-id="1733c-114">Rules and Syntax Conventions for Generics in XAML</span></span>  
 <span data-ttu-id="1733c-115">XAML では、ジェネリック型表す必要が常にある制約付きジェネリック; として制約のないジェネリックでは、XAML 型システムまたは XAML ノード ストリーム内が存在しないと、XAML マークアップで表されることはできません。</span><span class="sxs-lookup"><span data-stu-id="1733c-115">In XAML, a generic type must always be represented as a constrained generic; an unconstrained generic is never present in the XAML type system or a XAML node stream and cannot be represented in XAML markup.</span></span> <span data-ttu-id="1733c-116">ジェネリック型によって参照されているジェネリック型の入れ子にされた型の制約がある場合に、XAML 属性の構文で参照できます`x:TypeArguments`、場合や、`x:Type`ジェネリック型の CLR 型参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="1733c-116">A generic can be referenced within XAML attribute syntax, for cases where it is a nested type constraint of a generic being referenced by `x:TypeArguments`, or for cases where `x:Type` supplies a CLR type reference for a generic type.</span></span> <span data-ttu-id="1733c-117">これは、 <xref:System.Xaml.Schema.XamlTypeTypeConverter> .NET Framework XAML サービスによって定義されるクラスです。</span><span class="sxs-lookup"><span data-stu-id="1733c-117">This is supported through the <xref:System.Xaml.Schema.XamlTypeTypeConverter> class defined by .NET Framework XAML Services.</span></span>  
  
 <span data-ttu-id="1733c-118">XAML 属性の構文形式で有効になって<xref:System.Xaml.Schema.XamlTypeTypeConverter>典型的な MSIL を変更/角度を使用する CLR の構文規則の名前の型と、ジェネリックの制約の角かっこを代わりに制約コンテナーのかっこを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1733c-118">The XAML attribute syntax form enabled by <xref:System.Xaml.Schema.XamlTypeTypeConverter> alters the typical MSIL / CLR syntax convention that uses angle brackets for types and constraints of generics, and instead substitutes parentheses for the constraint container.</span></span> <span data-ttu-id="1733c-119">例については、次を参照してください。 [X:typearguments ディレクティブ](../../../docs/framework/xaml-services/x-typearguments-directive.md)です。</span><span class="sxs-lookup"><span data-stu-id="1733c-119">For an example, see [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
## <a name="generics-and-xaml-2009-features"></a><span data-ttu-id="1733c-120">ジェネリックと XAML 2009 の機能</span><span class="sxs-lookup"><span data-stu-id="1733c-120">Generics and XAML 2009 Features</span></span>  
 <span data-ttu-id="1733c-121">XAML 2009 を使用する場合は、CLR のマッピングではなく基本データ型を共通言語プリミティブの XAML 型を取得する、使用することができます[XAML 2009 の組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)情報アイテムとして`x:TypeArguments`です。</span><span class="sxs-lookup"><span data-stu-id="1733c-121">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [XAML 2009 built-in types](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) as information items in `x:TypeArguments`.</span></span> <span data-ttu-id="1733c-122">たとえば、次を宣言する可能性があります (表示されませんが、マッピングのプレフィックスが`x`は XAML 2009 の XAML 言語の XAML 名前空間)。</span><span class="sxs-lookup"><span data-stu-id="1733c-122">For example, you could declare the following (prefix mappings not shown, but `x` is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a><span data-ttu-id="1733c-123">WPF およびその他の v3.5 フレームワークでジェネリックのサポート</span><span class="sxs-lookup"><span data-stu-id="1733c-123">Generics Support in WPF and Other v3.5 Frameworks</span></span>  
 <span data-ttu-id="1733c-124">具体的には、WPF を対象とする場合の XAML 2006 の使用状況の[X:class](../../../docs/framework/xaml-services/x-class-directive.md)もと同じ要素に提供される必要があります`x:TypeArguments`、し、その要素は、XAML ドキュメントのルート要素である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1733c-124">For XAML 2006 usage when specifically targeting WPF, [x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element as `x:TypeArguments`, and that element must be the root element in a XAML document.</span></span> <span data-ttu-id="1733c-125">ルート要素は、少なくとも 1 つの型引数を持つジェネリック型にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1733c-125">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="1733c-126">例としては<xref:System.Windows.Navigation.PageFunction%601>します。</span><span class="sxs-lookup"><span data-stu-id="1733c-126">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span>  
  
 <span data-ttu-id="1733c-127">ジェネリックの使用をサポートするために、考えられる回避策など、ジェネリック型を返すことができるカスタム マークアップ拡張機能の定義、折り返しを提供するクラス定義があるが、ジェネリック型から派生した独自のクラス定義内でジェネリック制約を平坦化します。</span><span class="sxs-lookup"><span data-stu-id="1733c-127">Possible workarounds to support generic usages include defining a custom markup extension that can return generic types, or providing a wrapping class definition that derives from a generic type but flattens the generic constraint in its own class definition.</span></span>  
  
 <span data-ttu-id="1733c-128">対象とする WPF における[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]、と共に XAML 2009 の機能を使用することができます`x:TypeArguments`、loose XAML (XAML をマークアップ コンパイルされていない) に対してのみです。</span><span class="sxs-lookup"><span data-stu-id="1733c-128">In WPF and targeting [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], you can use XAML 2009 features together with `x:TypeArguments`, but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="1733c-129">WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1733c-129">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="1733c-130">カスタムの Windows Workflow Foundation ワークフロー[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]汎用的な XAML の使用方法をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1733c-130">Custom workflows in Windows Workflow Foundation for [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] do not support generic XAML usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1733c-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="1733c-131">See Also</span></span>  
 [<span data-ttu-id="1733c-132">x:TypeArguments ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="1733c-132">x:TypeArguments Directive</span></span>](../../../docs/framework/xaml-services/x-typearguments-directive.md)  
 [<span data-ttu-id="1733c-133">x:Class ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="1733c-133">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="1733c-134">共通の XAML 言語プリミティブの組み込み型</span><span class="sxs-lookup"><span data-stu-id="1733c-134">Built-in Types for Common XAML Language Primitives</span></span>](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
