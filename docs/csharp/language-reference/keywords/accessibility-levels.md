---
title: "アクセシビリティ レベル (C# リファレンス)"
ms.date: 12/06/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 816ee0fab3fae21bff2ffbfcbfe39d04dcf95025
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="b80c3-102">アクセシビリティ レベル (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b80c3-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="b80c3-103">以下に示したのは、メンバーに適用されるアクセシビリティ レベルの宣言です。[public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[private](../../../csharp/language-reference/keywords/private.md) の各アクセス修飾子を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="b80c3-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="b80c3-104">アクセシビリティの宣言</span><span class="sxs-lookup"><span data-stu-id="b80c3-104">Declared accessibility</span></span>|<span data-ttu-id="b80c3-105">説明</span><span class="sxs-lookup"><span data-stu-id="b80c3-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="b80c3-106">アクセスは無制限です。</span><span class="sxs-lookup"><span data-stu-id="b80c3-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="b80c3-107">コンテナーであるクラスまたはそこから派生した型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="b80c3-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="b80c3-108">アクセスは現在のアセンブリに限定されます。</span><span class="sxs-lookup"><span data-stu-id="b80c3-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="b80c3-109">現在のアセンブリ、またはコンテナーであるクラスから派生した型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="b80c3-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="b80c3-110">コンテナーである型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="b80c3-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="b80c3-111">現在のアセンブリ内の、コンテナーであるクラス、またはコンテナーであるクラスから派生した型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="b80c3-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="b80c3-112">C# 7.2 以降で使用可能です。</span><span class="sxs-lookup"><span data-stu-id="b80c3-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="b80c3-113">`protected internal` または `private protected` の組み合わせを使う場合を除き、1 つのメンバーまたは 1 つの型に指定できるアクセス修飾子は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="b80c3-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="b80c3-114">アクセス修飾子を名前空間に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b80c3-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="b80c3-115">名前空間には、アクセス制限がありません。</span><span class="sxs-lookup"><span data-stu-id="b80c3-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="b80c3-116">メンバーが宣言されているコンテキストによっては、決まったアクセシビリティしか宣言できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b80c3-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="b80c3-117">メンバーの宣言にアクセス修飾子が指定されていない場合は、既定のアクセシビリティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b80c3-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="b80c3-118">トップレベルの型 (他の型に対して入れ子にされていない型) に指定できるアクセシビリティは `internal` と `public` だけです。</span><span class="sxs-lookup"><span data-stu-id="b80c3-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="b80c3-119">既定では、そのような型に `internal` のアクセシビリティが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b80c3-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="b80c3-120">入れ子にされた型 (他の型のメンバーになっている型) には、次の表に示したアクセシビリティを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="b80c3-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="b80c3-121">コンテナー</span><span class="sxs-lookup"><span data-stu-id="b80c3-121">Members of</span></span>|<span data-ttu-id="b80c3-122">メンバーの既定のアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="b80c3-122">Default member accessibility</span></span>|<span data-ttu-id="b80c3-123">メンバーに対して宣言できるアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="b80c3-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="b80c3-124">なし</span><span class="sxs-lookup"><span data-stu-id="b80c3-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="b80c3-125">なし</span><span class="sxs-lookup"><span data-stu-id="b80c3-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="b80c3-126">入れ子にされた型のアクセシビリティは、その型の[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)によって決まります。このアクセシビリティ ドメインは、そのメンバーに対して宣言されているアクセシビリティと、そのメンバーの直接のコンテナーである型のアクセシビリティ ドメインの両方によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="b80c3-126">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="b80c3-127">ただし、入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを上回ることはできません。</span><span class="sxs-lookup"><span data-stu-id="b80c3-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b80c3-128">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="b80c3-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b80c3-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="b80c3-129">See Also</span></span>  
 [<span data-ttu-id="b80c3-130">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="b80c3-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b80c3-131">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b80c3-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b80c3-132">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="b80c3-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b80c3-133">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="b80c3-133">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="b80c3-134">アクセシビリティ ドメイン</span><span class="sxs-lookup"><span data-stu-id="b80c3-134">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="b80c3-135">アクセシビリティ レベルの使用に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="b80c3-135">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="b80c3-136">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="b80c3-136">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="b80c3-137">public</span><span class="sxs-lookup"><span data-stu-id="b80c3-137">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="b80c3-138">private</span><span class="sxs-lookup"><span data-stu-id="b80c3-138">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="b80c3-139">protected</span><span class="sxs-lookup"><span data-stu-id="b80c3-139">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="b80c3-140">internal</span><span class="sxs-lookup"><span data-stu-id="b80c3-140">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
