---
title: "複合キーを使用した結合"
description: "複合キーを使用して結合する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e3e860729ca9267d29ba105ac03ebe22a70b1762
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="acdfd-104">複合キーを使用した結合</span><span class="sxs-lookup"><span data-stu-id="acdfd-104">Join by using composite keys</span></span>

<span data-ttu-id="acdfd-105">この例では、複数のキーを使用して一致項目を定義する結合操作の実行方法を示します。</span><span class="sxs-lookup"><span data-stu-id="acdfd-105">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="acdfd-106">この操作は複合キーを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="acdfd-106">This is accomplished by using a composite key.</span></span> <span data-ttu-id="acdfd-107">比較対象とする値を使用し、匿名型または名前付きの型として複合キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="acdfd-107">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="acdfd-108">メソッドの境界を越えてクエリ変数が渡される場合は、キーの <xref:System.Object.Equals%2A> と <xref:System.Object.GetHashCode%2A> をオーバーライドする名前付きの型を使用してください。</span><span class="sxs-lookup"><span data-stu-id="acdfd-108">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="acdfd-109">各キーのプロパティ名とその出現順序は一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="acdfd-109">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acdfd-110">例</span><span class="sxs-lookup"><span data-stu-id="acdfd-110">Example</span></span>  
 <span data-ttu-id="acdfd-111">次の例では、複合キーを使用して 3 つのテーブルのデータを結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="acdfd-111">The following example demonstrates how to use a composite key to join data from three tables:</span></span>  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 <span data-ttu-id="acdfd-112">複合キーの型の推定は、キーに含まれるプロパティの名前とその出現順序によって異なります。</span><span class="sxs-lookup"><span data-stu-id="acdfd-112">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="acdfd-113">ソース シーケンス内のプロパティの名前が異なる場合は、キー内で新しい名前を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="acdfd-113">If the properties in the source sequences do not have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="acdfd-114">たとえば、`Orders` テーブルと `OrderDetails` テーブルの列にそれぞれ異なる名前が使用されている場合、匿名型で同じ名前を割り当てることにより、復号キーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="acdfd-114">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 <span data-ttu-id="acdfd-115">複合キーは、`group` 句でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="acdfd-115">Composite keys can be also used in a `group` clause.</span></span>  

## <a name="see-also"></a><span data-ttu-id="acdfd-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="acdfd-116">See also</span></span>  
 <span data-ttu-id="acdfd-117">[LINQ クエリ式](index.md) </span><span class="sxs-lookup"><span data-stu-id="acdfd-117">[LINQ query expressions](index.md) </span></span>  
 <span data-ttu-id="acdfd-118">[Join 句](../language-reference/keywords/join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="acdfd-118">[join clause](../language-reference/keywords/join-clause.md) </span></span>  
 [<span data-ttu-id="acdfd-119">group 句</span><span class="sxs-lookup"><span data-stu-id="acdfd-119">group clause</span></span>](../language-reference/keywords/group-clause.md)

