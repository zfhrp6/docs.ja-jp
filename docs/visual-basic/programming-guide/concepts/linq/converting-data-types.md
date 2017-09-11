---
title: "データ型 (Visual Basic) に変換する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 948779e1648291b00a68bfd83d57750d48a9a6d8
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="195ad-102">データ型 (Visual Basic) に変換します。</span><span class="sxs-lookup"><span data-stu-id="195ad-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="195ad-103">変換メソッドは、入力オブジェクトの種類を変更します。</span><span class="sxs-lookup"><span data-stu-id="195ad-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="195ad-104">変換操作は、LINQ クエリでは、さまざまなアプリケーションで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="195ad-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="195ad-105">いくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="195ad-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="195ad-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>メソッドは、標準クエリ演算子の型のカスタム実装を非表示にするために使用できます</xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="195ad-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="195ad-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>の LINQ クエリのコレクションの非パラメーター化を有効にするメソッドを使用できます</xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="195ad-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="195ad-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>、 <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>、 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>、および<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>メソッドは、クエリが列挙されるまで遅延させることではなく、クエリの即時実行を強制するために使用できます</xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="195ad-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="195ad-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="195ad-109">Methods</span></span>  
 <span data-ttu-id="195ad-110">次の表は、データ型変換を実行する標準クエリ演算子メソッドを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="195ad-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="195ad-111">このテーブルの"As"で始まる名前の変換メソッドは、ソース コレクションの静的な型の変更が、列挙しません。</span><span class="sxs-lookup"><span data-stu-id="195ad-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="195ad-112">"To ソース コレクションを列挙し、それらの項目を対応するコレクション"で始まる名前のメソッドを入力します。</span><span class="sxs-lookup"><span data-stu-id="195ad-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="195ad-113">メソッド名</span><span class="sxs-lookup"><span data-stu-id="195ad-113">Method Name</span></span>|<span data-ttu-id="195ad-114">説明</span><span class="sxs-lookup"><span data-stu-id="195ad-114">Description</span></span>|<span data-ttu-id="195ad-115">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="195ad-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="195ad-116">説明</span><span class="sxs-lookup"><span data-stu-id="195ad-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="195ad-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="195ad-117">AsEnumerable</span></span>|<span data-ttu-id="195ad-118"><xref:System.Collections.Generic.IEnumerable%601>。</xref:System.Collections.Generic.IEnumerable%601>として型指定された入力を返します</span><span class="sxs-lookup"><span data-stu-id="195ad-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="195ad-119">該当なし。</span><span class="sxs-lookup"><span data-stu-id="195ad-119">Not applicable.</span></span>|<span data-ttu-id="195ad-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="195ad-121">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="195ad-121">AsQueryable</span></span>|<span data-ttu-id="195ad-122">変換する (汎用) <xref:System.Collections.IEnumerable> <xref:System.Linq.IQueryable>。</xref:System.Linq.IQueryable> (汎用)</xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="195ad-122">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="195ad-123">該当なし。</span><span class="sxs-lookup"><span data-stu-id="195ad-123">Not applicable.</span></span>|<span data-ttu-id="195ad-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="195ad-125">Cast</span><span class="sxs-lookup"><span data-stu-id="195ad-125">Cast</span></span>|<span data-ttu-id="195ad-126">指定した型のコレクションの要素をキャストします。</span><span class="sxs-lookup"><span data-stu-id="195ad-126">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<span data-ttu-id="195ad-127"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-127"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="195ad-128"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-128"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="195ad-129">OfType</span><span class="sxs-lookup"><span data-stu-id="195ad-129">OfType</span></span>|<span data-ttu-id="195ad-130">指定した型にキャストするかどうかによって、値をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="195ad-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="195ad-131">該当なし。</span><span class="sxs-lookup"><span data-stu-id="195ad-131">Not applicable.</span></span>|<span data-ttu-id="195ad-132"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-132"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="195ad-133"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-133"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="195ad-134">ToArray</span><span class="sxs-lookup"><span data-stu-id="195ad-134">ToArray</span></span>|<span data-ttu-id="195ad-135">コレクションを配列に変換します。</span><span class="sxs-lookup"><span data-stu-id="195ad-135">Converts a collection to an array.</span></span> <span data-ttu-id="195ad-136">このメソッドは、クエリの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="195ad-136">This method forces query execution.</span></span>|<span data-ttu-id="195ad-137">該当なし。</span><span class="sxs-lookup"><span data-stu-id="195ad-137">Not applicable.</span></span>|<span data-ttu-id="195ad-138"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-138"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="195ad-139">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="195ad-139">ToDictionary</span></span>|<span data-ttu-id="195ad-140">要素を配置、<xref:System.Collections.Generic.Dictionary%602>されたキー セレクター関数に基づいて</xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="195ad-140">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="195ad-141">このメソッドは、クエリの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="195ad-141">This method forces query execution.</span></span>|<span data-ttu-id="195ad-142">該当なし。</span><span class="sxs-lookup"><span data-stu-id="195ad-142">Not applicable.</span></span>|<span data-ttu-id="195ad-143"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-143"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="195ad-144">ToList</span><span class="sxs-lookup"><span data-stu-id="195ad-144">ToList</span></span>|<span data-ttu-id="195ad-145"><xref:System.Collections.Generic.List%601>。</xref:System.Collections.Generic.List%601>コレクションに変換します</span><span class="sxs-lookup"><span data-stu-id="195ad-145">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="195ad-146">このメソッドは、クエリの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="195ad-146">This method forces query execution.</span></span>|<span data-ttu-id="195ad-147">該当なし。</span><span class="sxs-lookup"><span data-stu-id="195ad-147">Not applicable.</span></span>|<span data-ttu-id="195ad-148"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-148"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="195ad-149">ToLookup</span><span class="sxs-lookup"><span data-stu-id="195ad-149">ToLookup</span></span>|<span data-ttu-id="195ad-150">要素を配置、<xref:System.Linq.Lookup%602>されたキー セレクター関数に基づいて、(一対多辞書).</xref:System.Linq.Lookup%602></span><span class="sxs-lookup"><span data-stu-id="195ad-150">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="195ad-151">このメソッドは、クエリの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="195ad-151">This method forces query execution.</span></span>|<span data-ttu-id="195ad-152">該当なし。</span><span class="sxs-lookup"><span data-stu-id="195ad-152">Not applicable.</span></span>|<span data-ttu-id="195ad-153"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="195ad-153"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="195ad-154">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="195ad-154">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="195ad-155">次のコード例では、`From As`のサブタイプでのみ使用可能なメンバーにアクセスする前にサブタイプの型をキャストする句。</span><span class="sxs-lookup"><span data-stu-id="195ad-155">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="195ad-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="195ad-156">See Also</span></span>  
 <span data-ttu-id="195ad-157"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="195ad-157"><xref:System.Linq></span></span>   
<span data-ttu-id="195ad-158"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="195ad-158"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="195ad-159"> [From 句](../../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="195ad-159"> [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="195ad-160"> [方法: クエリ、LINQ で ArrayList を (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span><span class="sxs-lookup"><span data-stu-id="195ad-160"> [How to: Query an ArrayList with LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span></span>
