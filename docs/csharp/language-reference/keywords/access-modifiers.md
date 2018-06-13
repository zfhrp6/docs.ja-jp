---
title: アクセス修飾子 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 9629b1727fc210025256724db8db82b13b63b7db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217169"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="825cf-102">アクセス修飾子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="825cf-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="825cf-103">アクセス修飾子は、メンバーまたは型の宣言されたアクセシビリティを指定するときに使用されるキーワードです。</span><span class="sxs-lookup"><span data-stu-id="825cf-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="825cf-104">ここでは、4 つのアクセス修飾子について説明します。</span><span class="sxs-lookup"><span data-stu-id="825cf-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="825cf-105">アクセス修飾子を使用して、次の 6 つのアクセシビリティ レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="825cf-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="825cf-106">[`public`](public.md): アクセスは無制限です。</span><span class="sxs-lookup"><span data-stu-id="825cf-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="825cf-107">[`protected`](protected.md): コンテナーであるクラス、またはコンテナーであるクラスから派生した型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="825cf-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="825cf-108">[`internal`](internal.md): 現在のアセンブリにアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="825cf-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="825cf-109">[`protected internal`](protected-internal.md): 現在のアセンブリ、またはコンテナーであるクラスから派生した型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="825cf-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="825cf-110">[`private`](private.md): コンテナーである型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="825cf-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="825cf-111">[`private protected`](private-protected.md): 現在のアセンブリ内の、コンテナーであるクラス、またはコンテナーであるクラスから派生した型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="825cf-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="825cf-112">このセクションでは、以下についても説明します。</span><span class="sxs-lookup"><span data-stu-id="825cf-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="825cf-113">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md): 4 つのアクセス修飾子を使用して、6 つのアクセシビリティ レベルを宣言します。</span><span class="sxs-lookup"><span data-stu-id="825cf-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="825cf-114">[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md): プログラムのセクション内で、メンバーを参照できる位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="825cf-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="825cf-115">[アクセシビリティ レベルの使用に関する制限事項](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): 宣言されたアクセシビリティ レベルの使用に関する制限事項をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="825cf-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825cf-116">参照</span><span class="sxs-lookup"><span data-stu-id="825cf-116">See Also</span></span>  
 [<span data-ttu-id="825cf-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="825cf-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="825cf-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="825cf-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="825cf-119">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="825cf-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="825cf-120">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="825cf-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="825cf-121">アクセス キーワード</span><span class="sxs-lookup"><span data-stu-id="825cf-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="825cf-122">修飾子</span><span class="sxs-lookup"><span data-stu-id="825cf-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
