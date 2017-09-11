---
title: "クエリ式の null 値の処理"
description: "クエリ式の null 値を処理する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f4f189504c57c9c01268b10bc96ad3c9af49ddbd
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="a9c99-104">クエリ式の null 値の処理</span><span class="sxs-lookup"><span data-stu-id="a9c99-104">Handle null values in query expressions</span></span>

<span data-ttu-id="a9c99-105">この例では、ソース コレクション内の可能な null 値を処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a9c99-105">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="a9c99-106"><xref:System.Collections.Generic.IEnumerable%601> のようなオブジェクト コレクションには、値が [null](../language-reference/keywords/null.md) の要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a9c99-106">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="a9c99-107">ソース コレクションが null であるか null の値を持つ要素を含み、クエリで null 値を処理しない場合、クエリを実行すると <xref:System.NullReferenceException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a9c99-107">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9c99-108">例</span><span class="sxs-lookup"><span data-stu-id="a9c99-108">Example</span></span>

 <span data-ttu-id="a9c99-109">次の例に示すように、null 参照の例外を回避する防御的なコーディングをすることができます。</span><span class="sxs-lookup"><span data-stu-id="a9c99-109">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>  
  
 <span data-ttu-id="a9c99-110">[!code-cs[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a9c99-110">[!code-cs[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]</span></span>  
  
 <span data-ttu-id="a9c99-111">前の例では、`where` 句によって、カテゴリ シーケンス内のすべての null 要素が除外されます。</span><span class="sxs-lookup"><span data-stu-id="a9c99-111">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="a9c99-112">この手法は、join 句での null チェックに依存しません。</span><span class="sxs-lookup"><span data-stu-id="a9c99-112">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="a9c99-113">この例の null 条件式が機能する理由は、`Products.CategoryID` が `int?` 型 (`Nullable<int>` の短縮形) であるためです。</span><span class="sxs-lookup"><span data-stu-id="a9c99-113">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9c99-114">例</span><span class="sxs-lookup"><span data-stu-id="a9c99-114">Example</span></span>

 <span data-ttu-id="a9c99-115">join 句で、比較キーの一方だけが null 許容値型である場合、クエリ式でもう一方のキーを null 許容型にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="a9c99-115">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="a9c99-116">次の例では、`EmployeeID` は `int?` 型の値を含む列であるとします。</span><span class="sxs-lookup"><span data-stu-id="a9c99-116">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>  
  
 <span data-ttu-id="a9c99-117">[!code-cs[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="a9c99-117">[!code-cs[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c99-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9c99-118">See also</span></span>  
 <span data-ttu-id="a9c99-119"><xref:System.Nullable%601></span><span class="sxs-lookup"><span data-stu-id="a9c99-119"><xref:System.Nullable%601></span></span>   
 <span data-ttu-id="a9c99-120">[LINQ クエリ式](index.md) </span><span class="sxs-lookup"><span data-stu-id="a9c99-120">[LINQ query expressions](index.md) </span></span>  
 [<span data-ttu-id="a9c99-121">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="a9c99-121">Nullable types</span></span>](../programming-guide/nullable-types/index.md)

