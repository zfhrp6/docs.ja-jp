---
title: "stackalloc (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b9c5328bfa1b0fc9a7751763c7d728096886905
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="e1211-102">stackalloc (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e1211-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="e1211-103">`stackalloc` キーワードはアンセーフ コード コンテキストで使用され、スタックにメモリ ブロックを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e1211-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>  
  
```csharp  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a><span data-ttu-id="e1211-104">コメント</span><span class="sxs-lookup"><span data-stu-id="e1211-104">Remarks</span></span>  
 <span data-ttu-id="e1211-105">このキーワードは、ローカル変数初期化子でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="e1211-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="e1211-106">次のコードはコンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="e1211-106">The following code causes compiler errors.</span></span>  
  
```csharp  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 <span data-ttu-id="e1211-107">ポインター型が使用されるため、`stackalloc` には [unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストが必要です。</span><span class="sxs-lookup"><span data-stu-id="e1211-107">Because pointer types are involved, `stackalloc` requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="e1211-108">詳細については、「[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1211-108">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="e1211-109">`stackalloc` は、C ランタイム ライブラリの [_alloca](/cpp/c-runtime-library/reference/alloca) に似ています。</span><span class="sxs-lookup"><span data-stu-id="e1211-109">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>  
  
 <span data-ttu-id="e1211-110">次の例では、フィボナッチ数列の最初の 20 個の数値を計算して表示します。</span><span class="sxs-lookup"><span data-stu-id="e1211-110">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="e1211-111">それぞれの数値が、前の 2 つの数値の和になっています。</span><span class="sxs-lookup"><span data-stu-id="e1211-111">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="e1211-112">このコードでは、`int` 型の要素を 20 個保持できるサイズのメモリ ブロックが、ヒープではなくスタックに割り当てられ、</span><span class="sxs-lookup"><span data-stu-id="e1211-112">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="e1211-113">そのブロックのアドレスは `fib` ポインターに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e1211-113">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="e1211-114">このメモリは、ガベージ コレクションの対象にはならないため、[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) を使用して固定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e1211-114">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span></span> <span data-ttu-id="e1211-115">メモリ ブロックの有効期間は、そのブロックを定義するメソッドの有効期間に限定されます。</span><span class="sxs-lookup"><span data-stu-id="e1211-115">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="e1211-116">メソッドから制御が戻る前に、メモリを解放することはできません。</span><span class="sxs-lookup"><span data-stu-id="e1211-116">You cannot free the memory before the method returns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1211-117">例</span><span class="sxs-lookup"><span data-stu-id="e1211-117">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a><span data-ttu-id="e1211-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e1211-118">Security</span></span>  
 <span data-ttu-id="e1211-119">アンセーフ コードは、セーフ コードほど安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="e1211-119">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="e1211-120">ただし、`stackalloc` を使用すると、共通言語ランタイム (CLR) のバッファー オーバーラン検出機能が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="e1211-120">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="e1211-121">バッファー オーバーランが検出されると、悪意のあるコードが実行される可能性を最小限に抑えるために、プロセスはできる限り迅速に終了されます。</span><span class="sxs-lookup"><span data-stu-id="e1211-121">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e1211-122">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="e1211-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1211-123">参照</span><span class="sxs-lookup"><span data-stu-id="e1211-123">See Also</span></span>  
 [<span data-ttu-id="e1211-124">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="e1211-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e1211-125">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e1211-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e1211-126">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="e1211-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e1211-127">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="e1211-127">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="e1211-128">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="e1211-128">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
