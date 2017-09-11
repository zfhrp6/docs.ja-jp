---
title: "foreach、in (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: 29
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
ms.openlocfilehash: aed1d4f086f0b1334df750fd912d20d66326a043
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="1911d-102">foreach、in (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1911d-102">foreach, in (C# Reference)</span></span>
<span data-ttu-id="1911d-103">`foreach` ステートメントは、<xref:System.Collections.IEnumerable?displayProperty=fullName> インターフェイスまたは <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> インターフェイスを実装する配列またはオブジェクト コレクションのそれぞれの要素に対して埋め込みステートメントを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1911d-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=fullName> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface.</span></span> <span data-ttu-id="1911d-104">`foreach` ステートメントは、コレクションを繰り返し処理して目的の情報を取得するために使用しますが、予期しない副作用を防ぐため、ソース コレクションに対する項目の追加または削除には使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1911d-104">The `foreach` statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="1911d-105">ソース コレクションに対して項目を追加または削除する必要がある場合は、[for](../../../csharp/language-reference/keywords/for.md) ループを使います。</span><span class="sxs-lookup"><span data-stu-id="1911d-105">If you need to add or remove items from the source collection, use a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span>  
  
 <span data-ttu-id="1911d-106">埋め込みステートメントは、配列またはコレクション内の各要素に対して繰り返し実行されます。</span><span class="sxs-lookup"><span data-stu-id="1911d-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="1911d-107">コレクション内の全要素に対する繰り返しが完了すると、制御は、`foreach` ブロックに続く次のステートメントに移動します。</span><span class="sxs-lookup"><span data-stu-id="1911d-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>  
  
 <span data-ttu-id="1911d-108">`foreach` ブロック内の任意の位置で、[break](../../../csharp/language-reference/keywords/break.md) キーワードを使ってループから抜けることができます。または、[continue](../../../csharp/language-reference/keywords/continue.md) キーワードを使って、ループ内の次の反復処理にスキップできます。</span><span class="sxs-lookup"><span data-stu-id="1911d-108">At any point within the `foreach` block, you can break out of the loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or step to the next iteration in the loop by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span>  
  
 <span data-ttu-id="1911d-109">[goto](../../../csharp/language-reference/keywords/goto.md) ステートメント、[return](../../../csharp/language-reference/keywords/return.md) ステートメント、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントを使用して `foreach` ループを抜けることもできます。</span><span class="sxs-lookup"><span data-stu-id="1911d-109">A `foreach` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
 <span data-ttu-id="1911d-110">`foreach` キーワードとコード例の詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1911d-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  
  
 [<span data-ttu-id="1911d-111">配列での foreach の使用</span><span class="sxs-lookup"><span data-stu-id="1911d-111">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [<span data-ttu-id="1911d-112">方法: foreach を使用してコレクション クラスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="1911d-112">How to: Access a Collection Class with foreach</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## <a name="example"></a><span data-ttu-id="1911d-113">例</span><span class="sxs-lookup"><span data-stu-id="1911d-113">Example</span></span>  
 <span data-ttu-id="1911d-114">次のコードは、3 つの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="1911d-114">The following code shows three examples:</span></span>  
  
-   <span data-ttu-id="1911d-115">整数の配列の内容を表示する一般的な `foreach` ループ</span><span class="sxs-lookup"><span data-stu-id="1911d-115">a typical `foreach` loop that displays the contents of an array of integers</span></span>  
  
-   <span data-ttu-id="1911d-116">同じ処理を行う [for](../../../csharp/language-reference/keywords/for.md) ループ</span><span class="sxs-lookup"><span data-stu-id="1911d-116">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>  
  
-   <span data-ttu-id="1911d-117">配列内の要素数のカウントを保持する `foreach` ループ</span><span class="sxs-lookup"><span data-stu-id="1911d-117">a `foreach` loop that maintains a count of the number of elements in the array</span></span>  
  
 <span data-ttu-id="1911d-118">[!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1911d-118">[!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1911d-119">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1911d-119">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1911d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1911d-120">See Also</span></span>  
 <span data-ttu-id="1911d-121">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1911d-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1911d-122">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1911d-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1911d-123">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1911d-123">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1911d-124">[繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md) </span><span class="sxs-lookup"><span data-stu-id="1911d-124">[Iteration Statements](../../../csharp/language-reference/keywords/iteration-statements.md) </span></span>  
 [<span data-ttu-id="1911d-125">for</span><span class="sxs-lookup"><span data-stu-id="1911d-125">for</span></span>](../../../csharp/language-reference/keywords/for.md)

