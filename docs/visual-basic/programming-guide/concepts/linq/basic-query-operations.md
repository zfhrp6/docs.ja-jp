---
title: "基本的なクエリ操作 (Visual Basic) |Microsoft ドキュメント"
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
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
caps.latest.revision: 37
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1ced446d6646bd26b9169f5894138e12a38efde7
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="04398-102">基本的なクエリ操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04398-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="04398-103">このトピックでは、概要を[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]Visual Basic、およびクエリで実行される演算の一般的な種類の式。</span><span class="sxs-lookup"><span data-stu-id="04398-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="04398-104">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="04398-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="04398-105">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="04398-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="04398-106">クエリ</span><span class="sxs-lookup"><span data-stu-id="04398-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [<span data-ttu-id="04398-107">チュートリアル: Visual Basic でのクエリの作成</span><span class="sxs-lookup"><span data-stu-id="04398-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="04398-108">(From) データ ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="04398-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="04398-109">[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリでは、まず、クエリを実行するデータ ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="04398-109">In a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="04398-110">したがって、`From`クエリ内の句は常に最初にします。</span><span class="sxs-lookup"><span data-stu-id="04398-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="04398-111">クエリ演算子は、選択し、ソースの種類に基づく結果を形成します。</span><span class="sxs-lookup"><span data-stu-id="04398-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 <span data-ttu-id="04398-112">[!code-vb[VbLINQBasicOps&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-112">[!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]</span></span>  
  
 <span data-ttu-id="04398-113">`From`句データ ソースを指定`customers`、および*範囲変数*、`cust`です。</span><span class="sxs-lookup"><span data-stu-id="04398-113">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="04398-114">範囲変数ですが、ループの反復変数のように、クエリ式で実際の反復は行われません。</span><span class="sxs-lookup"><span data-stu-id="04398-114">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="04398-115">ときに、クエリを実行する多くの場合を使用して、`For Each`ループ、連続する各要素への参照として範囲変数`customers`します。</span><span class="sxs-lookup"><span data-stu-id="04398-115">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="04398-116">コンパイラの型を推論できるため`cust`、明示的に指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="04398-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="04398-117">明示的な型指定の有無に記述されたクエリの例については、次を参照してください。[クエリ操作 (Visual Basic) での型の関係](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)します。</span><span class="sxs-lookup"><span data-stu-id="04398-117">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="04398-118">使用する方法の詳細についての`From`Visual basic での句を参照してください[From 句](../../../../visual-basic/language-reference/queries/from-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="04398-118">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="04398-119">データのフィルター処理 (場所)</span><span class="sxs-lookup"><span data-stu-id="04398-119">Filtering Data (Where)</span></span>  
 <span data-ttu-id="04398-120">可能性があります、最も一般的なクエリ操作には、ブール式の形式でフィルターが適用しています。</span><span class="sxs-lookup"><span data-stu-id="04398-120">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="04398-121">クエリは、式が true の要素のみを返します。</span><span class="sxs-lookup"><span data-stu-id="04398-121">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="04398-122">A`Where`句を使用して、フィルター処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="04398-122">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="04398-123">フィルターは、結果のシーケンスに含めるデータ ソース内のどの要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="04398-123">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="04398-124">次の例では、ロンドンにあるアドレスを持っている顧客のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="04398-124">In the following example, only those customers who have an address in London are included.</span></span>  
  
 <span data-ttu-id="04398-125">[!code-vb[VbLINQBasicOps&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-125">[!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]</span></span>  
  
 <span data-ttu-id="04398-126">などの論理演算子を使用する`And`と`Or`でフィルター式を組み合わせて、`Where`句。</span><span class="sxs-lookup"><span data-stu-id="04398-126">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="04398-127">たとえば、ロンドン、およびメンバー名が Devon 顧客のみを返すには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="04398-127">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="04398-128">ロンドンまたはパリにある顧客を取得するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="04398-128">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="04398-129">使用する方法の詳細についての`Where`Visual basic での句を参照してください[Where 句の](../../../../visual-basic/language-reference/queries/where-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="04398-129">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="04398-130">データ (Order By) の並べ替え</span><span class="sxs-lookup"><span data-stu-id="04398-130">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="04398-131">多くの場合は、特定の順序に返されるデータを並べ替えると便利なです。</span><span class="sxs-lookup"><span data-stu-id="04398-131">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="04398-132">`Order By`句が指定されたフィールドでソートされた、返されるシーケンスの要素を発生します。</span><span class="sxs-lookup"><span data-stu-id="04398-132">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="04398-133">たとえば、次のクエリがに基づいて結果を並べ替えます、`Name`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="04398-133">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="04398-134">`Name`文字列では、a ~ Z、返されるデータは、アルファベット順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="04398-134">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 <span data-ttu-id="04398-135">[!code-vb[VbLINQBasicOps&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-135">[!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]</span></span>  
  
 <span data-ttu-id="04398-136">Z から A、逆の順序で結果の順序を使用して、`Order By...Descending`句。</span><span class="sxs-lookup"><span data-stu-id="04398-136">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="04398-137">既定値は`Ascending`がいずれも`Ascending`も`Descending`を指定します。</span><span class="sxs-lookup"><span data-stu-id="04398-137">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="04398-138">使用する方法の詳細についての`Order By`Visual basic での句を参照してください[Order By 句](../../../../visual-basic/language-reference/queries/order-by-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="04398-138">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="04398-139">データ (Select) を選択します。</span><span class="sxs-lookup"><span data-stu-id="04398-139">Selecting Data (Select)</span></span>  
 <span data-ttu-id="04398-140">`Select`句は、フォームと返される要素の内容を指定します。</span><span class="sxs-lookup"><span data-stu-id="04398-140">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="04398-141">完全な結果がで構成されているかどうかを指定するたとえば、`Customer`オブジェクト、1 つにすぎません`Customer`計算に基づいて、プロパティ、プロパティのサブセット、さまざまなデータ ソース、または新しい結果の種類からのプロパティの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="04398-141">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="04398-142">ときに、`Select`句がソース要素のコピー以外のものを発生した場合、操作が呼び出される、*投影*します。</span><span class="sxs-lookup"><span data-stu-id="04398-142">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="04398-143">完全なので構成されるコレクションを取得する`Customer`オブジェクトを範囲変数自体を選択します。</span><span class="sxs-lookup"><span data-stu-id="04398-143">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 <span data-ttu-id="04398-144">[!code-vb[VbLINQBasicOps&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-144">[!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]</span></span>  
  
 <span data-ttu-id="04398-145">場合、`Customer`インスタンスは、多くのフィールドを持つ大きいオブジェクトと名前を取得することだけが、選択できるように`cust.Name`の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="04398-145">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="04398-146">ローカル型推論のコレクションから結果の型が変更される`Customer`オブジェクトを文字列のコレクション。</span><span class="sxs-lookup"><span data-stu-id="04398-146">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 <span data-ttu-id="04398-147">[!code-vb[VbLINQBasicOps&#5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-147">[!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]</span></span>  
  
 <span data-ttu-id="04398-148">データ ソースから複数のフィールドを選択するには、2 つの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="04398-148">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="04398-149">`Select`句、結果に含めるフィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="04398-149">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="04398-150">コンパイラは、プロパティとしてこれらのフィールドを持つ匿名型を定義します。</span><span class="sxs-lookup"><span data-stu-id="04398-150">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="04398-151">詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="04398-151">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="04398-152">次の例で返される要素は、匿名型のインスタンスであるためにことはできません参照する型名で別の場所で、コード内。</span><span class="sxs-lookup"><span data-stu-id="04398-152">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="04398-153">型のコンパイラが指定の名前には、通常の Visual Basic コードでは無効な文字が含まれています。</span><span class="sxs-lookup"><span data-stu-id="04398-153">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="04398-154">次の例のクエリによって返されるコレクション内の要素で`londonCusts4`匿名型のインスタンス</span><span class="sxs-lookup"><span data-stu-id="04398-154">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     <span data-ttu-id="04398-155">[!code-vb[VbLINQBasicOps&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-155">[!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]</span></span>  
  
     <span data-ttu-id="04398-156">または</span><span class="sxs-lookup"><span data-stu-id="04398-156">-or-</span></span>  
  
-   <span data-ttu-id="04398-157">結果に含めるを作成し、型のインスタンスを初期化する特定のフィールドを含む名前付きの型を定義、`Select`句。</span><span class="sxs-lookup"><span data-stu-id="04398-157">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="04398-158">これらは、返されますが、コレクションの外部の個別の結果を使用している場合にのみ、またはメソッドの呼び出しでパラメーターとして渡すことがある場合は、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="04398-158">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="04398-159">型`londonCusts5`次の例では、IEnumerable (Of NamePhone)。</span><span class="sxs-lookup"><span data-stu-id="04398-159">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     <span data-ttu-id="04398-160">[!code-vb[VbLINQBasicOps&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-160">[!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]</span></span>  
  
     <span data-ttu-id="04398-161">[!code-vb[VbLINQBasicOps&#8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-161">[!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]</span></span>  
  
 <span data-ttu-id="04398-162">使用する方法の詳細についての`Select`Visual basic での句を参照してください[Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="04398-162">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="04398-163">結合のデータ (結合と Group Join)</span><span class="sxs-lookup"><span data-stu-id="04398-163">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="04398-164">1 つ以上のデータ ソースを組み合わせることができます、`From`方法はいくつかの句。</span><span class="sxs-lookup"><span data-stu-id="04398-164">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="04398-165">たとえば、次のコードでは、2 つのデータ ソースを使用して、結果に、これらの両方からのプロパティを暗黙的に結合します。</span><span class="sxs-lookup"><span data-stu-id="04398-165">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="04398-166">クエリでは、姓が母音で始まる受講者を選択します。</span><span class="sxs-lookup"><span data-stu-id="04398-166">The query selects students whose last names start with a vowel.</span></span>  
  
 <span data-ttu-id="04398-167">[!code-vb[VbLINQBasicOps&#9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-167">[!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04398-168">作成した学生の一覧にこのコードを実行する[方法: 項目の一覧を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)します。</span><span class="sxs-lookup"><span data-stu-id="04398-168">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="04398-169">`Join`キーワードは、 `INNER JOIN` sql です。</span><span class="sxs-lookup"><span data-stu-id="04398-169">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="04398-170">これは、2 つのコレクション内の要素間の一致するキー値に基づいて&2; つのコレクションを結合します。</span><span class="sxs-lookup"><span data-stu-id="04398-170">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="04398-171">このクエリは、キーの値が一致するコレクションの要素のすべてまたは一部を返します。</span><span class="sxs-lookup"><span data-stu-id="04398-171">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="04398-172">たとえば、次のコードでは、前の暗黙的な結合の操作が重複しています。</span><span class="sxs-lookup"><span data-stu-id="04398-172">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 <span data-ttu-id="04398-173">[!code-vb[VbLINQBasicOps&#10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-173">[!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]</span></span>  
  
 <span data-ttu-id="04398-174">`Group Join`同じように単一の階層コレクションにコレクションを結合、 `LEFT JOIN` sql です。</span><span class="sxs-lookup"><span data-stu-id="04398-174">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="04398-175">詳細については、次を参照してください。 [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)と[Group Join 句](../../../../visual-basic/language-reference/queries/group-join-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="04398-175">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="04398-176">データのグループ化 (グループ化)</span><span class="sxs-lookup"><span data-stu-id="04398-176">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="04398-177">追加することができます、`Group By`句、クエリ結果の要素の&1; つまたは複数のフィールドに従って要素をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="04398-177">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="04398-178">たとえば、次のコードでは、クラス、年ごと受講者をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="04398-178">For example, the following code groups students by class year.</span></span>  
  
 <span data-ttu-id="04398-179">[!code-vb[VbLINQBasicOps&#11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-179">[!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]</span></span>  
  
 <span data-ttu-id="04398-180">作成した生徒のリストを使用してこのコードを実行するかどうかは[する方法: 項目の一覧を作成する](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)からの出力、`For Each`ステートメントは。</span><span class="sxs-lookup"><span data-stu-id="04398-180">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="04398-181">年: Junior</span><span class="sxs-lookup"><span data-stu-id="04398-181">Year: Junior</span></span>  
  
 <span data-ttu-id="04398-182">Tucker、Michael</span><span class="sxs-lookup"><span data-stu-id="04398-182">Tucker, Michael</span></span>  
  
 <span data-ttu-id="04398-183">Garcia、Hugo</span><span class="sxs-lookup"><span data-stu-id="04398-183">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="04398-184">Garcia Debra</span><span class="sxs-lookup"><span data-stu-id="04398-184">Garcia, Debra</span></span>  
  
 <span data-ttu-id="04398-185">Tucker Lance</span><span class="sxs-lookup"><span data-stu-id="04398-185">Tucker, Lance</span></span>  
  
 <span data-ttu-id="04398-186">年: シニア</span><span class="sxs-lookup"><span data-stu-id="04398-186">Year: Senior</span></span>  
  
 <span data-ttu-id="04398-187">Omelchenko Svetlana</span><span class="sxs-lookup"><span data-stu-id="04398-187">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="04398-188">田山 Michiko</span><span class="sxs-lookup"><span data-stu-id="04398-188">Osada, Michiko</span></span>  
  
 <span data-ttu-id="04398-189">Fakhouri Fadi</span><span class="sxs-lookup"><span data-stu-id="04398-189">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="04398-190">Hanying Feng</span><span class="sxs-lookup"><span data-stu-id="04398-190">Feng, Hanying</span></span>  
  
 <span data-ttu-id="04398-191">Terry Adams</span><span class="sxs-lookup"><span data-stu-id="04398-191">Adams, Terry</span></span>  
  
 <span data-ttu-id="04398-192">年: Freshman</span><span class="sxs-lookup"><span data-stu-id="04398-192">Year: Freshman</span></span>  
  
 <span data-ttu-id="04398-193">Mortensen Sven</span><span class="sxs-lookup"><span data-stu-id="04398-193">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="04398-194">Garcia Cesar</span><span class="sxs-lookup"><span data-stu-id="04398-194">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="04398-195">次のコードに示すように変化は、クラス年を注文し、各学年の姓の順、受講者を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="04398-195">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 <span data-ttu-id="04398-196">[!code-vb[VbLINQBasicOps&#12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="04398-196">[!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]</span></span>  
  
 <span data-ttu-id="04398-197">詳細については`Group By`を参照してください[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="04398-197">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04398-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="04398-198">See Also</span></span>  
 <span data-ttu-id="04398-199"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="04398-199"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="04398-200"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="04398-200"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="04398-201"> [クエリ](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="04398-201"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="04398-202"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="04398-202"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="04398-203"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="04398-203"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)</span></span>
