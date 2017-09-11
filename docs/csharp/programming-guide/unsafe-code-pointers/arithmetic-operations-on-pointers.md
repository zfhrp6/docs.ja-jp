---
title: "ポインターに対する算術演算 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 18
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
ms.openlocfilehash: d40d44f8be590a909ff059b0fa84efb598fcf263
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="f215c-102">ポインターに対する算術演算 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f215c-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="f215c-103">このトピックでは、算術演算子 `+` と  **-**  を使用したポインター操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="f215c-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f215c-104">void ポインターには、算術演算を実行できません。</span><span class="sxs-lookup"><span data-stu-id="f215c-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="f215c-105">ポインターに対する数値の加算と減算</span><span class="sxs-lookup"><span data-stu-id="f215c-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="f215c-106">型が [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) のいずれかである値 `n` は、`void*` 型以外のあらゆるポインター `p` に加算できます。</span><span class="sxs-lookup"><span data-stu-id="f215c-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="f215c-107">結果の `p+n` は `n * sizeof(p) to the address of p` を加算した結果を表すポインターです。</span><span class="sxs-lookup"><span data-stu-id="f215c-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="f215c-108">同様に、`p-n` は `p` のアドレスから `n * sizeof(p)` を減算した結果を表すポインターです。</span><span class="sxs-lookup"><span data-stu-id="f215c-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="f215c-109">ポインターの減算</span><span class="sxs-lookup"><span data-stu-id="f215c-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="f215c-110">同じ型のポインターを減算することもできます。</span><span class="sxs-lookup"><span data-stu-id="f215c-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="f215c-111">結果は常に `long` 型になります。</span><span class="sxs-lookup"><span data-stu-id="f215c-111">The result is always of the type `long`.</span></span> <span data-ttu-id="f215c-112">たとえば場合、`p1` と `p2` が `pointer-type*` 型のポインターである場合、式 `p1-p2` の結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f215c-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="f215c-113">算術演算がポインターのドメインをオーバーフローしても、例外は生成されません。生じる結果は実装によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f215c-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f215c-114">例</span><span class="sxs-lookup"><span data-stu-id="f215c-114">Example</span></span>  
 <span data-ttu-id="f215c-115">[!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f215c-115">[!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]</span></span>  
  
 <span data-ttu-id="f215c-116">[!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f215c-116">[!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f215c-117">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f215c-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f215c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f215c-118">See Also</span></span>  
 <span data-ttu-id="f215c-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f215c-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f215c-120">[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="f215c-120">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="f215c-121">[ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="f215c-121">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="f215c-122">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="f215c-122">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="f215c-123">[ポインターの操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span><span class="sxs-lookup"><span data-stu-id="f215c-123">[Manipulating Pointers](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span></span>  
 <span data-ttu-id="f215c-124">[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="f215c-124">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="f215c-125">[型](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="f215c-125">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="f215c-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="f215c-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="f215c-127">[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f215c-127">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="f215c-128">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f215c-128">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

