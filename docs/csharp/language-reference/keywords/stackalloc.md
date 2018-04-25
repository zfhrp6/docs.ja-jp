---
title: stackalloc (C# リファレンス)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4cde254bb6a5601d10619c4a3bd2f00f1f146d3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="01dcf-102">stackalloc (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="01dcf-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="01dcf-103">`stackalloc` キーワードはアンセーフ コード コンテキストで使用され、スタックにメモリ ブロックを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="01dcf-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="01dcf-104">コメント</span><span class="sxs-lookup"><span data-stu-id="01dcf-104">Remarks</span></span>

<span data-ttu-id="01dcf-105">このキーワードは、ローカル変数初期化子でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="01dcf-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="01dcf-106">次のコードはコンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="01dcf-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="01dcf-107">C# 7.3 以降では、`stackalloc` 配列に対して配列初期化子構文を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="01dcf-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="01dcf-108">次のすべての宣言では、値が整数 `1`、`2`、`3` である 3 つの要素を含む配列が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="01dcf-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="01dcf-109">ポインター型が使用されるため、`stackalloc` には [unsafe](unsafe.md) コンテキストが必要です。</span><span class="sxs-lookup"><span data-stu-id="01dcf-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="01dcf-110">詳しくは、「[アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="01dcf-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md)</span></span> 

<span data-ttu-id="01dcf-111">`stackalloc` は、C ランタイム ライブラリの [_alloca](/cpp/c-runtime-library/reference/alloca) に似ています。</span><span class="sxs-lookup"><span data-stu-id="01dcf-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="01dcf-112">使用例</span><span class="sxs-lookup"><span data-stu-id="01dcf-112">Examples</span></span>

<span data-ttu-id="01dcf-113">次の例では、フィボナッチ数列の最初の 20 個の数値を計算して表示します。</span><span class="sxs-lookup"><span data-stu-id="01dcf-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="01dcf-114">それぞれの数値が、前の 2 つの数値の和になっています。</span><span class="sxs-lookup"><span data-stu-id="01dcf-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="01dcf-115">このコードでは、`int` 型の要素を 20 個保持できるサイズのメモリ ブロックが、ヒープではなくスタックに割り当てられ、</span><span class="sxs-lookup"><span data-stu-id="01dcf-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="01dcf-116">そのブロックのアドレスは `fib` ポインターに格納されます。</span><span class="sxs-lookup"><span data-stu-id="01dcf-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="01dcf-117">このメモリは、ガベージ コレクションの対象にはならないため、[fixed](fixed-statement.md) を使用して固定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="01dcf-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="01dcf-118">メモリ ブロックの有効期間は、そのブロックを定義するメソッドの有効期間に限定されます。</span><span class="sxs-lookup"><span data-stu-id="01dcf-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="01dcf-119">メソッドから制御が戻る前に、メモリを解放することはできません。</span><span class="sxs-lookup"><span data-stu-id="01dcf-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="01dcf-120">次の例では、整数の `stackalloc` 配列を、要素ごとに 1 ビットが設定されているビット マスクに初期化しています。</span><span class="sxs-lookup"><span data-stu-id="01dcf-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="01dcf-121">これは、C# 7.3 以降で使用可能な新しい初期化子の構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="01dcf-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="01dcf-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="01dcf-122">Security</span></span>

<span data-ttu-id="01dcf-123">アンセーフ コードは、セーフ コードほど安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="01dcf-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="01dcf-124">ただし、`stackalloc` を使用すると、共通言語ランタイム (CLR) のバッファー オーバーラン検出機能が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="01dcf-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="01dcf-125">バッファー オーバーランが検出されると、悪意のあるコードが実行される可能性を最小限に抑えるために、プロセスはできる限り迅速に終了されます。</span><span class="sxs-lookup"><span data-stu-id="01dcf-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="01dcf-126">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="01dcf-126">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="01dcf-127">参照</span><span class="sxs-lookup"><span data-stu-id="01dcf-127">See Also</span></span>
 [<span data-ttu-id="01dcf-128">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="01dcf-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="01dcf-129">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="01dcf-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="01dcf-130">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="01dcf-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="01dcf-131">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="01dcf-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="01dcf-132">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="01dcf-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
