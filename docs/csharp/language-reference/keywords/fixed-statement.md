---
title: fixed ステートメント (C# リファレンス)
ms.date: 04/20/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e1664f508cb861ffa73b800eeb0da3a1f1cdc432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="252fc-102">fixed ステートメント (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="252fc-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="252fc-103">`fixed` ステートメントは、移動可能な変数がガベージ コレクターにより再配置されることを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="252fc-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="252fc-104">`fixed` ステートメントは、[unsafe](unsafe.md) コンテキストでのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="252fc-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="252fc-105">`Fixed` は、[固定サイズ バッファー](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)の作成にも使うことができます。</span><span class="sxs-lookup"><span data-stu-id="252fc-105">`Fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="252fc-106">`fixed` ステートメントは、マネージ変数へのポインターを設定し、ステートメントの実行中にその変数を "固定" します。</span><span class="sxs-lookup"><span data-stu-id="252fc-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="252fc-107">移動可能なマネージド変数へのポインターは、`fixed` コンテキストでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="252fc-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="252fc-108">`fixed` コンテキストがない場合、ガベージ コレクションによって変数が予期せず再配置される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="252fc-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="252fc-109">C# コンパイラでは、`fixed` ステートメントでマネージ変数へのポインターを割り当てることだけができます。</span><span class="sxs-lookup"><span data-stu-id="252fc-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="252fc-110">配列、文字列、固定サイズ バッファー、または変数のアドレスを使って、ポインターを初期化できます。</span><span class="sxs-lookup"><span data-stu-id="252fc-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="252fc-111">次の例では、変数のアドレス、配列、および文字列の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="252fc-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="252fc-112">固定サイズ バッファーについて詳しくは、「[固定サイズ バッファー](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="252fc-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="252fc-113">複数のポインターは、すべて同じ型の場合、1 つのステートメントで初期化できます。</span><span class="sxs-lookup"><span data-stu-id="252fc-113">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="252fc-114">異なる型のポインターを初期化するには、次の例で示すように、`fixed` ステートメントを入れ子にします。</span><span class="sxs-lookup"><span data-stu-id="252fc-114">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="252fc-115">ステートメント内のコードの実行が済むと、固定された変数は固定を解除されて、ガベージ コレクションの対象になります。</span><span class="sxs-lookup"><span data-stu-id="252fc-115">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="252fc-116">そのため、`fixed` ステートメントの外側ではこれらの変数を参照しないでください。</span><span class="sxs-lookup"><span data-stu-id="252fc-116">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="252fc-117">`fixed` ステートメントで宣言された変数は、そのステートメントにスコープされるので、この処理が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="252fc-117">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="252fc-118">`fixed` ステートメントで初期化されたポインターは読み取り専用変数です。</span><span class="sxs-lookup"><span data-stu-id="252fc-118">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="252fc-119">ポインター値を変更するには、2 つ目のポインター変数を宣言し、それを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="252fc-119">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="252fc-120">`fixed` ステートメントで宣言された変数は変更できません。</span><span class="sxs-lookup"><span data-stu-id="252fc-120">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="252fc-121">unsafe モードでは、スタック上のメモリを割り当てることができ、スタックはガベージ コレクションの対象にならないので、固定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="252fc-121">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="252fc-122">詳しくは、「[stackalloc](stackalloc.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="252fc-122">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="252fc-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="252fc-123">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="252fc-124">参照</span><span class="sxs-lookup"><span data-stu-id="252fc-124">See Also</span></span>

 [<span data-ttu-id="252fc-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="252fc-125">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="252fc-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="252fc-126">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="252fc-127">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="252fc-127">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="252fc-128">unsafe</span><span class="sxs-lookup"><span data-stu-id="252fc-128">unsafe</span></span>](unsafe.md)  
 [<span data-ttu-id="252fc-129">固定サイズ バッファー</span><span class="sxs-lookup"><span data-stu-id="252fc-129">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
