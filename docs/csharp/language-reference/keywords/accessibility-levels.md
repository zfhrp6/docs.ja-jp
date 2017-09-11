---
title: "アクセシビリティ レベル (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 796802a407c486c1df5332d5b4920467f3a1171b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="267ce-102">アクセシビリティ レベル (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="267ce-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="267ce-103">以下に示したのは、メンバーに適用されるアクセシビリティ レベルの宣言です。[public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[private](../../../csharp/language-reference/keywords/private.md) の各アクセス修飾子を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="267ce-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="267ce-104">アクセシビリティの宣言</span><span class="sxs-lookup"><span data-stu-id="267ce-104">Declared accessibility</span></span>|<span data-ttu-id="267ce-105">説明</span><span class="sxs-lookup"><span data-stu-id="267ce-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="267ce-106">アクセスは無制限です。</span><span class="sxs-lookup"><span data-stu-id="267ce-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="267ce-107">コンテナーであるクラスまたはそこから派生した型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="267ce-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="267ce-108">アクセスは現在のアセンブリに限定されます。</span><span class="sxs-lookup"><span data-stu-id="267ce-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="267ce-109">現在のアセンブリ、またはコンテナーであるクラスから派生した型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="267ce-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="267ce-110">コンテナーである型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="267ce-110">Access is limited to the containing type.</span></span>|  
  
 <span data-ttu-id="267ce-111">`protected internal` の組み合わせを使う場合を除き、1 つのメンバーまたは 1 つの型に指定できるアクセス修飾子は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="267ce-111">Only one access modifier is allowed for a member or type, except when you use the `protected internal` combination.</span></span>  
  
 <span data-ttu-id="267ce-112">アクセス修飾子を名前空間に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="267ce-112">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="267ce-113">名前空間には、アクセス制限がありません。</span><span class="sxs-lookup"><span data-stu-id="267ce-113">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="267ce-114">メンバーが宣言されているコンテキストによっては、決まったアクセシビリティしか宣言できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="267ce-114">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="267ce-115">メンバーの宣言にアクセス修飾子が指定されていない場合は、既定のアクセシビリティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="267ce-115">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="267ce-116">トップレベルの型 (他の型に対して入れ子にされていない型) に指定できるアクセシビリティは `internal` と `public` だけです。</span><span class="sxs-lookup"><span data-stu-id="267ce-116">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="267ce-117">既定では、そのような型に `internal` のアクセシビリティが適用されます。</span><span class="sxs-lookup"><span data-stu-id="267ce-117">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="267ce-118">入れ子にされた型 (他の型のメンバーになっている型) には、次の表に示したアクセシビリティを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="267ce-118">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="267ce-119">コンテナー</span><span class="sxs-lookup"><span data-stu-id="267ce-119">Members of</span></span>|<span data-ttu-id="267ce-120">メンバーの既定のアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="267ce-120">Default member accessibility</span></span>|<span data-ttu-id="267ce-121">メンバーに対して宣言できるアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="267ce-121">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="267ce-122">なし</span><span class="sxs-lookup"><span data-stu-id="267ce-122">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal`|  
|`interface`|`public`|<span data-ttu-id="267ce-123">なし</span><span class="sxs-lookup"><span data-stu-id="267ce-123">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="267ce-124">入れ子にされた型のアクセシビリティは、その型の[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)によって決まります。このアクセシビリティ ドメインは、そのメンバーに対して宣言されているアクセシビリティと、そのメンバーの直接のコンテナーである型のアクセシビリティ ドメインの両方によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="267ce-124">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="267ce-125">ただし、入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを上回ることはできません。</span><span class="sxs-lookup"><span data-stu-id="267ce-125">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="267ce-126">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="267ce-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="267ce-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="267ce-127">See Also</span></span>  
 <span data-ttu-id="267ce-128">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-128">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="267ce-129">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="267ce-130">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-130">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="267ce-131">[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-131">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="267ce-132">[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-132">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md) </span></span>  
 <span data-ttu-id="267ce-133">[アクセシビリティ レベルの使用に関する制限事項](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-133">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span></span>  
 <span data-ttu-id="267ce-134">[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-134">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="267ce-135">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-135">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="267ce-136">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-136">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="267ce-137">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="267ce-137">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="267ce-138">internal</span><span class="sxs-lookup"><span data-stu-id="267ce-138">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

