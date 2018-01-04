---
title: "入れ子にされた型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 389ba73c4509f41f6c2cf86363e59ea720eb3c9f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="nested-types"></a><span data-ttu-id="565a9-102">入れ子にされた型</span><span class="sxs-lookup"><span data-stu-id="565a9-102">Nested Types</span></span>
<span data-ttu-id="565a9-103">入れ子になった型は、それを囲む型と呼ばれる別の種類のスコープ内で定義された型です。</span><span class="sxs-lookup"><span data-stu-id="565a9-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="565a9-104">入れ子になった型は、その外側の型のすべてのメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="565a9-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="565a9-105">たとえば、それを囲む型のすべての先祖で定義されたフィールドを保護して、それを囲む型で定義されてプライベート フィールドにアクセス権を持ちます。</span><span class="sxs-lookup"><span data-stu-id="565a9-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="565a9-106">一般に、入れ子にされた型慎重に使用します。</span><span class="sxs-lookup"><span data-stu-id="565a9-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="565a9-107">直接呼び出すべきではないいくつかの理由があります。</span><span class="sxs-lookup"><span data-stu-id="565a9-107">There are several reasons for this.</span></span> <span data-ttu-id="565a9-108">一部の開発者は、概念を完全に習熟していません。</span><span class="sxs-lookup"><span data-stu-id="565a9-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="565a9-109">これらの開発者、たとえば、問題がありますの入れ子にされた型の変数を宣言する構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="565a9-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="565a9-110">入れ子にされた型は、外側の型とも非常に密接に結び付いているし、そのため、汎用的な型にすることが適していません。</span><span class="sxs-lookup"><span data-stu-id="565a9-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="565a9-111">入れ子にされた型は、その外側の型の実装の詳細をモデル化に最適です。</span><span class="sxs-lookup"><span data-stu-id="565a9-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="565a9-112">エンドユーザーは、入れ子にされた型の変数を宣言することはほとんどなく、入れ子にされた型を明示的にインスタンス化することはほぼありません必要があります。</span><span class="sxs-lookup"><span data-stu-id="565a9-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="565a9-113">たとえば、コレクションの列挙子は、そのコレクションの入れ子にされた型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="565a9-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="565a9-114">列挙子は通常、それを囲む型でインスタンス化され、多くの言語では、foreach ステートメントをサポート、列挙子変数まれであるために、宣言するのには、エンドユーザーがします。</span><span class="sxs-lookup"><span data-stu-id="565a9-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="565a9-115">**✓ しないで**入れ子にされた型とその外側の型間の関係のあるメンバーのアクセシビリティのセマンティクスは次のことをお勧めときに、入れ子にされた型を使用します。</span><span class="sxs-lookup"><span data-stu-id="565a9-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="565a9-116">**X しないで**論理的なグループとしてパブリック入れ子にされた型を使用して構築以外の場合はこの名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="565a9-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="565a9-117">**避け x**入れ子にされた型をパブリックに公開します。</span><span class="sxs-lookup"><span data-stu-id="565a9-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="565a9-118">唯一の例外は、入れ子にされた型の変数がサブクラスまたはその他の高度なカスタマイズのシナリオなど、まれなシナリオでのみ宣言する必要があるかどうかです。</span><span class="sxs-lookup"><span data-stu-id="565a9-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="565a9-119">**X しないで**型が、含んでいる型の外部で参照されている可能性が高い場合は、入れ子にされた型を使用します。</span><span class="sxs-lookup"><span data-stu-id="565a9-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="565a9-120">たとえば、クラスに定義されたメソッドに渡される列挙型であり、いないクラスに入れ子にされた型として定義すべきです。</span><span class="sxs-lookup"><span data-stu-id="565a9-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="565a9-121">**X しないで**クライアント コードでインスタンス化する必要がある場合は、入れ子にされた型を使用します。</span><span class="sxs-lookup"><span data-stu-id="565a9-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="565a9-122">型にパブリック コンス トラクターがある場合は、その必要があります可能性があります入れ子にします。</span><span class="sxs-lookup"><span data-stu-id="565a9-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="565a9-123">型が、独自のフレームワーク内の場所を示すためには、型はインスタンス化することができる場合 (できます作成し、使用して、外側の型を使用することがなく破棄)、したがって必要がある入れ子になっていないとします。</span><span class="sxs-lookup"><span data-stu-id="565a9-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="565a9-124">内部の型は広く再利用できません、リレーションシップがない場合、外部型の外部で外側の型と責任も負わないものです。</span><span class="sxs-lookup"><span data-stu-id="565a9-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="565a9-125">**X しないで**インターフェイスのメンバーとして入れ子にされた型を定義します。</span><span class="sxs-lookup"><span data-stu-id="565a9-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="565a9-126">多くの言語は、このような構造をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="565a9-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="565a9-127">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="565a9-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="565a9-128">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="565a9-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565a9-129">参照</span><span class="sxs-lookup"><span data-stu-id="565a9-129">See Also</span></span>  
 [<span data-ttu-id="565a9-130">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="565a9-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="565a9-131">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="565a9-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
