---
title: "x:FieldModifier ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ed50dd2aff1702543789f06939f7c2bc4b3dd83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xfieldmodifier-directive"></a><span data-ttu-id="db270-102">x:FieldModifier ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="db270-102">x:FieldModifier Directive</span></span>
<span data-ttu-id="db270-103">XAML のコンパイルの動作を変更してでの名前付きオブジェクトの参照フィールドが定義されているように<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>の代わりにアクセス、<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="db270-103">Modifies XAML compilation behavior so that fields for named object references are defined with <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> access instead of the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> default behavior.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="db270-104">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="db270-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="db270-105">XAML 値</span><span class="sxs-lookup"><span data-stu-id="db270-105">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db270-106">*Public*</span><span class="sxs-lookup"><span data-stu-id="db270-106">*Public*</span></span>|<span data-ttu-id="db270-107">正確な指定した文字列を指定する<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>のために使用される分離コードのプログラミング言語によって異なります。</span><span class="sxs-lookup"><span data-stu-id="db270-107">The exact string you pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that is used.</span></span> <span data-ttu-id="db270-108">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db270-108">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="db270-109">依存関係</span><span class="sxs-lookup"><span data-stu-id="db270-109">Dependencies</span></span>  
 <span data-ttu-id="db270-110">XAML の運用環境で使用する場合`x:FieldModifier`任意の場所では、その XAML の運用環境のルート要素を宣言する必要があります、 [X:class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)です。</span><span class="sxs-lookup"><span data-stu-id="db270-110">If a XAML production uses `x:FieldModifier` anywhere, the root element of that XAML production must declare an [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db270-111">コメント</span><span class="sxs-lookup"><span data-stu-id="db270-111">Remarks</span></span>  
 <span data-ttu-id="db270-112">`x:FieldModifier`無効、クラスまたはそのメンバーの一般的なアクセス レベルを宣言するためです。</span><span class="sxs-lookup"><span data-stu-id="db270-112">`x:FieldModifier` is not relevant for declaring the general access level of a class or its members.</span></span> <span data-ttu-id="db270-113">XAML 処理の動作にのみ関連する XAML の運用環境の一部である特定の XAML オブジェクトが処理され、アプリケーションのオブジェクト グラフに可能性のあるアクセス可能なオブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="db270-113">It is relevant only for XAML-processing behavior when a particular XAML object that is part of a XAML production is processed, and becomes an object that is potentially accessible in the object graph of an application.</span></span> <span data-ttu-id="db270-114">既定では、このようなオブジェクトのフィールド参照は厳重に保管され、コントロールのコンシューマーは、オブジェクト グラフを直接変更できなきます。</span><span class="sxs-lookup"><span data-stu-id="db270-114">By default, the field reference for such an object is kept private, which prevents control consumers from modifying the object graph directly.</span></span> <span data-ttu-id="db270-115">代わりに、コントロール コンシューマーでは有効なプログラミング モデルなどのレイアウト ルート、子要素のコレクション、専用のパブリック プロパティを取得することによって標準のパターンを使用して、オブジェクト グラフを変更する必要と。</span><span class="sxs-lookup"><span data-stu-id="db270-115">Instead, control consumers are expected to modify the object graph by using standard patterns that are enabled by programming models, such as by obtaining the layout root, the child element collections, the dedicated public properties, and so on.</span></span>  
  
 <span data-ttu-id="db270-116">値、`x:FieldModifier`属性は、プログラミング言語によって異なります、特定のフレームワークでの目的が異なります。</span><span class="sxs-lookup"><span data-stu-id="db270-116">The value for the `x:FieldModifier` attribute varies by programming language, and its purpose can vary in specific frameworks.</span></span> <span data-ttu-id="db270-117">使用する文字列は、各言語の実装に依存その<xref:System.CodeDom.Compiler.CodeDomProvider>と返しますの意味を定義する型コンバーター<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>、その言語は大文字小文字を区別するかどうかとします。</span><span class="sxs-lookup"><span data-stu-id="db270-117">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="db270-118">[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]、指定に渡す文字列<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>は`public`します。</span><span class="sxs-lookup"><span data-stu-id="db270-118">For [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `public`.</span></span>  
  
-   <span data-ttu-id="db270-119">[!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)]、指定に渡す文字列<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>は`Public`します。</span><span class="sxs-lookup"><span data-stu-id="db270-119">For [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `Public`.</span></span>  
  
-   <span data-ttu-id="db270-120">[!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]XAML のターゲット現在存在しません。 そのため、渡す文字列は未定義です。</span><span class="sxs-lookup"><span data-stu-id="db270-120">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets for XAML currently exist; therefore, the string to pass is undefined.</span></span>  
  
 <span data-ttu-id="db270-121">指定することも<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>(`internal`で[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]、`Friend`で[!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) が指定する<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>はほとんどありませんので`NotPublic`動作は、既に既定値として。</span><span class="sxs-lookup"><span data-stu-id="db270-121">You can also specify <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` in [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Friend` in [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) but specifying <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is unusual because `NotPublic` as the behavior is already the default.</span></span>  
  
 <span data-ttu-id="db270-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>XAML をコンパイルされたアセンブリの外側のコードが XAML で作成された要素へのアクセスを必要があることが頻繁ではないために、既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="db270-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is the default behavior because it is infrequent that code outside the assembly that compiled the XAML needs access to a XAML-created element.</span></span> <span data-ttu-id="db270-123">具体的に設定していない場合、XAML のコンパイルの動作と WPF のセキュリティ アーキテクチャは、public として要素のインスタンスを格納するフィールドを宣言しませんが、`x:FieldModifier`パブリック アクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="db270-123">WPF security architecture together with XAML compilation behavior will not declare fields that store element instances as public, unless you specifically set the `x:FieldModifier` to allow public access.</span></span>  
  
 <span data-ttu-id="db270-124">`x:FieldModifier`のみを持つ要素の関係、 [X:name ディレクティブ](../../../docs/framework/xaml-services/x-name-directive.md)その名前は public では後にフィールドを参照に使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="db270-124">`x:FieldModifier` is only relevant for elements with an [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md) because that name is used to reference the field after it is public.</span></span>  
  
 <span data-ttu-id="db270-125">既定では、ルート要素の部分クラスはパブリックです。ただし、することができます、パブリックでないを使用して、 [X:classmodifier ディレクティブ](../../../docs/framework/xaml-services/x-classmodifier-directive.md)です。</span><span class="sxs-lookup"><span data-stu-id="db270-125">By default, the partial class for the root element is public; however, you can make it nonpublic by using the [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).</span></span> <span data-ttu-id="db270-126">[X:classmodifier ディレクティブ](../../../docs/framework/xaml-services/x-classmodifier-directive.md)ルート要素クラスのインスタンスのアクセス レベルにも影響します。</span><span class="sxs-lookup"><span data-stu-id="db270-126">The [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md) also affects the access level of the instance of the root element class.</span></span> <span data-ttu-id="db270-127">両方を配置できる`x:Name`と`x:FieldModifier`ルートに要素が、これだけのパブリック フィールドのコピーを作成は true。 ルート要素クラスのアクセス レベルも、ルート要素によって制御されます[X:classmodifier ディレクティブ](../../../docs/framework/xaml-services/x-classmodifier-directive.md)です。</span><span class="sxs-lookup"><span data-stu-id="db270-127">You can put both `x:Name` and `x:FieldModifier` on the root element, but this only makes a public field copy of the root element, with the true root element class access level still controlled by [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db270-128">参照</span><span class="sxs-lookup"><span data-stu-id="db270-128">See Also</span></span>  
 [<span data-ttu-id="db270-129">WPF における XAML とカスタム クラス</span><span class="sxs-lookup"><span data-stu-id="db270-129">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [<span data-ttu-id="db270-130">WPF における分離コードと XAML</span><span class="sxs-lookup"><span data-stu-id="db270-130">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="db270-131">x:Name ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="db270-131">x:Name Directive</span></span>](../../../docs/framework/xaml-services/x-name-directive.md)  
 [<span data-ttu-id="db270-132">WPF アプリケーション (WPF) のビルド</span><span class="sxs-lookup"><span data-stu-id="db270-132">Building a WPF Application (WPF)</span></span>](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="db270-133">x:ClassModifier ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="db270-133">x:ClassModifier Directive</span></span>](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
