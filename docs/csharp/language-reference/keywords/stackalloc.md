---
title: "stackalloc (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
dev_langs:
- CSharp
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 27
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
ms.openlocfilehash: 53d61cfdcf4d356a28881c57ad923017c2b479ae
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="81d43-102">stackalloc (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="81d43-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="81d43-103">`stackalloc` キーワードはアンセーフ コード コンテキストで使用され、スタックにメモリ ブロックを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="81d43-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a><span data-ttu-id="81d43-104">コメント</span><span class="sxs-lookup"><span data-stu-id="81d43-104">Remarks</span></span>  
 <span data-ttu-id="81d43-105">このキーワードは、ローカル変数初期化子でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="81d43-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="81d43-106">次のコードはコンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="81d43-106">The following code causes compiler errors.</span></span>  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 <span data-ttu-id="81d43-107">ポインター型が使用されるため、`stackalloc` には [unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストが必要です。</span><span class="sxs-lookup"><span data-stu-id="81d43-107">Because pointer types are involved, `stackalloc` requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="81d43-108">詳細については、「[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81d43-108">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="81d43-109">`stackalloc` は、C ランタイム ライブラリの [_alloca](/cpp/c-runtime-library/reference/alloca) に似ています。</span><span class="sxs-lookup"><span data-stu-id="81d43-109">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>  
  
 <span data-ttu-id="81d43-110">次の例では、フィボナッチ数列の最初の 20 個の数値を計算して表示します。</span><span class="sxs-lookup"><span data-stu-id="81d43-110">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="81d43-111">それぞれの数値が、前の 2 つの数値の和になっています。</span><span class="sxs-lookup"><span data-stu-id="81d43-111">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="81d43-112">このコードでは、`int` 型の要素を 20 個保持できるサイズのメモリ ブロックが、ヒープではなくスタックに割り当てられ、</span><span class="sxs-lookup"><span data-stu-id="81d43-112">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="81d43-113">そのブロックのアドレスは `fib` ポインターに格納されます。</span><span class="sxs-lookup"><span data-stu-id="81d43-113">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="81d43-114">このメモリは、ガベージ コレクションの対象にはならないため、[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) を使用して固定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="81d43-114">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span></span> <span data-ttu-id="81d43-115">メモリ ブロックの有効期間は、そのブロックを定義するメソッドの有効期間に限定されます。</span><span class="sxs-lookup"><span data-stu-id="81d43-115">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="81d43-116">メソッドから制御が戻る前に、メモリを解放することはできません。</span><span class="sxs-lookup"><span data-stu-id="81d43-116">You cannot free the memory before the method returns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81d43-117">例</span><span class="sxs-lookup"><span data-stu-id="81d43-117">Example</span></span>  
 <span data-ttu-id="81d43-118">[!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="81d43-118">[!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]</span></span>  
  
## <a name="security"></a><span data-ttu-id="81d43-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="81d43-119">Security</span></span>  
 <span data-ttu-id="81d43-120">アンセーフ コードは、セーフ コードほど安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="81d43-120">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="81d43-121">ただし、`stackalloc` を使用すると、共通言語ランタイム (CLR) のバッファー オーバーラン検出機能が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="81d43-121">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="81d43-122">バッファー オーバーランが検出されると、悪意のあるコードが実行される可能性を最小限に抑えるために、プロセスはできる限り迅速に終了されます。</span><span class="sxs-lookup"><span data-stu-id="81d43-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="81d43-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="81d43-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="81d43-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="81d43-124">See Also</span></span>  
 <span data-ttu-id="81d43-125">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="81d43-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="81d43-126">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="81d43-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="81d43-127">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="81d43-127">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="81d43-128">[演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="81d43-128">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 [<span data-ttu-id="81d43-129">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="81d43-129">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)

