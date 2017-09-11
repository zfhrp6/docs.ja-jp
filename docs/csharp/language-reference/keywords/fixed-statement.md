---
title: "fixed ステートメント (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
dev_langs:
- CSharp
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
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
ms.openlocfilehash: 4e1f810f6e6cfaef3a65c7391f074b414ef18b5a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="51cd5-102">fixed ステートメント (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="51cd5-102">fixed Statement (C# Reference)</span></span>
<span data-ttu-id="51cd5-103">`fixed` ステートメントは、移動可能な変数がガベージ コレクターにより再配置されることを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="51cd5-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="51cd5-104">`fixed` ステートメントは、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストでのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="51cd5-104">The `fixed` statement is only permitted in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="51cd5-105">`Fixed` は、[固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)の作成にも使うことができます。</span><span class="sxs-lookup"><span data-stu-id="51cd5-105">`Fixed` can also be used to create [fixed size buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="51cd5-106">`fixed` ステートメントは、マネージ変数へのポインターを設定し、ステートメントの実行中にその変数を "固定" します。</span><span class="sxs-lookup"><span data-stu-id="51cd5-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="51cd5-107">`fixed` を指定しないと、ガベージ コレクションが変数を予期せず再配置するため、移動可能なマネージ変数へのポインターはほとんど役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="51cd5-107">Without `fixed`, pointers to movable managed variables would be of little use since garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="51cd5-108">C# コンパイラでは、`fixed` ステートメントでマネージ変数へのポインターを割り当てることだけができます。</span><span class="sxs-lookup"><span data-stu-id="51cd5-108">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>  
  
 <span data-ttu-id="51cd5-109">[!code-cs[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="51cd5-109">[!code-cs[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]</span></span>  
  
 <span data-ttu-id="51cd5-110">配列、文字列、固定サイズ バッファー、または変数のアドレスを使って、ポインターを初期化できます。</span><span class="sxs-lookup"><span data-stu-id="51cd5-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="51cd5-111">次の例では、変数のアドレス、配列、および文字列の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="51cd5-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="51cd5-112">固定サイズ バッファーについて詳しくは、「[固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51cd5-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="51cd5-113">[!code-cs[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="51cd5-113">[!code-cs[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]</span></span>  
  
 <span data-ttu-id="51cd5-114">すべてが同じ型であれば、複数のポインターをまとめて初期化できます。</span><span class="sxs-lookup"><span data-stu-id="51cd5-114">You can initialize multiple pointers, as long as they are all of the same type.</span></span>  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 <span data-ttu-id="51cd5-115">異なる型のポインターを初期化するには、次の例で示すように、`fixed` ステートメントを入れ子にします。</span><span class="sxs-lookup"><span data-stu-id="51cd5-115">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>  
  
 <span data-ttu-id="51cd5-116">[!code-cs[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="51cd5-116">[!code-cs[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]</span></span>  
  
 <span data-ttu-id="51cd5-117">ステートメント内のコードの実行が済むと、固定された変数は固定を解除されて、ガベージ コレクションの対象になります。</span><span class="sxs-lookup"><span data-stu-id="51cd5-117">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="51cd5-118">そのため、`fixed` ステートメントの外側ではこれらの変数を参照しないでください。</span><span class="sxs-lookup"><span data-stu-id="51cd5-118">Therefore, do not point to those variables outside the `fixed` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51cd5-119">fixed ステートメントで初期化されたポインターは変更できません。</span><span class="sxs-lookup"><span data-stu-id="51cd5-119">Pointers initialized in fixed statements cannot be modified.</span></span>  
  
 <span data-ttu-id="51cd5-120">unsafe モードでは、スタック上のメモリを割り当てることができ、スタックはガベージ コレクションの対象にならないので、固定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="51cd5-120">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="51cd5-121">詳しくは、「[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51cd5-121">For more information, see [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51cd5-122">例</span><span class="sxs-lookup"><span data-stu-id="51cd5-122">Example</span></span>  
 <span data-ttu-id="51cd5-123">[!code-cs[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="51cd5-123">[!code-cs[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="51cd5-124">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="51cd5-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="51cd5-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="51cd5-125">See Also</span></span>  
 <span data-ttu-id="51cd5-126">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="51cd5-126">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="51cd5-127">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="51cd5-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="51cd5-128">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="51cd5-128">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="51cd5-129">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="51cd5-129">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 [<span data-ttu-id="51cd5-130">固定サイズ バッファー</span><span class="sxs-lookup"><span data-stu-id="51cd5-130">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

