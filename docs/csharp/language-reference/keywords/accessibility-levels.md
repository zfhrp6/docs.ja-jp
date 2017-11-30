---
title: "アクセシビリティ レベル (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="bb1d9-102">アクセシビリティ レベル (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="bb1d9-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="bb1d9-103">以下に示したのは、メンバーに適用されるアクセシビリティ レベルの宣言です。[public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[private](../../../csharp/language-reference/keywords/private.md) の各アクセス修飾子を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="bb1d9-104">アクセシビリティの宣言</span><span class="sxs-lookup"><span data-stu-id="bb1d9-104">Declared accessibility</span></span>|<span data-ttu-id="bb1d9-105">説明</span><span class="sxs-lookup"><span data-stu-id="bb1d9-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="bb1d9-106">アクセスは無制限です。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="bb1d9-107">コンテナーであるクラスまたはそこから派生した型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="bb1d9-108">アクセスは現在のアセンブリに限定されます。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="bb1d9-109">現在のアセンブリ、またはコンテナーであるクラスから派生した型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="bb1d9-110">コンテナーである型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="bb1d9-111">アクセスは、含んでいるクラスまたは現在のアセンブリ内の外側のクラスから派生した型に制限されます。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>|  
  
 <span data-ttu-id="bb1d9-112">1 つだけアクセス修飾子は使用メンバーまたは型、以外を使用するときに、`protected internal`または`private protected`の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-112">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="bb1d9-113">アクセス修飾子を名前空間に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-113">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="bb1d9-114">名前空間には、アクセス制限がありません。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-114">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="bb1d9-115">メンバーが宣言されているコンテキストによっては、決まったアクセシビリティしか宣言できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-115">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="bb1d9-116">メンバーの宣言にアクセス修飾子が指定されていない場合は、既定のアクセシビリティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-116">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="bb1d9-117">トップレベルの型 (他の型に対して入れ子にされていない型) に指定できるアクセシビリティは `internal` と `public` だけです。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-117">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="bb1d9-118">既定では、そのような型に `internal` のアクセシビリティが適用されます。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-118">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="bb1d9-119">入れ子にされた型 (他の型のメンバーになっている型) には、次の表に示したアクセシビリティを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-119">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="bb1d9-120">コンテナー</span><span class="sxs-lookup"><span data-stu-id="bb1d9-120">Members of</span></span>|<span data-ttu-id="bb1d9-121">メンバーの既定のアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="bb1d9-121">Default member accessibility</span></span>|<span data-ttu-id="bb1d9-122">メンバーに対して宣言できるアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="bb1d9-122">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="bb1d9-123">なし</span><span class="sxs-lookup"><span data-stu-id="bb1d9-123">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="bb1d9-124">なし</span><span class="sxs-lookup"><span data-stu-id="bb1d9-124">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="bb1d9-125">入れ子にされた型のアクセシビリティは、その型の[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)によって決まります。このアクセシビリティ ドメインは、そのメンバーに対して宣言されているアクセシビリティと、そのメンバーの直接のコンテナーである型のアクセシビリティ ドメインの両方によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-125">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="bb1d9-126">ただし、入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを上回ることはできません。</span><span class="sxs-lookup"><span data-stu-id="bb1d9-126">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bb1d9-127">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="bb1d9-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb1d9-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb1d9-128">See Also</span></span>  
 [<span data-ttu-id="bb1d9-129">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="bb1d9-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bb1d9-130">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="bb1d9-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bb1d9-131">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="bb1d9-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="bb1d9-132">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="bb1d9-132">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="bb1d9-133">アクセシビリティ ドメイン</span><span class="sxs-lookup"><span data-stu-id="bb1d9-133">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="bb1d9-134">アクセシビリティ レベルの使用に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="bb1d9-134">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="bb1d9-135">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="bb1d9-135">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="bb1d9-136">public</span><span class="sxs-lookup"><span data-stu-id="bb1d9-136">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="bb1d9-137">private</span><span class="sxs-lookup"><span data-stu-id="bb1d9-137">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="bb1d9-138">protected</span><span class="sxs-lookup"><span data-stu-id="bb1d9-138">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="bb1d9-139">internal</span><span class="sxs-lookup"><span data-stu-id="bb1d9-139">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
