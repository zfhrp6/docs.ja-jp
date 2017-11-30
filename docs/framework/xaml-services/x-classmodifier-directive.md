---
title: "x:ClassModifier ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: "22"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 111c4a6ed78a908ae3b171dc9349a3c9b81750de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="14521-102">x:ClassModifier ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="14521-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="14521-103">XAML のコンパイルの動作を変更するときに`x:Class`も用意されています。</span><span class="sxs-lookup"><span data-stu-id="14521-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="14521-104">部分を作成する代わりに、具体的には、`class`を持つ、`Public`アクセス レベル (既定)、指定された`x:Class`で作成された、`NotPublic`アクセス レベル。</span><span class="sxs-lookup"><span data-stu-id="14521-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="14521-105">この動作では、生成されたアセンブリでクラスのアクセス レベルに影響します。</span><span class="sxs-lookup"><span data-stu-id="14521-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="14521-106">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="14521-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="14521-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="14521-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14521-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="14521-108">*NotPublic*</span></span>|<span data-ttu-id="14521-109">正確な文字列を指定に渡す<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>を使用する分離コードのプログラミング言語によって異なります。</span><span class="sxs-lookup"><span data-stu-id="14521-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="14521-110">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14521-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="14521-111">依存関係</span><span class="sxs-lookup"><span data-stu-id="14521-111">Dependencies</span></span>  
 <span data-ttu-id="14521-112">[X:class](../../../docs/framework/xaml-services/x-class-directive.md)も、同じ要素に提供される必要があり、その要素はページのルート要素である必要があります。</span><span class="sxs-lookup"><span data-stu-id="14521-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="14521-113">詳細については、次を参照してください。 [ \[MS-XAML\]セクション 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="14521-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14521-114">コメント</span><span class="sxs-lookup"><span data-stu-id="14521-114">Remarks</span></span>  
 <span data-ttu-id="14521-115">値`x:ClassModifier`.NET Framework XAML サービスの使用方法はプログラミング言語によって異なります。</span><span class="sxs-lookup"><span data-stu-id="14521-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="14521-116">使用する文字列は、各言語の実装に依存その<xref:System.CodeDom.Compiler.CodeDomProvider>と返しますの意味を定義する型コンバーター<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>、その言語は大文字小文字を区別するかどうかとします。</span><span class="sxs-lookup"><span data-stu-id="14521-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="14521-117">[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]、指定に渡す文字列<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>は`internal`します。</span><span class="sxs-lookup"><span data-stu-id="14521-117">For [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="14521-118">[!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)]、指定に渡す文字列<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>は`Friend`します。</span><span class="sxs-lookup"><span data-stu-id="14521-118">For [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="14521-119">[!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]ターゲットをサポートする XAML をコンパイルするが存在しない; そのため、に渡す値は指定されていません。</span><span class="sxs-lookup"><span data-stu-id="14521-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="14521-120">指定することも<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>(`public`で[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]、`Public`で[!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)])。 ただし、を指定する<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>が頻度の低い実行されるため<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>は既に既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="14521-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Public` in [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="14521-121">その他の値と同じユーザー コードとアクセス レベルの制限など`private`で[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]は関連しない`x:ClassModifier`XAML では、入れ子になったクラスの参照はサポートされていませんし、そのため、<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>修飾子が同じ効果です。</span><span class="sxs-lookup"><span data-stu-id="14521-121">Other values with equivalent user code access-level restrictions, such as `private` in [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="14521-122">セキュリティに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="14521-122">Security Notes</span></span>  
 <span data-ttu-id="14521-123">アクセス レベルで宣言されている`x:ClassModifier`は、特定のフレームワークとその機能によって解釈される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="14521-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="14521-124">WPF には、読み込みし、型のインスタンスを作成する機能が含まれています。 ここで`x:ClassModifier`は`internal`パック URI 参照を使用して、WPF リソースからそのクラスが参照されている場合、します。</span><span class="sxs-lookup"><span data-stu-id="14521-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="14521-125">この場合は、可能性のある他のフレームワークによって実装されるようなその他の結果として使用しない専用に`x:ClassModifier`をすべての可能なインスタンス化をブロックしようとします。</span><span class="sxs-lookup"><span data-stu-id="14521-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14521-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="14521-126">See Also</span></span>  
 [<span data-ttu-id="14521-127">x:Class ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="14521-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="14521-128">WPF における分離コードと XAML</span><span class="sxs-lookup"><span data-stu-id="14521-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="14521-129">x:FieldModifier ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="14521-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [<span data-ttu-id="14521-130">セキュリティ (WPF)</span><span class="sxs-lookup"><span data-stu-id="14521-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="14521-131">WPF から System.Xaml に移行した型</span><span class="sxs-lookup"><span data-stu-id="14521-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
