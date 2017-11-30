---
title: "アクセス修飾子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23f99d0925aefde7ef43888d16e888a0943dfc21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="60233-102">アクセス修飾子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="60233-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="60233-103">アクセス修飾子は、メンバーまたは型の宣言されたアクセシビリティを指定するときに使用されるキーワードです。</span><span class="sxs-lookup"><span data-stu-id="60233-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="60233-104">ここでは、4 つのアクセス修飾子について説明します。</span><span class="sxs-lookup"><span data-stu-id="60233-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="60233-105">public</span><span class="sxs-lookup"><span data-stu-id="60233-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="60233-106">protected</span><span class="sxs-lookup"><span data-stu-id="60233-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="60233-107">internal</span><span class="sxs-lookup"><span data-stu-id="60233-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="60233-108">private</span><span class="sxs-lookup"><span data-stu-id="60233-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="60233-109">アクセス修飾子を使用して、次の 6 つのユーザー補助機能レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="60233-109">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="60233-110">`public`: アクセスは無制限です。</span><span class="sxs-lookup"><span data-stu-id="60233-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="60233-111">`protected`: コンテナーであるクラス、またはコンテナーであるクラスから派生した型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="60233-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="60233-112">`internal`: 現在のアセンブリにアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="60233-112">`internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="60233-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): アクセスは、現在のアセンブリまたは外側のクラスから派生した型に制限されます。</span><span class="sxs-lookup"><span data-stu-id="60233-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="60233-114">`private`: コンテナーである型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="60233-114">`private`: Access is limited to the containing type.</span></span>  

 <span data-ttu-id="60233-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): アクセスは、含んでいるクラスまたは現在のアセンブリ内の外側のクラスから派生した型に制限されます。</span><span class="sxs-lookup"><span data-stu-id="60233-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="60233-116">このセクションでは、以下についても説明します。</span><span class="sxs-lookup"><span data-stu-id="60233-116">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="60233-117">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md): 4 つのアクセス修飾子を使用して、ユーザー補助の 6 つのレベルを宣言します。</span><span class="sxs-lookup"><span data-stu-id="60233-117">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="60233-118">[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md): プログラムのセクション内で、メンバーを参照できる位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="60233-118">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="60233-119">[アクセシビリティ レベルの使用に関する制限事項](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): 宣言されたアクセシビリティ レベルの使用に関する制限事項をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="60233-119">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60233-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="60233-120">See Also</span></span>  
 [<span data-ttu-id="60233-121">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="60233-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="60233-122">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="60233-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="60233-123">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="60233-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="60233-124">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="60233-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="60233-125">アクセス キーワード</span><span class="sxs-lookup"><span data-stu-id="60233-125">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="60233-126">修飾子</span><span class="sxs-lookup"><span data-stu-id="60233-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
