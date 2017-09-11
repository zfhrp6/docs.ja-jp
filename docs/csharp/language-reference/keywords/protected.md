---
title: "protected (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- protected
- protected_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
caps.latest.revision: 20
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
ms.openlocfilehash: c3d24389f66edec313d4f5238b0aee02518e33b7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="protected-c-reference"></a><span data-ttu-id="1fd95-102">protected (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1fd95-102">protected (C# Reference)</span></span>
<span data-ttu-id="1fd95-103">`protected` キーワードはメンバー アクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="1fd95-103">The `protected` keyword is a member access modifier.</span></span> <span data-ttu-id="1fd95-104">protected メンバーは、そのクラス内部と、派生クラスのインスタンスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1fd95-104">A protected member is accessible within its class and by derived class instances.</span></span> <span data-ttu-id="1fd95-105">`protected` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fd95-105">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fd95-106">例</span><span class="sxs-lookup"><span data-stu-id="1fd95-106">Example</span></span>  
 <span data-ttu-id="1fd95-107">派生クラス内で基底クラスの protected メンバーにアクセスできるのは、派生クラスの型を通してアクセスした場合のみです。</span><span class="sxs-lookup"><span data-stu-id="1fd95-107">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="1fd95-108">たとえば、次のコード セグメントを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="1fd95-108">For example, consider the following code segment:</span></span>  
  
 <span data-ttu-id="1fd95-109">[!code-cs[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1fd95-109">[!code-cs[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]</span></span>  
  
 <span data-ttu-id="1fd95-110">ステートメント `a.x = 10` でエラーが発生します。これは、クラス B のインスタンスではなく、静的メソッド Main 内にあるためです。</span><span class="sxs-lookup"><span data-stu-id="1fd95-110">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="1fd95-111">構造体は継承できないため、構造体のメンバーを protected にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1fd95-111">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fd95-112">例</span><span class="sxs-lookup"><span data-stu-id="1fd95-112">Example</span></span>  
 <span data-ttu-id="1fd95-113">この例では、`DerivedPoint` クラスは `Point` から派生しています。</span><span class="sxs-lookup"><span data-stu-id="1fd95-113">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="1fd95-114">そのため、基底クラスの protected メンバーに、派生クラスから直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1fd95-114">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 <span data-ttu-id="1fd95-115">[!code-cs[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="1fd95-115">[!code-cs[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]</span></span>  
  
 <span data-ttu-id="1fd95-116">`x` と `y` のアクセス レベルを [private](../../../csharp/language-reference/keywords/private.md) に変更すると、コンパイラによってエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1fd95-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="1fd95-117">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1fd95-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1fd95-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fd95-118">See Also</span></span>  
 <span data-ttu-id="1fd95-119">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1fd95-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1fd95-120">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1fd95-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1fd95-121">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1fd95-121">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1fd95-122">[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1fd95-122">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="1fd95-123">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="1fd95-123">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="1fd95-124">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1fd95-124">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="1fd95-125">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="1fd95-125">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="1fd95-126">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="1fd95-126">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 [<span data-ttu-id="1fd95-127">internal</span><span class="sxs-lookup"><span data-stu-id="1fd95-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

