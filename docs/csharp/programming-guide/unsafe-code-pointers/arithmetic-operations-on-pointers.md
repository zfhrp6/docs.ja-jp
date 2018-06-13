---
title: ポインターに対する算術演算 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: c40b125e42649093aa1f1fe860a3e8f5d2690359
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324302"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="9a4a8-102">ポインターに対する算術演算 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="9a4a8-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="9a4a8-103">このトピックでは、算術演算子 `+` と **-** を使用したポインター操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a4a8-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a4a8-104">void ポインターには、算術演算を実行できません。</span><span class="sxs-lookup"><span data-stu-id="9a4a8-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="9a4a8-105">ポインターに対する数値の加算と減算</span><span class="sxs-lookup"><span data-stu-id="9a4a8-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="9a4a8-106">型が [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) のいずれかである値 `n` は、`void*` 型以外のあらゆるポインター `p` に加算できます。</span><span class="sxs-lookup"><span data-stu-id="9a4a8-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="9a4a8-107">結果の `p+n` は `n * sizeof(p) to the address of p` を加算した結果を表すポインターです。</span><span class="sxs-lookup"><span data-stu-id="9a4a8-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="9a4a8-108">同様に、`p-n` は `p` のアドレスから `n * sizeof(p)` を減算した結果を表すポインターです。</span><span class="sxs-lookup"><span data-stu-id="9a4a8-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="9a4a8-109">ポインターの減算</span><span class="sxs-lookup"><span data-stu-id="9a4a8-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="9a4a8-110">同じ型のポインターを減算することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a4a8-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="9a4a8-111">結果は常に `long` 型になります。</span><span class="sxs-lookup"><span data-stu-id="9a4a8-111">The result is always of the type `long`.</span></span> <span data-ttu-id="9a4a8-112">たとえば場合、`p1` と `p2` が `pointer-type*` 型のポインターである場合、式 `p1-p2` の結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9a4a8-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="9a4a8-113">算術演算がポインターのドメインをオーバーフローしても、例外は生成されません。生じる結果は実装によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9a4a8-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a4a8-114">例</span><span class="sxs-lookup"><span data-stu-id="9a4a8-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9a4a8-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9a4a8-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a4a8-116">参照</span><span class="sxs-lookup"><span data-stu-id="9a4a8-116">See Also</span></span>  
 [<span data-ttu-id="9a4a8-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9a4a8-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9a4a8-118">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="9a4a8-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="9a4a8-119">ポインター式</span><span class="sxs-lookup"><span data-stu-id="9a4a8-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="9a4a8-120">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="9a4a8-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="9a4a8-121">ポインターの操作</span><span class="sxs-lookup"><span data-stu-id="9a4a8-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="9a4a8-122">ポインター型</span><span class="sxs-lookup"><span data-stu-id="9a4a8-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="9a4a8-123">型</span><span class="sxs-lookup"><span data-stu-id="9a4a8-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="9a4a8-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="9a4a8-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="9a4a8-125">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="9a4a8-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="9a4a8-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="9a4a8-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
