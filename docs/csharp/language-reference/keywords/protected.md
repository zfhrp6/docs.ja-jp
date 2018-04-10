---
title: protected (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 18278ed28f899d9030d6056eca9bbe83ebec04c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="protected-c-reference"></a><span data-ttu-id="5a1e6-102">protected (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5a1e6-102">protected (C# Reference)</span></span>
<span data-ttu-id="5a1e6-103">`protected` キーワードはメンバー アクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-103">The `protected` keyword is a member access modifier.</span></span> 

 > <span data-ttu-id="5a1e6-104">このページで対象`protected`アクセスします。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-104">This page covers `protected` access.</span></span> <span data-ttu-id="5a1e6-105">`protected`キーワードはまたの一部、 [ `protected internal` ](./protected-internal.md)と[ `private protected` ](./private-protected.md)アクセス修飾子。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-105">The `protected` keyword is also part of the [`protected internal`](./protected-internal.md) and [`private protected`](./private-protected.md) access modifiers.</span></span> 

<span data-ttu-id="5a1e6-106">protected メンバーは、そのクラス内部と、派生クラスのインスタンスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-106">A protected member is accessible within its class and by derived class instances.</span></span> 

<span data-ttu-id="5a1e6-107">`protected` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
  
## <a name="example"></a><span data-ttu-id="5a1e6-108">例</span><span class="sxs-lookup"><span data-stu-id="5a1e6-108">Example</span></span>  
 <span data-ttu-id="5a1e6-109">派生クラス内で基底クラスの protected メンバーにアクセスできるのは、派生クラスの型を通してアクセスした場合のみです。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="5a1e6-110">たとえば、次のコード セグメントを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-110">For example, consider the following code segment:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 <span data-ttu-id="5a1e6-111">ステートメント `a.x = 10` でエラーが発生します。これは、クラス B のインスタンスではなく、静的メソッド Main 内にあるためです。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="5a1e6-112">構造体は継承できないため、構造体のメンバーを protected にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a1e6-113">例</span><span class="sxs-lookup"><span data-stu-id="5a1e6-113">Example</span></span>  
 <span data-ttu-id="5a1e6-114">この例では、`DerivedPoint` クラスは `Point` から派生しています。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="5a1e6-115">そのため、基底クラスの protected メンバーに、派生クラスから直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 <span data-ttu-id="5a1e6-116">`x` と `y` のアクセス レベルを [private](../../../csharp/language-reference/keywords/private.md) に変更すると、コンパイラによってエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5a1e6-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="5a1e6-117">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="5a1e6-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a1e6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a1e6-118">See Also</span></span>  
 [<span data-ttu-id="5a1e6-119">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="5a1e6-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5a1e6-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5a1e6-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5a1e6-121">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="5a1e6-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5a1e6-122">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="5a1e6-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="5a1e6-123">アクセシビリティ レベル</span><span class="sxs-lookup"><span data-stu-id="5a1e6-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="5a1e6-124">修飾子</span><span class="sxs-lookup"><span data-stu-id="5a1e6-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="5a1e6-125">public</span><span class="sxs-lookup"><span data-stu-id="5a1e6-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="5a1e6-126">private</span><span class="sxs-lookup"><span data-stu-id="5a1e6-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="5a1e6-127">internal</span><span class="sxs-lookup"><span data-stu-id="5a1e6-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="5a1e6-128">[Internal virtual キーワードのセキュリティに関する注意事項](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="5a1e6-128">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>