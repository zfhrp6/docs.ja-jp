---
title: Attributes1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 89e892a379c7540cf67488471ae5281a4c4b86f4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="attributes"></a><span data-ttu-id="fefaf-102">属性</span><span class="sxs-lookup"><span data-stu-id="fefaf-102">Attributes</span></span>
<span data-ttu-id="fefaf-103"><xref:System.Attribute?displayProperty=nameWithType>カスタム属性を定義するために使用する基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="fefaf-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="fefaf-104">属性は、アセンブリ、型、メンバー、およびパラメーターなどのプログラミング要素に追加できる注釈です。</span><span class="sxs-lookup"><span data-stu-id="fefaf-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="fefaf-105">これらは、アセンブリのメタデータには保存され、リフレクション Api を使用して実行時にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="fefaf-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="fefaf-106">たとえば、フレームワークの定義、 <xref:System.ObsoleteAttribute>、型またはメンバーは廃止されていることを示すために、型またはメンバーに適用できます。</span><span class="sxs-lookup"><span data-stu-id="fefaf-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="fefaf-107">属性は、属性に関連するその他のデータを伝達する 1 つまたは複数のプロパティを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="fefaf-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="fefaf-108">たとえば、`ObsoleteAttribute`のリリースに関する追加情報を実行できる、型またはメンバーが使用されなくなったと廃止された API を置き換える新しい Api の説明。</span><span class="sxs-lookup"><span data-stu-id="fefaf-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="fefaf-109">属性が適用されるときに、属性の一部のプロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fefaf-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="fefaf-110">これらと呼ばれるに必要なプロパティまたは必須の引数のため、位置指定のコンス トラクターのパラメーターとして表されます。</span><span class="sxs-lookup"><span data-stu-id="fefaf-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="fefaf-111">たとえば、<xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A>のプロパティ、<xref:System.Diagnostics.ConditionalAttribute>必要なプロパティです。</span><span class="sxs-lookup"><span data-stu-id="fefaf-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="fefaf-112">プロパティがないとは限りません属性が適用されたときに指定するのには、省略可能なプロパティ (または省略可能な引数) と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fefaf-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="fefaf-113">設定可能なプロパティによって表されます。</span><span class="sxs-lookup"><span data-stu-id="fefaf-113">They are represented by settable properties.</span></span> <span data-ttu-id="fefaf-114">コンパイラでは、属性が適用されるときに、これらのプロパティを設定する特別な構文を提供します。</span><span class="sxs-lookup"><span data-stu-id="fefaf-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="fefaf-115">たとえば、<xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>プロパティは省略可能な引数を表します。</span><span class="sxs-lookup"><span data-stu-id="fefaf-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="fefaf-116">**✓ しないで**「属性」サフィックスを持つカスタム属性クラスの名前</span><span class="sxs-lookup"><span data-stu-id="fefaf-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="fefaf-117">**✓ しないで**適用、<xref:System.AttributeUsageAttribute>カスタム属性にします。</span><span class="sxs-lookup"><span data-stu-id="fefaf-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="fefaf-118">**✓ しないで**省略可能な引数の設定可能なプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="fefaf-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="fefaf-119">**✓ しないで**必須の引数の取得専用のプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="fefaf-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="fefaf-120">**✓ しないで**必須の引数に対応するプロパティを初期化するコンス トラクターのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="fefaf-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="fefaf-121">各パラメーターにすることは、同じ名前 (大文字小文字が異なる) には、対応するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="fefaf-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="fefaf-122">**避け x**省略可能な引数に対応するプロパティを初期化するコンス トラクターのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="fefaf-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="fefaf-123">つまり、コンス トラクターと、set アクセス操作子の両方で設定できるプロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="fefaf-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="fefaf-124">このガイドラインは、明示的に指定する引数は省略可能なこれが必要であり、2 つの方法で同じことを行う必要はなくなります。</span><span class="sxs-lookup"><span data-stu-id="fefaf-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="fefaf-125">**避け x**カスタム属性のコンス トラクターのオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="fefaf-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="fefaf-126">コンス トラクターの 1 つだけのことを明確に伝達をユーザーにどの引数が必須および省略可能な。</span><span class="sxs-lookup"><span data-stu-id="fefaf-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="fefaf-127">**✓ しないで**可能であれば、カスタム属性クラスをシールします。</span><span class="sxs-lookup"><span data-stu-id="fefaf-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="fefaf-128">これにより、属性の参照も高速です。</span><span class="sxs-lookup"><span data-stu-id="fefaf-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="fefaf-129">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="fefaf-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fefaf-130">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="fefaf-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefaf-131">参照</span><span class="sxs-lookup"><span data-stu-id="fefaf-131">See Also</span></span>  
 [<span data-ttu-id="fefaf-132">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="fefaf-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="fefaf-133">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="fefaf-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
