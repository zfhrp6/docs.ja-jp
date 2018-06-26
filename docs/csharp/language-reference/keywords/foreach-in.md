---
title: foreach、in (C# リファレンス)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 7613590686f7f7ec6439da4a2bb672e524ab01e8
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34565707"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="5faa0-102">foreach、in (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5faa0-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="5faa0-103">`foreach` ステートメントは、<xref:System.Collections.IEnumerable?displayProperty=nameWithType> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> インターフェイスを実装している型のインスタンス内の要素ごとに、ステートメントまたはステートメントのブロックを実行します。</span><span class="sxs-lookup"><span data-stu-id="5faa0-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="5faa0-104">`foreach` ステートメントはこのような型にのみ限定されるものではありません。次の条件を満たす任意の型のインスタンスに適用できます。</span><span class="sxs-lookup"><span data-stu-id="5faa0-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="5faa0-105">戻り値の型がクラス、構造体、インターフェイス型のいずれかである、パラメーターなしのパブリック メソッド `GetEnumerator` を持っている。</span><span class="sxs-lookup"><span data-stu-id="5faa0-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="5faa0-106">`GetEnumerator` メソッドの戻り値の型が、パブリック プロパティ `Current` と、戻り値の型が <xref:System.Boolean> であるパラメーターなしのパブリック メソッド `MoveNext` を持っている。</span><span class="sxs-lookup"><span data-stu-id="5faa0-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="5faa0-107">`foreach` ステートメント ブロック内の任意の位置で、[break](break.md) ステートメントを使ってループから抜けることができます。または、[continue](continue.md) ステートメントを使って、ループ内の次の繰り返しにスキップできます。</span><span class="sxs-lookup"><span data-stu-id="5faa0-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="5faa0-108">また、[goto](goto.md)、[return](return.md)、[throw](throw.md) ステートメントのいずれかを使って `foreach` ループを終了することもできます。</span><span class="sxs-lookup"><span data-stu-id="5faa0-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="5faa0-109">使用例</span><span class="sxs-lookup"><span data-stu-id="5faa0-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="5faa0-110">次の例では、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装する <xref:System.Collections.Generic.List%601> 型のインスタンスを使用して、`foreach` ステートメントの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5faa0-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="5faa0-111">次の例では、何のインターフェイスも実装していない <xref:System.Span%601?displayProperty=nameWithType> 型のインスタンスを使用して、`foreach` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5faa0-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="5faa0-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="5faa0-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5faa0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="5faa0-113">See also</span></span>

[<span data-ttu-id="5faa0-114">foreach ステートメント (C# 言語仕様)</span><span class="sxs-lookup"><span data-stu-id="5faa0-114">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="5faa0-115">配列での foreach の使用</span><span class="sxs-lookup"><span data-stu-id="5faa0-115">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="5faa0-116">for</span><span class="sxs-lookup"><span data-stu-id="5faa0-116">for</span></span>](for.md)  
[<span data-ttu-id="5faa0-117">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="5faa0-117">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="5faa0-118">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="5faa0-118">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="5faa0-119">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="5faa0-119">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="5faa0-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5faa0-120">C# Programming Guide</span></span>](../../programming-guide/index.md)  