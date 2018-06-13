---
title: stackalloc (C# リファレンス)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 905873cf7f576ff35a9bc1c182ce7ebe17920288
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269169"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="fb490-102">stackalloc (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="fb490-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="fb490-103">`stackalloc` キーワードはアンセーフ コード コンテキストで使用され、スタックにメモリ ブロックを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="fb490-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="fb490-104">コメント</span><span class="sxs-lookup"><span data-stu-id="fb490-104">Remarks</span></span>

<span data-ttu-id="fb490-105">このキーワードは、ローカル変数初期化子でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="fb490-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="fb490-106">次のコードはコンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="fb490-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="fb490-107">C# 7.3 以降では、`stackalloc` 配列に対して配列初期化子構文を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="fb490-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="fb490-108">次のすべての宣言では、値が整数 `1`、`2`、`3` である 3 つの要素を含む配列が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="fb490-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="fb490-109">ポインター型が使用されるため、`stackalloc` には [unsafe](unsafe.md) コンテキストが必要です。</span><span class="sxs-lookup"><span data-stu-id="fb490-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="fb490-110">詳しくは、「[アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fb490-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md)</span></span> 

<span data-ttu-id="fb490-111">`stackalloc` は、C ランタイム ライブラリの [_alloca](/cpp/c-runtime-library/reference/alloca) に似ています。</span><span class="sxs-lookup"><span data-stu-id="fb490-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="fb490-112">使用例</span><span class="sxs-lookup"><span data-stu-id="fb490-112">Examples</span></span>

<span data-ttu-id="fb490-113">次の例では、フィボナッチ数列の最初の 20 個の数値を計算して表示します。</span><span class="sxs-lookup"><span data-stu-id="fb490-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="fb490-114">それぞれの数値が、前の 2 つの数値の和になっています。</span><span class="sxs-lookup"><span data-stu-id="fb490-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="fb490-115">このコードでは、`int` 型の要素を 20 個保持できるサイズのメモリ ブロックが、ヒープではなくスタックに割り当てられ、</span><span class="sxs-lookup"><span data-stu-id="fb490-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="fb490-116">そのブロックのアドレスは `fib` ポインターに格納されます。</span><span class="sxs-lookup"><span data-stu-id="fb490-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="fb490-117">このメモリは、ガベージ コレクションの対象にはならないため、[fixed](fixed-statement.md) を使用して固定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fb490-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="fb490-118">メモリ ブロックの有効期間は、そのブロックを定義するメソッドの有効期間に限定されます。</span><span class="sxs-lookup"><span data-stu-id="fb490-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="fb490-119">メソッドから制御が戻る前に、メモリを解放することはできません。</span><span class="sxs-lookup"><span data-stu-id="fb490-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="fb490-120">次の例では、整数の `stackalloc` 配列を、要素ごとに 1 ビットが設定されているビット マスクに初期化しています。</span><span class="sxs-lookup"><span data-stu-id="fb490-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="fb490-121">これは、C# 7.3 以降で使用可能な新しい初期化子の構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="fb490-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="fb490-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fb490-122">Security</span></span>

<span data-ttu-id="fb490-123">アンセーフ コードは、セーフ コードほど安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="fb490-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="fb490-124">ただし、`stackalloc` を使用すると、共通言語ランタイム (CLR) のバッファー オーバーラン検出機能が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="fb490-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="fb490-125">バッファー オーバーランが検出されると、悪意のあるコードが実行される可能性を最小限に抑えるために、プロセスはできる限り迅速に終了されます。</span><span class="sxs-lookup"><span data-stu-id="fb490-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fb490-126">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="fb490-126">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fb490-127">参照</span><span class="sxs-lookup"><span data-stu-id="fb490-127">See Also</span></span>
 [<span data-ttu-id="fb490-128">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="fb490-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fb490-129">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fb490-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fb490-130">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="fb490-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fb490-131">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="fb490-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="fb490-132">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="fb490-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
