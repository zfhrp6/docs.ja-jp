---
title: "LINQ によるデータ変換 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5b48dd495b843f8211a2b6e26df8a4f0618b254a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="58da0-102">LINQ によるデータ変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="58da0-102">Data Transformations with LINQ (C#)</span></span>
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]<span data-ttu-id="58da0-103"> で行うことができるのは、データの取得だけではありません。</span><span class="sxs-lookup"><span data-stu-id="58da0-103"> is not only about retrieving data.</span></span> <span data-ttu-id="58da0-104">データ変換のための強力なツールとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="58da0-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="58da0-105">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを使用することにより、ソース シーケンスを入力として使用し、さまざまな方法で加工して新しい出力シーケンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="58da0-105">By using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="58da0-106">要素自体を変更せずに、並べ替えやグループ化してシーケンス自体を変更できます。</span><span class="sxs-lookup"><span data-stu-id="58da0-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="58da0-107">しかし、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] のクエリの最も強力な機能は、新しい型を作成する機能です。</span><span class="sxs-lookup"><span data-stu-id="58da0-107">But perhaps the most powerful feature of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries is the ability to create new types.</span></span> <span data-ttu-id="58da0-108">この操作は [select](../../../../csharp/language-reference/keywords/select-clause.md) 句内で行います。</span><span class="sxs-lookup"><span data-stu-id="58da0-108">This is accomplished in the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="58da0-109">たとえば、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="58da0-109">For example, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="58da0-110">複数の入力シーケンスを結合して、新しい型の単一の出力シーケンスを作成する。</span><span class="sxs-lookup"><span data-stu-id="58da0-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
-   <span data-ttu-id="58da0-111">ソース シーケンス内の各要素の単一のプロパティまたは複数のプロパティを構成要素とする出力シーケンスを作成する。</span><span class="sxs-lookup"><span data-stu-id="58da0-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
-   <span data-ttu-id="58da0-112">ソース データに対して実行した操作の結果を構成要素とする出力シーケンスを作成する。</span><span class="sxs-lookup"><span data-stu-id="58da0-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
-   <span data-ttu-id="58da0-113">別の形式で出力シーケンスを作成する。</span><span class="sxs-lookup"><span data-stu-id="58da0-113">Create output sequences in a different format.</span></span> <span data-ttu-id="58da0-114">たとえば、SQL の行またはテキスト ファイルのデータを XML に変換できます。</span><span class="sxs-lookup"><span data-stu-id="58da0-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="58da0-115">これらはほんの一例です。</span><span class="sxs-lookup"><span data-stu-id="58da0-115">These are just several examples.</span></span> <span data-ttu-id="58da0-116">これらの変換を、同じクエリ内でさまざまな方法で組み合わせて使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="58da0-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="58da0-117">また、あるクエリの出力シーケンスを別のクエリの入力シーケンスとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="58da0-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="58da0-118">複数の入力を 1 つの出力シーケンスに結合する</span><span class="sxs-lookup"><span data-stu-id="58da0-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="58da0-119">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを使用して、複数の入力シーケンスの要素を含む 1 つの出力シーケンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="58da0-119">You can use a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="58da0-120">次の例は、2 つのインメモリ データ構造を結合する方法を示していますが、ソースが XML、SQL、または DataSet のデータを結合する場合にも同じ基本原則を適用できます。</span><span class="sxs-lookup"><span data-stu-id="58da0-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="58da0-121">次の 2 つのクラス型があるとします。</span><span class="sxs-lookup"><span data-stu-id="58da0-121">Assume the following two class types:</span></span>  
  
 <span data-ttu-id="58da0-122">[!code-cs[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="58da0-122">[!code-cs[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]</span></span>  
  
 <span data-ttu-id="58da0-123">クエリの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="58da0-123">The following example shows the query:</span></span>  
  
 <span data-ttu-id="58da0-124">[!code-cs[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="58da0-124">[!code-cs[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]</span></span>  
  
 <span data-ttu-id="58da0-125">詳細については、「[join 句](../../../../csharp/language-reference/keywords/join-clause.md)」および「[select 句](../../../../csharp/language-reference/keywords/select-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58da0-125">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="58da0-126">各ソース要素のサブセットを選択する</span><span class="sxs-lookup"><span data-stu-id="58da0-126">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="58da0-127">ソース シーケンスの各要素のサブセットを選択するには、主に次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="58da0-127">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1.  <span data-ttu-id="58da0-128">ソース要素の 1 つのメンバーのみを選択するには、ドット演算を使用します。</span><span class="sxs-lookup"><span data-stu-id="58da0-128">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="58da0-129">次の例で、`Customer` オブジェクトに `City` という文字列を含むいくつかのパブリック プロパティが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="58da0-129">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="58da0-130">このクエリを実行すると、文字列の出力シーケンスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="58da0-130">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  <span data-ttu-id="58da0-131">ソース要素からの複数のプロパティを含む要素を作成するには、名前付きオブジェクトまたは匿名型を指定したオブジェクト初期化子を使用します。</span><span class="sxs-lookup"><span data-stu-id="58da0-131">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="58da0-132">次の例は、匿名型を使用して各 `Customer` 要素の 2 つのプロパティをカプセル化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="58da0-132">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="58da0-133">詳細については、「[オブジェクト初期化子とコレクション初期化子](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」および「[匿名型](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58da0-133">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="58da0-134">インメモリ オブジェクトを XML に変換する</span><span class="sxs-lookup"><span data-stu-id="58da0-134">Transforming in-Memory Objects into XML</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="58da0-135"> クエリを使用すると、インメモリ データ構造、SQL データベース、[!INCLUDE[vstecado](~/includes/vstecado-md.md)] データセット、XML ストリーム、または XML ドキュメントの間でデータ変換を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="58da0-135"> queries make it easy to transform data between in-memory data structures, SQL databases, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] Datasets and XML streams or documents.</span></span> <span data-ttu-id="58da0-136">インメモリ データ構造のオブジェクトを XML 要素に変換する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="58da0-136">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 <span data-ttu-id="58da0-137">[!code-cs[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="58da0-137">[!code-cs[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]</span></span>  
  
 <span data-ttu-id="58da0-138">このコードを実行すると、次の XML 出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="58da0-138">The code produces the following XML output:</span></span>  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 <span data-ttu-id="58da0-139">詳細については、「[C# での XML ツリーの作成 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58da0-139">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="58da0-140">ソース要素に対して操作を実行する</span><span class="sxs-lookup"><span data-stu-id="58da0-140">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="58da0-141">出力シーケンスには、ソース シーケンスの要素または要素のプロパティが 1 つも含まれない場合があります。</span><span class="sxs-lookup"><span data-stu-id="58da0-141">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="58da0-142">代わりに、ソース要素を入力引数として使用することで計算された値のシーケンスを出力として生成できます。</span><span class="sxs-lookup"><span data-stu-id="58da0-142">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="58da0-143">次の簡単なクエリを実行すると、`double` 型の要素のソース シーケンスに基づく計算を表す値を含む文字列のシーケンスが出力されます。</span><span class="sxs-lookup"><span data-stu-id="58da0-143">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58da0-144">クエリが他のドメインに変換される場合、クエリ式でのメソッド呼び出しはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="58da0-144">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="58da0-145">たとえば、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] で C# の通常のメソッドを呼び出すことはできません。これは、C# のメソッドのコンテキストが SQL Server にないためです。</span><span class="sxs-lookup"><span data-stu-id="58da0-145">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="58da0-146">ただし、ストアド プロシージャをメソッドにマップして呼び出すことは可能です。</span><span class="sxs-lookup"><span data-stu-id="58da0-146">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="58da0-147">詳細については、「[ストアド プロシージャ](../../../../framework/data/adonet/sql/linq/stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58da0-147">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 <span data-ttu-id="58da0-148">[!code-cs[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="58da0-148">[!code-cs[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58da0-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="58da0-149">See Also</span></span>  
 <span data-ttu-id="58da0-150">[統合言語クエリ (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="58da0-150">[Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md) </span></span>  
 <span data-ttu-id="58da0-151">[LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="58da0-151">[LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
 <span data-ttu-id="58da0-152">[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md) </span><span class="sxs-lookup"><span data-stu-id="58da0-152">[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md) </span></span>  
 <span data-ttu-id="58da0-153">[LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="58da0-153">[LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) </span></span>  
 <span data-ttu-id="58da0-154">[LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="58da0-154">[LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="58da0-155">select 句</span><span class="sxs-lookup"><span data-stu-id="58da0-155">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)

