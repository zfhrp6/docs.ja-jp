---
title: "アクセス修飾子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: 15
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
ms.openlocfilehash: a3ad46580561500d9f011da4997007023a3bc844
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="14aa4-102">アクセス修飾子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="14aa4-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="14aa4-103">アクセス修飾子は、メンバーまたは型の宣言されたアクセシビリティを指定するときに使用されるキーワードです。</span><span class="sxs-lookup"><span data-stu-id="14aa4-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="14aa4-104">ここでは、4 つのアクセス修飾子について説明します。</span><span class="sxs-lookup"><span data-stu-id="14aa4-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="14aa4-105">public</span><span class="sxs-lookup"><span data-stu-id="14aa4-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="14aa4-106">protected</span><span class="sxs-lookup"><span data-stu-id="14aa4-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="14aa4-107">internal</span><span class="sxs-lookup"><span data-stu-id="14aa4-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="14aa4-108">private</span><span class="sxs-lookup"><span data-stu-id="14aa4-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="14aa4-109">アクセス修飾子を使用して、次の 5 つのアクセシビリティ レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="14aa4-109">The following five accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="14aa4-110">`public`: アクセスは無制限です。</span><span class="sxs-lookup"><span data-stu-id="14aa4-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="14aa4-111">`protected`: コンテナーであるクラス、またはコンテナーであるクラスから派生した型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="14aa4-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="14aa4-112">`Internal`: 現在のアセンブリにアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="14aa4-112">`Internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="14aa4-113">[保護された内部](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md): 現在のアセンブリ、またはコンテナーであるクラスから派生した型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="14aa4-113">[protected internal](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="14aa4-114">`private`: コンテナーである型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="14aa4-114">`private`: Access is limited to the containing type.</span></span>  
  
 <span data-ttu-id="14aa4-115">このセクションでは、以下についても説明します。</span><span class="sxs-lookup"><span data-stu-id="14aa4-115">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="14aa4-116">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md): 4 つのアクセス修飾子を使用して、5 つのアクセシビリティ レベルを宣言します。</span><span class="sxs-lookup"><span data-stu-id="14aa4-116">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare five levels of accessibility.</span></span>  
  
-   <span data-ttu-id="14aa4-117">[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md): プログラムのセクション内で、メンバーを参照できる位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="14aa4-117">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="14aa4-118">[アクセシビリティ レベルの使用に関する制限事項](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): 宣言されたアクセシビリティ レベルの使用に関する制限事項をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="14aa4-118">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14aa4-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="14aa4-119">See Also</span></span>  
 <span data-ttu-id="14aa4-120">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="14aa4-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="14aa4-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="14aa4-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="14aa4-122">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="14aa4-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="14aa4-123">[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="14aa4-123">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="14aa4-124">[アクセス キーワード](../../../csharp/language-reference/keywords/access-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="14aa4-124">[Access Keywords](../../../csharp/language-reference/keywords/access-keywords.md) </span></span>  
 [<span data-ttu-id="14aa4-125">修飾子</span><span class="sxs-lookup"><span data-stu-id="14aa4-125">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

