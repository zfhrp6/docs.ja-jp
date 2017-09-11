---
title: "射影操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
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
ms.openlocfilehash: aac5cf69e6c3f4041a4302e8d606ca8dfddbc8a2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="3a76b-102">射影操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a76b-102">Projection Operations (Visual Basic)</span></span>
<span data-ttu-id="3a76b-103">射影は、多くの場合のみで構成される、後で使用されるこれらのプロパティを新しいフォームにオブジェクトを変換する処理を指します。</span><span class="sxs-lookup"><span data-stu-id="3a76b-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="3a76b-104">射影を使用することにより、個々のオブジェクトから構築された新しい型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="3a76b-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="3a76b-105">プロパティを投影し、それに数学関数を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3a76b-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="3a76b-106">これを変更することがなく、元のオブジェクトを射影することもできます。</span><span class="sxs-lookup"><span data-stu-id="3a76b-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="3a76b-107">射影を実行する標準クエリ演算子メソッドは、次のように記載されています。</span><span class="sxs-lookup"><span data-stu-id="3a76b-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a76b-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="3a76b-108">Methods</span></span>  
  
|<span data-ttu-id="3a76b-109">メソッド名</span><span class="sxs-lookup"><span data-stu-id="3a76b-109">Method Name</span></span>|<span data-ttu-id="3a76b-110">説明</span><span class="sxs-lookup"><span data-stu-id="3a76b-110">Description</span></span>|<span data-ttu-id="3a76b-111">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="3a76b-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="3a76b-112">説明</span><span class="sxs-lookup"><span data-stu-id="3a76b-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="3a76b-113">選択</span><span class="sxs-lookup"><span data-stu-id="3a76b-113">Select</span></span>|<span data-ttu-id="3a76b-114">変換関数に基づくプロジェクト値です。</span><span class="sxs-lookup"><span data-stu-id="3a76b-114">Projects values that are based on a transform function.</span></span>|`Select`|<span data-ttu-id="3a76b-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3a76b-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="3a76b-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3a76b-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="3a76b-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="3a76b-117">SelectMany</span></span>|<span data-ttu-id="3a76b-118">変換関数に基づいており、その&1; つのシーケンスへの射影する値のシーケンスを射影します。</span><span class="sxs-lookup"><span data-stu-id="3a76b-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="3a76b-119">複数回使用`From`句</span><span class="sxs-lookup"><span data-stu-id="3a76b-119">Use multiple `From` clauses</span></span>|<span data-ttu-id="3a76b-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3a76b-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="3a76b-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3a76b-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="3a76b-122">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="3a76b-122">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="3a76b-123">[選択]</span><span class="sxs-lookup"><span data-stu-id="3a76b-123">Select</span></span>  
 <span data-ttu-id="3a76b-124">次の例では、`Select`文字列のリスト内の各文字列から先頭の文字を射影する句。</span><span class="sxs-lookup"><span data-stu-id="3a76b-124">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a><span data-ttu-id="3a76b-125">SelectMany</span><span class="sxs-lookup"><span data-stu-id="3a76b-125">SelectMany</span></span>  
 <span data-ttu-id="3a76b-126">次のコードの例では、複数`From`文字列のリスト内の各文字列から各単語を射影する句。</span><span class="sxs-lookup"><span data-stu-id="3a76b-126">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="3a76b-127">SelectMany と選択します。</span><span class="sxs-lookup"><span data-stu-id="3a76b-127">Select versus SelectMany</span></span>  
 <span data-ttu-id="3a76b-128">両方の作業`Select()`と`SelectMany()`ソースの値から結果値 (または値) を作成することです。</span><span class="sxs-lookup"><span data-stu-id="3a76b-128">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="3a76b-129">`Select()`ソース値ごとに&1; つの結果値を生成します。</span><span class="sxs-lookup"><span data-stu-id="3a76b-129">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="3a76b-130">全体の結果は、ソース コレクションと同じ数の要素のコレクションではこのためです。</span><span class="sxs-lookup"><span data-stu-id="3a76b-130">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="3a76b-131">これに対し、`SelectMany()`を各ソース値から、連結されたサブ コレクションを含む単一の全体的な結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3a76b-131">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="3a76b-132">変換関数に渡す引数として渡される`SelectMany()`の各ソース値の値の列挙可能なシーケンスを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a76b-132">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="3a76b-133">これらの列挙可能なシーケンスに連結して`SelectMany()`大きな&1; つのシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a76b-133">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="3a76b-134">次の&2; つの図は、これら&2; つのメソッドのアクションの概念の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="3a76b-134">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="3a76b-135">各ケースでは、セレクター (変換) 関数が、各ソース値から花の配列を選択することを仮定します。</span><span class="sxs-lookup"><span data-stu-id="3a76b-135">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="3a76b-136">この図を示して 方法`Select()`をソース コレクションと同じ数の要素を持つコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="3a76b-136">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="3a76b-137">![Select() のアクションの概念を示す図](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="3a76b-137">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="3a76b-138">この図を示して 方法`SelectMany()`各中間配列から各値を含む&1; つの最終的な結果値に中間一連の配列を連結します。</span><span class="sxs-lookup"><span data-stu-id="3a76b-138">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="3a76b-139">![SelectMany() のアクションを示すグラフィック。] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="3a76b-139">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="3a76b-140">コード例</span><span class="sxs-lookup"><span data-stu-id="3a76b-140">Code Example</span></span>  
 <span data-ttu-id="3a76b-141">次の例の動作を比較する`Select()`と`SelectMany()`です。</span><span class="sxs-lookup"><span data-stu-id="3a76b-141">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="3a76b-142">コードは、ソース コレクション内のそれぞれの花の名前の一覧から最初の&2; つの項目を実行することで、花の「いつも」を作成します。</span><span class="sxs-lookup"><span data-stu-id="3a76b-142">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="3a76b-143">この例は、「単一の値」でを変換関数は、<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>はそれ自体が値のコレクション</xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>。</span><span class="sxs-lookup"><span data-stu-id="3a76b-143">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="3a76b-144">余分な必要があります`For Each`各サブ シーケンス内の各文字列を列挙するためにループします。</span><span class="sxs-lookup"><span data-stu-id="3a76b-144">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a76b-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a76b-145">See Also</span></span>  
 <span data-ttu-id="3a76b-146"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="3a76b-146"><xref:System.Linq></span></span>   
<span data-ttu-id="3a76b-147"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="3a76b-147"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="3a76b-148"> [Select 句](../../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="3a76b-148"> [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="3a76b-149"> [方法: 結合を使用したデータを結合](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md) </span><span class="sxs-lookup"><span data-stu-id="3a76b-149"> [How to: Combine Data with Joins](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md) </span></span>  
<span data-ttu-id="3a76b-150"> [方法: 複数のソース (LINQ) (Visual Basic の場合) からオブジェクトのコレクション設定](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span><span class="sxs-lookup"><span data-stu-id="3a76b-150"> [How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span></span>  
<span data-ttu-id="3a76b-151"> [方法: 特定の種類での LINQ クエリ結果を返す](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md) </span><span class="sxs-lookup"><span data-stu-id="3a76b-151"> [How to: Return a LINQ Query Result as a Specific Type](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md) </span></span>  
<span data-ttu-id="3a76b-152"> [方法: 多くのファイルのファイル グループ (LINQ) (Visual Basic) を使用して分割](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="3a76b-152"> [How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
