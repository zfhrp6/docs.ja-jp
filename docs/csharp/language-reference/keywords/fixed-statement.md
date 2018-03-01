---
title: "fixed ステートメント (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="a4df7-102">fixed ステートメント (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a4df7-102">fixed Statement (C# Reference)</span></span>
<span data-ttu-id="a4df7-103">`fixed` ステートメントは、移動可能な変数がガベージ コレクターにより再配置されることを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="a4df7-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="a4df7-104">`fixed` ステートメントは、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストでのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="a4df7-104">The `fixed` statement is only permitted in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="a4df7-105">`Fixed` は、[固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)の作成にも使うことができます。</span><span class="sxs-lookup"><span data-stu-id="a4df7-105">`Fixed` can also be used to create [fixed size buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="a4df7-106">`fixed` ステートメントは、マネージ変数へのポインターを設定し、ステートメントの実行中にその変数を "固定" します。</span><span class="sxs-lookup"><span data-stu-id="a4df7-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="a4df7-107">`fixed` を指定しないと、ガベージ コレクションが変数を予期せず再配置するため、移動可能なマネージ変数へのポインターはほとんど役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="a4df7-107">Without `fixed`, pointers to movable managed variables would be of little use since garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="a4df7-108">C# コンパイラでは、`fixed` ステートメントでマネージ変数へのポインターを割り当てることだけができます。</span><span class="sxs-lookup"><span data-stu-id="a4df7-108">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 <span data-ttu-id="a4df7-109">配列、文字列、固定サイズ バッファー、または変数のアドレスを使って、ポインターを初期化できます。</span><span class="sxs-lookup"><span data-stu-id="a4df7-109">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="a4df7-110">次の例では、変数のアドレス、配列、および文字列の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="a4df7-110">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="a4df7-111">固定サイズ バッファーについて詳しくは、「[固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a4df7-111">For more information about fixed-size buffers, see [Fixed Size Buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 <span data-ttu-id="a4df7-112">すべてが同じ型であれば、複数のポインターをまとめて初期化できます。</span><span class="sxs-lookup"><span data-stu-id="a4df7-112">You can initialize multiple pointers, as long as they are all of the same type.</span></span>  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 <span data-ttu-id="a4df7-113">異なる型のポインターを初期化するには、次の例で示すように、`fixed` ステートメントを入れ子にします。</span><span class="sxs-lookup"><span data-stu-id="a4df7-113">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 <span data-ttu-id="a4df7-114">ステートメント内のコードの実行が済むと、固定された変数は固定を解除されて、ガベージ コレクションの対象になります。</span><span class="sxs-lookup"><span data-stu-id="a4df7-114">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="a4df7-115">そのため、`fixed` ステートメントの外側ではこれらの変数を参照しないでください。</span><span class="sxs-lookup"><span data-stu-id="a4df7-115">Therefore, do not point to those variables outside the `fixed` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4df7-116">fixed ステートメントで初期化されたポインターは変更できません。</span><span class="sxs-lookup"><span data-stu-id="a4df7-116">Pointers initialized in fixed statements cannot be modified.</span></span>  
  
 <span data-ttu-id="a4df7-117">unsafe モードでは、スタック上のメモリを割り当てることができ、スタックはガベージ コレクションの対象にならないので、固定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a4df7-117">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="a4df7-118">詳しくは、「[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a4df7-118">For more information, see [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4df7-119">例</span><span class="sxs-lookup"><span data-stu-id="a4df7-119">Example</span></span>  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a4df7-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="a4df7-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a4df7-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4df7-121">See Also</span></span>  
 [<span data-ttu-id="a4df7-122">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="a4df7-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a4df7-123">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a4df7-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a4df7-124">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="a4df7-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a4df7-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="a4df7-125">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="a4df7-126">固定サイズ バッファー</span><span class="sxs-lookup"><span data-stu-id="a4df7-126">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
