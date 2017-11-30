---
title: "変換する際のデータ型 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5fb0e9dfb0f1fb882116449757ed0f0bf9029b39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="c7d55-102">変換する際のデータ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7d55-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="c7d55-103">変換メソッドは、入力オブジェクトの型を変更します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="c7d55-104">LINQ クエリの変換操作は、さまざまなアプリケーションで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="c7d55-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="c7d55-105">次にいくつかの例を示します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="c7d55-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> メソッドを使用すると、標準クエリ演算子の型のカスタム実装を非表示することができます。</span><span class="sxs-lookup"><span data-stu-id="c7d55-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="c7d55-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> メソッドを使用すると、LINQ クエリのパラメーター化されていないコレクションを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c7d55-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="c7d55-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>、および <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> メソッドを使用すると、クエリが列挙されるまで延期させるのではなく、即時のクエリ実行を強制することができます。</span><span class="sxs-lookup"><span data-stu-id="c7d55-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7d55-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="c7d55-109">Methods</span></span>  
 <span data-ttu-id="c7d55-110">次の表には、データ型の変換を実行する標準クエリ演算子メソッドの一覧が示されています。</span><span class="sxs-lookup"><span data-stu-id="c7d55-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="c7d55-111">名前が "As" で始まるこの表の変換メソッドは、ソース コレクションの静的型を変更しますが、ソース コレクションを列挙しません。</span><span class="sxs-lookup"><span data-stu-id="c7d55-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="c7d55-112">名前が "To" で始まるメソッドは、ソース コレクションを列挙し、各項目を対応するコレクション型に変換します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="c7d55-113">メソッド名</span><span class="sxs-lookup"><span data-stu-id="c7d55-113">Method Name</span></span>|<span data-ttu-id="c7d55-114">説明</span><span class="sxs-lookup"><span data-stu-id="c7d55-114">Description</span></span>|<span data-ttu-id="c7d55-115">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="c7d55-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="c7d55-116">説明</span><span class="sxs-lookup"><span data-stu-id="c7d55-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="c7d55-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="c7d55-117">AsEnumerable</span></span>|<span data-ttu-id="c7d55-118"><xref:System.Collections.Generic.IEnumerable%601> として型指定された入力を返します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="c7d55-119">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c7d55-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c7d55-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="c7d55-120">AsQueryable</span></span>|<span data-ttu-id="c7d55-121">(ジェネリック) <xref:System.Collections.IEnumerable> を (ジェネリック) <xref:System.Linq.IQueryable> に変換します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="c7d55-122">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c7d55-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c7d55-123">Cast</span><span class="sxs-lookup"><span data-stu-id="c7d55-123">Cast</span></span>|<span data-ttu-id="c7d55-124">コレクションの要素を指定した型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="c7d55-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c7d55-125">OfType</span><span class="sxs-lookup"><span data-stu-id="c7d55-125">OfType</span></span>|<span data-ttu-id="c7d55-126">指定した型にキャストできるかどうかに応じて値をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="c7d55-127">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c7d55-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c7d55-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="c7d55-128">ToArray</span></span>|<span data-ttu-id="c7d55-129">コレクションを配列に変換します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-129">Converts a collection to an array.</span></span> <span data-ttu-id="c7d55-130">このメソッドはクエリの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-130">This method forces query execution.</span></span>|<span data-ttu-id="c7d55-131">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c7d55-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c7d55-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="c7d55-132">ToDictionary</span></span>|<span data-ttu-id="c7d55-133">キー セレクター関数に基づいて、<xref:System.Collections.Generic.Dictionary%602> に要素を変換します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="c7d55-134">このメソッドはクエリの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-134">This method forces query execution.</span></span>|<span data-ttu-id="c7d55-135">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c7d55-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c7d55-136">ToList</span><span class="sxs-lookup"><span data-stu-id="c7d55-136">ToList</span></span>|<span data-ttu-id="c7d55-137">コレクションを <xref:System.Collections.Generic.List%601> に変換します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="c7d55-138">このメソッドはクエリの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-138">This method forces query execution.</span></span>|<span data-ttu-id="c7d55-139">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c7d55-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c7d55-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="c7d55-140">ToLookup</span></span>|<span data-ttu-id="c7d55-141">キー セレクター関数に基づいて、<xref:System.Linq.Lookup%602> (一対多の辞書) に要素を変換します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="c7d55-142">このメソッドはクエリの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-142">This method forces query execution.</span></span>|<span data-ttu-id="c7d55-143">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c7d55-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="c7d55-144">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="c7d55-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="c7d55-145">次のコード例では、`From As`サブタイプでのみ利用可能なメンバーにアクセスする前に、サブタイプの型をキャストする句。</span><span class="sxs-lookup"><span data-stu-id="c7d55-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7d55-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7d55-146">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="c7d55-147">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7d55-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="c7d55-148">From 句</span><span class="sxs-lookup"><span data-stu-id="c7d55-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="c7d55-149">方法: LINQ (Visual Basic) で ArrayList を照会します。</span><span class="sxs-lookup"><span data-stu-id="c7d55-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
