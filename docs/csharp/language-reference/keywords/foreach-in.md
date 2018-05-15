---
title: foreach、in (C# リファレンス)
ms.date: 10/11/2017
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: f00ae873e615f653d3e760f82b157a57fdaef6ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="e34dc-102">foreach、in (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e34dc-102">foreach, in (C# Reference)</span></span>
<span data-ttu-id="e34dc-103">`foreach` ステートメントは、<xref:System.Collections.IEnumerable?displayProperty=nameWithType> インターフェイスまたは <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> インターフェイスを実装する配列またはオブジェクト コレクションのそれぞれの要素に対して埋め込みステートメントを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="e34dc-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="e34dc-104">`foreach` ステートメントは、コレクションを繰り返し処理して目的の情報を取得するために使用しますが、予期しない副作用を防ぐため、ソース コレクションに対する項目の追加または削除には使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="e34dc-104">The `foreach` statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="e34dc-105">ソース コレクションに対して項目を追加または削除する必要がある場合は、[for](for.md) ループを使います。</span><span class="sxs-lookup"><span data-stu-id="e34dc-105">If you need to add or remove items from the source collection, use a [for](for.md) loop.</span></span>
  
 <span data-ttu-id="e34dc-106">埋め込みステートメントは、配列またはコレクション内の各要素に対して繰り返し実行されます。</span><span class="sxs-lookup"><span data-stu-id="e34dc-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="e34dc-107">コレクション内の全要素に対する繰り返しが完了すると、制御は、`foreach` ブロックに続く次のステートメントに移動します。</span><span class="sxs-lookup"><span data-stu-id="e34dc-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>
  
 <span data-ttu-id="e34dc-108">`foreach` ブロック内の任意の位置で、[break](break.md) キーワードを使ってループから抜けることができます。または、[continue](continue.md) キーワードを使って、ループ内の次の反復処理にスキップできます。</span><span class="sxs-lookup"><span data-stu-id="e34dc-108">At any point within the `foreach` block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span>

 <span data-ttu-id="e34dc-109">[goto](goto.md) ステートメント、[return](return.md) ステートメント、または [throw](throw.md) ステートメントを使用して `foreach` ループを抜けることもできます。</span><span class="sxs-lookup"><span data-stu-id="e34dc-109">A `foreach` loop can also be exited by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

 <span data-ttu-id="e34dc-110">`foreach` キーワードとコード例の詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34dc-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  

 [<span data-ttu-id="e34dc-111">配列での foreach の使用</span><span class="sxs-lookup"><span data-stu-id="e34dc-111">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [<span data-ttu-id="e34dc-112">方法: foreach を使用してコレクション クラスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="e34dc-112">How to: Access a Collection Class with foreach</span></span>](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a><span data-ttu-id="e34dc-113">例</span><span class="sxs-lookup"><span data-stu-id="e34dc-113">Example</span></span>
 <span data-ttu-id="e34dc-114">次のコードは、3 つの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="e34dc-114">The following code shows three examples.</span></span>

> [!TIP]
> <span data-ttu-id="e34dc-115">例を変更して構文の実験をしたり、自身のユース ケースにより近い異なる使用方法を試したりできます。</span><span class="sxs-lookup"><span data-stu-id="e34dc-115">You can modify the examples to experiment with the syntax and try different usages that are more similar to your use case.</span></span> <span data-ttu-id="e34dc-116">「実行」を押してコードを実行し、編集したら再び「実行」を押します。</span><span class="sxs-lookup"><span data-stu-id="e34dc-116">Press "Run" to run the code, then edit and press "Run" again.</span></span>

-   <span data-ttu-id="e34dc-117">整数の配列の内容を表示する一般的な `foreach` ループ</span><span class="sxs-lookup"><span data-stu-id="e34dc-117">a typical `foreach` loop that displays the contents of an array of integers</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   <span data-ttu-id="e34dc-118">同じ処理を行う [for](../../../csharp/language-reference/keywords/for.md) ループ</span><span class="sxs-lookup"><span data-stu-id="e34dc-118">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   <span data-ttu-id="e34dc-119">配列内の要素数のカウントを保持する `foreach` ループ</span><span class="sxs-lookup"><span data-stu-id="e34dc-119">a `foreach` loop that maintains a count of the number of elements in the array</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a><span data-ttu-id="e34dc-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="e34dc-120">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e34dc-121">参照</span><span class="sxs-lookup"><span data-stu-id="e34dc-121">See Also</span></span>  

[<span data-ttu-id="e34dc-122">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="e34dc-122">C# Reference</span></span>](../index.md)

[<span data-ttu-id="e34dc-123">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e34dc-123">C# Programming Guide</span></span>](../../programming-guide/index.md)

[<span data-ttu-id="e34dc-124">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="e34dc-124">C# Keywords</span></span>](index.md)

[<span data-ttu-id="e34dc-125">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="e34dc-125">Iteration Statements</span></span>](iteration-statements.md)

[<span data-ttu-id="e34dc-126">for</span><span class="sxs-lookup"><span data-stu-id="e34dc-126">for</span></span>](for.md)
