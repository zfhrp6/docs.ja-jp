---
title: "orderby 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- orderby
- orderby_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: 17
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
ms.openlocfilehash: ec9507e4c1d9691d90d47cdbb20fdb22fc281d24
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="17d89-102">orderby 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="17d89-102">orderby clause (C# Reference)</span></span>
<span data-ttu-id="17d89-103">クエリ式では、`orderby` 句によって返されるシーケンスまたはサブシーケンス (グループ) が昇順または降順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="17d89-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="17d89-104">2 番目の並べ替え操作を 1 つ以上実行するために、複数のキーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="17d89-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="17d89-105">並べ替えは、要素の型の既定の比較演算子によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="17d89-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="17d89-106">既定の並べ替え順序は昇順です。</span><span class="sxs-lookup"><span data-stu-id="17d89-106">The default sort order is ascending.</span></span> <span data-ttu-id="17d89-107">カスタムの比較演算子を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="17d89-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="17d89-108">ただしこれは、メソッド ベースの構文を使用する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="17d89-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="17d89-109">詳細については、「[Sorting Data](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48)」(データの並べ替え) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17d89-109">For more information, see [Sorting Data](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17d89-110">例</span><span class="sxs-lookup"><span data-stu-id="17d89-110">Example</span></span>  
 <span data-ttu-id="17d89-111">次の例では、最初のクエリが A から始まるアルファベット順で単語を並べ替え、2 番目のクエリが同じ単語を降順で並べ替えます </span><span class="sxs-lookup"><span data-stu-id="17d89-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="17d89-112">(`ascending` キーワードは、既定の並べ替え値で、省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="17d89-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>  
  
 <span data-ttu-id="17d89-113">[!code-cs[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="17d89-113">[!code-cs[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="17d89-114">例</span><span class="sxs-lookup"><span data-stu-id="17d89-114">Example</span></span>  
 <span data-ttu-id="17d89-115">次の例では、学生の姓で最初の並べ替えを実行し、学生の名で 2 番目の並べ替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="17d89-115">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>  
  
 <span data-ttu-id="17d89-116">[!code-cs[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="17d89-116">[!code-cs[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17d89-117">コメント</span><span class="sxs-lookup"><span data-stu-id="17d89-117">Remarks</span></span>  
 <span data-ttu-id="17d89-118">コンパイル時に、`orderby` 句は <xref:System.Linq.Enumerable.OrderBy%2A> メソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="17d89-118">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="17d89-119">`orderby` 句内の複数のキーは、<xref:System.Linq.Enumerable.ThenBy%2A> メソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="17d89-119">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d89-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="17d89-120">See Also</span></span>  
 <span data-ttu-id="17d89-121">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="17d89-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="17d89-122">[クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="17d89-122">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="17d89-123">[LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="17d89-123">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="17d89-124">[group 句](../../../csharp/language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="17d89-124">[group clause](../../../csharp/language-reference/keywords/group-clause.md) </span></span>  
 [<span data-ttu-id="17d89-125">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="17d89-125">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

