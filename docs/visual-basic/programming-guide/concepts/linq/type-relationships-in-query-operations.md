---
title: クエリ操作での型の関係 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: ed0072eeb44a17201ddab2af6f6a44fd14461029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655343"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="3dc89-102">クエリ操作での型の関係 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dc89-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="3dc89-103">使用される変数[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]クエリ操作は、厳密に型指定し、相互に互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc89-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="3dc89-104">厳密な型指定は、データ ソース、クエリ自体、およびクエリの実行に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3dc89-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="3dc89-105">次の図は、説明に使用される用語の識別、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="3dc89-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="3dc89-106">クエリの部分についての詳細については、次を参照してください。[基本的なクエリ操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 <span data-ttu-id="3dc89-107">![要素が強調表示された擬似コード クエリ。] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span><span class="sxs-lookup"><span data-stu-id="3dc89-107">![Pseudocode query with elements highlighted.](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span></span>  
<span data-ttu-id="3dc89-108">LINQ クエリの部分</span><span class="sxs-lookup"><span data-stu-id="3dc89-108">Parts of a LINQ query</span></span>  
  
 <span data-ttu-id="3dc89-109">クエリで範囲変数の型は、データ ソース内の要素の型と互換性のあるする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc89-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="3dc89-110">クエリ変数の型で定義されたシーケンスの要素と互換性のある必要があります、`Select`句。</span><span class="sxs-lookup"><span data-stu-id="3dc89-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="3dc89-111">最後に、シーケンスの要素の型もする必要がありますで使用されているループ コントロール変数の型と互換性のある、`For Each`クエリを実行するステートメント。</span><span class="sxs-lookup"><span data-stu-id="3dc89-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="3dc89-112">この厳密な型指定には、コンパイル時に型のエラーの識別が容易にします。</span><span class="sxs-lookup"><span data-stu-id="3dc89-112">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 <span data-ttu-id="3dc89-113">Visual Basic が容易厳密な型指定とも呼ばれるローカル型推論を実装することによって*暗黙の型指定*です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-113">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="3dc89-114">機能は、前の例で使用して、全体で使用されることが表示されます、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]のサンプルとドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="3dc89-114">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="3dc89-115">Visual basic でローカル型推論を使用するだけで完了、`Dim`ステートメントなし、`As`句。</span><span class="sxs-lookup"><span data-stu-id="3dc89-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="3dc89-116">次の例では、`city`を文字列として厳密に型指定します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-116">In the following example, `city` is strongly typed as a string.</span></span>  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="3dc89-117">ローカル型推論は場合にのみ機能`Option Infer`に設定されている`On`です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-117">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="3dc89-118">詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-118">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="3dc89-119">ただし、クエリでローカル型推論を使用する場合でも同じ型の関係は、データ ソース内の変数、クエリ変数、およびクエリの実行ループの間に存在します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-119">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="3dc89-120">作成しているときにこれらの型の関係の基本を理解すると便利ですが[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ、または作業用サンプルとドキュメントのコード例を使用します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-120">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="3dc89-121">たとえば、データ ソースから返される型と一致しない範囲変数の明示的な型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc89-121">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="3dc89-122">使用して、範囲変数の種類を指定することができます、`As`句。</span><span class="sxs-lookup"><span data-stu-id="3dc89-122">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="3dc89-123">その結果、エラーに変換すると、[縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と`Option Strict`に設定されている`On`です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-123">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="3dc89-124">したがって、データ ソースから取得した値を変換を実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3dc89-124">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="3dc89-125">使用して、明示的な範囲変数の型のデータ ソースからの値を変換することができます、<xref:System.Linq.Enumerable.Cast%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3dc89-125">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="3dc89-126">選択した値をキャストすることも、`Select`句の範囲変数の型とは異なる、明示的な型にします。</span><span class="sxs-lookup"><span data-stu-id="3dc89-126">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="3dc89-127">これらのポイントは、次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-127">These points are illustrated in the following code.</span></span>  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="3dc89-128">ソース データの全体の要素を返すクエリ</span><span class="sxs-lookup"><span data-stu-id="3dc89-128">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="3dc89-129">次の例は、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]操作、ソース データから選択した要素のシーケンスを返すクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-129">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="3dc89-130">ソース`names`文字列の配列が含まれ、クエリの出力は M という文字で始まる文字列を含むシーケンス。</span><span class="sxs-lookup"><span data-stu-id="3dc89-130">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 <span data-ttu-id="3dc89-131">これは次のコードに相当はより短く、記述を簡単にです。</span><span class="sxs-lookup"><span data-stu-id="3dc89-131">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="3dc89-132">クエリでローカル型推論の依存は、Visual Basic で推奨されるスタイルです。</span><span class="sxs-lookup"><span data-stu-id="3dc89-132">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 <span data-ttu-id="3dc89-133">次のリレーションシップは、種類が暗黙的または明示的に決定されるかどうか、前のコード例の両方に存在します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-133">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1.  <span data-ttu-id="3dc89-134">データ ソース内の要素の型`names`、範囲変数の型は、`name`クエリにします。</span><span class="sxs-lookup"><span data-stu-id="3dc89-134">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2.  <span data-ttu-id="3dc89-135">選択されているオブジェクトの種類`name`、クエリ変数の種類を決定`mNames`です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-135">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="3dc89-136">ここで`name`は string では、そのため、クエリ変数は Visual Basic での IEnumerable (Of String)。</span><span class="sxs-lookup"><span data-stu-id="3dc89-136">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3.  <span data-ttu-id="3dc89-137">定義されたクエリ`mNames`で実行される、`For Each`ループします。</span><span class="sxs-lookup"><span data-stu-id="3dc89-137">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="3dc89-138">ループは、クエリの実行の結果を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-138">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="3dc89-139">`mNames`が実行されると、ループの反復変数、文字列のシーケンスを返す`nm`も文字列です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-139">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="3dc89-140">選択した要素から 1 つのフィールドを返すクエリ</span><span class="sxs-lookup"><span data-stu-id="3dc89-140">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="3dc89-141">次の例は、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]クエリ、データ ソースから選択した各要素の一部分のみを含むシーケンスを返す操作。</span><span class="sxs-lookup"><span data-stu-id="3dc89-141">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="3dc89-142">クエリのコレクションを受け取って`Customer`、データ ソースとしてオブジェクトおよびプロジェクトのみ、`Name`プロパティを結果にします。</span><span class="sxs-lookup"><span data-stu-id="3dc89-142">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="3dc89-143">顧客名は、文字列であるため、クエリは出力として文字列のシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-143">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 <span data-ttu-id="3dc89-144">変数間のリレーションシップは、単純な例のようです。</span><span class="sxs-lookup"><span data-stu-id="3dc89-144">The relationships between variables are like those in the simpler example.</span></span>  
  
1.  <span data-ttu-id="3dc89-145">データ ソース内の要素の型`customers`、範囲変数の型は、`cust`クエリにします。</span><span class="sxs-lookup"><span data-stu-id="3dc89-145">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="3dc89-146">この例では型に対して`Customer`です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-146">In this example, that type is `Customer`.</span></span>  
  
2.  <span data-ttu-id="3dc89-147">`Select`ステートメントから返される、`Name`の各プロパティ`Customer`オブジェクト全体ではなくオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3dc89-147">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="3dc89-148">`Name`文字列で、クエリ変数`custNames`、もう一度されません (文字列) の IEnumerable の`Customer`します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-148">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3.  <span data-ttu-id="3dc89-149">`custNames`文字列のシーケンスを表す、`For Each`ループの反復変数`custName`文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc89-149">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="3dc89-150">ローカル型推論、せず、前の例を記述し、次の例を理解するのには煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="3dc89-150">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="3dc89-151">匿名型を必要とするクエリ</span><span class="sxs-lookup"><span data-stu-id="3dc89-151">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="3dc89-152">次の例より複雑な状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="3dc89-152">The following example shows a more complex situation.</span></span> <span data-ttu-id="3dc89-153">前の例では、すべての変数の型を明示的に指定するときに便利でした。</span><span class="sxs-lookup"><span data-stu-id="3dc89-153">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="3dc89-154">この例ではことはできません。</span><span class="sxs-lookup"><span data-stu-id="3dc89-154">In this example, it is impossible.</span></span> <span data-ttu-id="3dc89-155">全体を選択する代わりに`Customer`データ ソース、または各要素から 1 つのフィールドからの要素、`Select`このクエリ内の句は、元の 2 つのプロパティを返します`Customer`オブジェクト:`Name`と`City`です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-155">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="3dc89-156">応答、`Select`句、コンパイラはこれら 2 つのプロパティを含む匿名型を定義します。</span><span class="sxs-lookup"><span data-stu-id="3dc89-156">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="3dc89-157">実行結果`nameCityQuery`で、`For Each`ループは、新しい匿名型のインスタンスのコレクション。</span><span class="sxs-lookup"><span data-stu-id="3dc89-157">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="3dc89-158">型を指定することはできません、匿名型に使用可能な名前があるないため`nameCityQuery`または`custInfo`明示的にします。</span><span class="sxs-lookup"><span data-stu-id="3dc89-158">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="3dc89-159">つまり、匿名型を含む名前があるない型の代わりに使用する`String`で`IEnumerable(Of String)`です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-159">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="3dc89-160">詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dc89-160">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 <span data-ttu-id="3dc89-161">前の例ですべての変数の型を指定することはありませんが、リレーションシップが同じになります。</span><span class="sxs-lookup"><span data-stu-id="3dc89-161">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1.  <span data-ttu-id="3dc89-162">データ ソース内の要素の型が、クエリで範囲変数の型です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-162">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="3dc89-163">この例では`cust`のインスタンスは、`Customer`です。</span><span class="sxs-lookup"><span data-stu-id="3dc89-163">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2.  <span data-ttu-id="3dc89-164">`Select`ステートメントは、匿名型をクエリ変数を生成する`nameCityQuery`、匿名型として暗黙的に型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc89-164">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="3dc89-165">匿名型は、使用可能な名前を持たず、したがって、明示的に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="3dc89-165">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3.  <span data-ttu-id="3dc89-166">反復変数の型、`For Each`ループは、手順 2. で作成された匿名型。</span><span class="sxs-lookup"><span data-stu-id="3dc89-166">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="3dc89-167">型に使用可能な名前があるないために、ループの反復変数の型は暗黙的に決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc89-167">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc89-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dc89-168">See Also</span></span>  
 [<span data-ttu-id="3dc89-169">Visual Basic の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="3dc89-169">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="3dc89-170">匿名型</span><span class="sxs-lookup"><span data-stu-id="3dc89-170">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="3dc89-171">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="3dc89-171">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="3dc89-172">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="3dc89-172">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="3dc89-173">LINQ</span><span class="sxs-lookup"><span data-stu-id="3dc89-173">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="3dc89-174">クエリ</span><span class="sxs-lookup"><span data-stu-id="3dc89-174">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)
