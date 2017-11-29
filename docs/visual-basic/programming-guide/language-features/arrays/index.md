---
title: "Visual Basic における配列"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04deeccd19fd4edb3f2c88310d660eedf5c707d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-in-visual-basic"></a><span data-ttu-id="4c8f3-102">Visual Basic における配列</span><span class="sxs-lookup"><span data-stu-id="4c8f3-102">Arrays in Visual Basic</span></span>
<span data-ttu-id="4c8f3-103">配列は、学校の各学年の生徒の数など、互いに論理的に関連する一連の値です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-103">An array is a set of values that are logically related to each other, such as the number of students in each grade in a grammar school.</span></span>  <span data-ttu-id="4c8f3-104">Visual Basic for Applications (VBA) の配列についてのヘルプが必要な場合は、 [言語リファレンス](https://msdn.microsoft.com/library/office/gg264383\(v=office.14\).aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-104">If you are looking for help on arrays in Visual Basic for Applications (VBA), see the [language reference](https://msdn.microsoft.com/library/office/gg264383\(v=office.14\).aspx).</span></span>  
  
 <span data-ttu-id="4c8f3-105">配列を使うと、これらの関連する値を同じ名前で参照できます。配列の各要素を区別するには、インデックスまたは添字と呼ばれる番号を使います。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-105">By using an array, you can refer to these related values by the same name, and use a number that’s called an index or subscript to tell them apart.</span></span> <span data-ttu-id="4c8f3-106">個々の値は、配列の要素と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-106">The individual values are called the elements of the array.</span></span> <span data-ttu-id="4c8f3-107">これは、インデックス 0 から最も大きいインデックス値まで連続しています。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-107">They’re contiguous from index 0 through the highest index value.</span></span>  
  
 <span data-ttu-id="4c8f3-108">配列とは対照的に、単一の値が含まれている変数は *スカラー* 変数と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-108">In contrast to an array, a variable that contain a single value is called a *scalar* variable.</span></span>  
  
 <span data-ttu-id="4c8f3-109">説明する前に、簡単な例をいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-109">Some quick examples before explanation:</span></span>  
  
```vb  
'Declare a single-dimension array of 5 values  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set array element values  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
'Redefine the size of an existing array retaining the current values  
ReDim Preserve numbers(15)  
  
'Redefine the size of an existing array, resetting the values  
ReDim numbers(15)  
  
'Declare a multi-dimensional array  
Dim matrix(5, 5) As Double  
  
'Declare a multi-dimensional array and set array element values  
Dim matrix = New Integer(4, 4) {{1, 2}, {3, 4}, {5, 6}, {7, 8}}  
  
'Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 <span data-ttu-id="4c8f3-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4c8f3-110">**In this topic**</span></span>  
  
-   [<span data-ttu-id="4c8f3-111">単純な配列の配列要素</span><span class="sxs-lookup"><span data-stu-id="4c8f3-111">Array Elements in a Simple Array</span></span>](#BKMK_ArrayElements)  
  
-   [<span data-ttu-id="4c8f3-112">配列の作成</span><span class="sxs-lookup"><span data-stu-id="4c8f3-112">Creating an Array</span></span>](#BKMK_CreatingAnArray)  
  
-   [<span data-ttu-id="4c8f3-113">配列への値の格納</span><span class="sxs-lookup"><span data-stu-id="4c8f3-113">Storing Values in an Array</span></span>](#BKMK_StoringValues)  
  
-   [<span data-ttu-id="4c8f3-114">配列への初期値の取り込み</span><span class="sxs-lookup"><span data-stu-id="4c8f3-114">Populating an Array with Initial Values</span></span>](#BKMK_Populating)  
  
    -   [<span data-ttu-id="4c8f3-115">入れ子になった配列リテラル</span><span class="sxs-lookup"><span data-stu-id="4c8f3-115">Nested Array Literals</span></span>](#BKMK_NestedArrayLiterals)  
  
-   [<span data-ttu-id="4c8f3-116">配列の反復処理</span><span class="sxs-lookup"><span data-stu-id="4c8f3-116">Iterating Through an Array</span></span>](#BKMK_Iterating)  
  
-   [<span data-ttu-id="4c8f3-117">戻り値およびパラメーターとしての配列</span><span class="sxs-lookup"><span data-stu-id="4c8f3-117">Arrays as Return Values and Parameters</span></span>](#BKMK_ReturnValues)  
  
-   [<span data-ttu-id="4c8f3-118">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="4c8f3-118">Jagged Arrays</span></span>](#BKMK_JaggedArrays)  
  
-   [<span data-ttu-id="4c8f3-119">長さ 0 の配列</span><span class="sxs-lookup"><span data-stu-id="4c8f3-119">Zero-Length Arrays</span></span>](#BKMK_ZeroLength)  
  
-   [<span data-ttu-id="4c8f3-120">配列のサイズ</span><span class="sxs-lookup"><span data-stu-id="4c8f3-120">Array Size</span></span>](#BKMK_ArraySize)  
  
-   [<span data-ttu-id="4c8f3-121">配列の型および他の型</span><span class="sxs-lookup"><span data-stu-id="4c8f3-121">Array Types and Other Types</span></span>](#BKMK_ArrayTypes)  
  
-   [<span data-ttu-id="4c8f3-122">配列の代わりとしてのコレクション</span><span class="sxs-lookup"><span data-stu-id="4c8f3-122">Collections as an Alternative to Arrays</span></span>](#BKMK_Collections)  
  
##  <span data-ttu-id="4c8f3-123"><a name="BKMK_ArrayElements"></a> 単純な配列の配列要素</span><span class="sxs-lookup"><span data-stu-id="4c8f3-123"><a name="BKMK_ArrayElements"></a> Array Elements in a Simple Array</span></span>  
 <span data-ttu-id="4c8f3-124">次の例では、学校の各学年の生徒の数を保持するために、配列変数を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-124">The following example declares an array variable to hold the number of students in each grade in a grammar school.</span></span>  
  
 [!code-vb[VbVbalrArrays#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#2)]  
  
 <span data-ttu-id="4c8f3-125">上の例の `students` 配列には、7 つの要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-125">The array `students` in the preceding example contains seven elements.</span></span> <span data-ttu-id="4c8f3-126">要素のインデックスの範囲は 0 から 6 までです。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-126">The indexes of the elements range from 0 through 6.</span></span> <span data-ttu-id="4c8f3-127">7 つの変数を宣言するよりも、この配列の方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-127">Having this array is simpler than declaring seven variables.</span></span>  
  
 <span data-ttu-id="4c8f3-128">`students`配列を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-128">The following illustration shows the array `students`.</span></span> <span data-ttu-id="4c8f3-129">配列の各要素は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-129">For each element of the array:</span></span>  
  
-   <span data-ttu-id="4c8f3-130">要素のインデックスは、学年を表します (インデックス 0 は幼稚園を表します)。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-130">The index of the element represents the grade (index 0 represents kindergarten).</span></span>  
  
-   <span data-ttu-id="4c8f3-131">要素に含まれている値は、その学年の生徒の数を表します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-131">The value that’s contained in the element represents the number of students in that grade.</span></span>  
  
 <span data-ttu-id="4c8f3-132">![生徒数を示す配列の図](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")</span><span class="sxs-lookup"><span data-stu-id="4c8f3-132">![Picture of array showing numbers of students](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")</span></span>  
<span data-ttu-id="4c8f3-133">"生徒" 配列の要素</span><span class="sxs-lookup"><span data-stu-id="4c8f3-133">Elements of the "students" array</span></span>  
  
 <span data-ttu-id="4c8f3-134">次の例は、 `students`配列の先頭の要素、2 番目の要素、および最後の要素を参照する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-134">The following example shows how to refer to the first, second, and last element of the array `students`.</span></span>  
  
 [!code-vb[VbVbalrArrays#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#3)]  
  
 <span data-ttu-id="4c8f3-135">インデックスを持たない配列変数名だけを使用して、配列全体を参照できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-135">You can refer to the array as a whole by using just the array variable name without indexes.</span></span>  
  
 <span data-ttu-id="4c8f3-136">前の例の `students` 配列では、1 つのインデックスが使用されており、これを 1 次元と言います。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-136">The array `students` in the preceding example uses one index and is said to be one-dimensional.</span></span> <span data-ttu-id="4c8f3-137">複数のインデックスまたは添字が使用されている配列は、多次元と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-137">An array that uses more than one index or subscript is called multidimensional.</span></span> <span data-ttu-id="4c8f3-138">詳細については、このトピックの残りの部分と「 [Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-138">For more information, see the rest of this topic and [Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
##  <span data-ttu-id="4c8f3-139"><a name="BKMK_CreatingAnArray"></a> 配列の作成</span><span class="sxs-lookup"><span data-stu-id="4c8f3-139"><a name="BKMK_CreatingAnArray"></a> Creating an Array</span></span>  
 <span data-ttu-id="4c8f3-140">配列のサイズは、さまざまな方法で定義できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-140">You can define the size of an array several ways.</span></span> <span data-ttu-id="4c8f3-141">次の例に示すように、配列を宣言するときにサイズを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-141">You can supply the size when the array is declared, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrArrays#12](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#12)]  
  
 <span data-ttu-id="4c8f3-142">また、次の例に示すように、 `New` 句を使用して配列を作成するときにサイズを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-142">You can also use a `New` clause to supply the size of an array when it’s created, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrArrays#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#11)]  
  
 <span data-ttu-id="4c8f3-143">既存の配列がある場合は、 `Redim` ステートメントを使用してサイズを再定義できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-143">If you have an existing array, you can redefine its size by using the `Redim` statement.</span></span> <span data-ttu-id="4c8f3-144">`Redim` ステートメントでは、配列に格納されている値を保持するように指定することも、空の配列を作成するように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-144">You can specify that the `Redim` statement should keep the values that are in the array, or you can specify that it create an empty array.</span></span> <span data-ttu-id="4c8f3-145">次に、 `Redim` ステートメントを使用して既存の配列のサイズを変更する例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-145">The following example shows different uses of the `Redim` statement to modify the size of an existing array.</span></span>  
  
 [!code-vb[VbVbalrArrays#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#13)]  
  
 <span data-ttu-id="4c8f3-146">詳細については、「[ReDim ステートメント](../../../../visual-basic/language-reference/statements/redim-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-146">For more information, see [ReDim Statement](../../../../visual-basic/language-reference/statements/redim-statement.md).</span></span>  
  
##  <span data-ttu-id="4c8f3-147"><a name="BKMK_StoringValues"></a> 配列への値の格納</span><span class="sxs-lookup"><span data-stu-id="4c8f3-147"><a name="BKMK_StoringValues"></a> Storing Values in an Array</span></span>  
 <span data-ttu-id="4c8f3-148">配列のそれぞれの位置には、 `Integer`型のインデックスを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-148">You can access each location in an array by using an index of type `Integer`.</span></span> <span data-ttu-id="4c8f3-149">かっこで囲まれたインデックスを使用して配列のそれぞれの位置を参照することで、配列の値を格納および取得することができます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-149">You can store and retrieve values in an array by referencing each array location by using its index enclosed in parentheses.</span></span> <span data-ttu-id="4c8f3-150">多次元配列のインデックスはコンマ (,) で区切ります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-150">Indexes for multi-dimensional arrays are separated by commas (,).</span></span> <span data-ttu-id="4c8f3-151">配列の次元ごとに 1 つのインデックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-151">You need one index for each array dimension.</span></span> <span data-ttu-id="4c8f3-152">配列に値を格納するステートメントの例を示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-152">The following example shows some statements that store values in arrays.</span></span>  
  
 [!code-vb[VbVbalrArrays#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#5)]  
  
 <span data-ttu-id="4c8f3-153">配列から値を取得するステートメントの例を示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-153">The following example shows some statements that get values from arrays.</span></span>  
  
 [!code-vb[VbVbalrArrays#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#6)]  
  
##  <span data-ttu-id="4c8f3-154"><a name="BKMK_Populating"></a> 配列への初期値の取り込み</span><span class="sxs-lookup"><span data-stu-id="4c8f3-154"><a name="BKMK_Populating"></a> Populating an Array with Initial Values</span></span>  
 <span data-ttu-id="4c8f3-155">配列リテラルを使用すると、初期値のセットを含む配列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-155">By using an array literal, you can create an array that contains an initial set of values.</span></span> <span data-ttu-id="4c8f3-156">配列リテラルは、中かっこ (`{}`) で囲んだ値のコンマ区切りの一覧で構成されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-156">An array literal consists of a list of comma-separated values that are enclosed in braces (`{}`).</span></span>  
  
 <span data-ttu-id="4c8f3-157">配列リテラルを使用して配列を作成する場合、配列の型を指定するか、型の推定を使用して配列の型を決定することができます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-157">When you create an array by using an array literal, you can either supply the array type or use type inference to determine the array type.</span></span> <span data-ttu-id="4c8f3-158">この 2 つの方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-158">The following code shows both options.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#3)]  
  
 <span data-ttu-id="4c8f3-159">型の推定を使用する場合、配列の型は、配列リテラルに指定された値の一覧の中で最も優先度の高い型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-159">When you use type inference, the type of the array is determined by the dominant type in the list of values that’s supplied for the array literal.</span></span> <span data-ttu-id="4c8f3-160">最も優先度の高い型は、配列リテラル内の他のすべての型から拡大変換できる一意の型です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-160">The dominant type is a unique type to which all other types in the array literal can widen.</span></span> <span data-ttu-id="4c8f3-161">この一意の型を特定できない場合、最も優先度の高い型は、配列内の他のすべての型から縮小変換できる一意の型になります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-161">If this unique type can’t be determined, the dominant type is the unique type to which all other types in the array can narrow.</span></span> <span data-ttu-id="4c8f3-162">これらの一意の型をどちらも特定できない場合は、 `Object`が最も優先度の高い型になります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-162">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="4c8f3-163">たとえば、配列リテラルに指定された値の一覧に `Integer`型、 `Long`型、および `Double`型の値が含まれている場合、結果の配列の型は `Double`です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-163">For example, if the list of values that’s supplied to the array literal contains values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="4c8f3-164">`Integer` と `Long` は `Double`にのみ拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-164">Both `Integer` and `Long` widen only to `Double`.</span></span> <span data-ttu-id="4c8f3-165">そのため、 `Double` が最も優先度の高い型になります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-165">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="4c8f3-166">詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-166">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="4c8f3-167">これらの推定規則は、クラス メンバーで定義されたローカル変数である配列についての型の推定に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-167">These inference rules apply to types that are inferred for arrays that are local variables that are defined in a class member.</span></span> <span data-ttu-id="4c8f3-168">クラス レベルの変数を作成するときに配列リテラルを使用することはできますが、クラス レベルで型の推定を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-168">Although you can use array literals when you create class-level variables, you can’t use type inference at the class level.</span></span> <span data-ttu-id="4c8f3-169">そのため、クラス レベルで指定された配列リテラルでは、配列リテラルに指定された値の型は `Object`型であると推論されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-169">As a result, array literals that are specified at the class level infer the values that are supplied for the array literal as type `Object`.</span></span>  
  
 <span data-ttu-id="4c8f3-170">配列リテラルを使用して作成した配列の要素の型を明示的に指定することができます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-170">You can explicitly specify the type of the elements in an array that’s created by using an array literal.</span></span> <span data-ttu-id="4c8f3-171">この場合、配列リテラル内の値を配列の要素の型に拡大変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-171">In this case, the values in the array literal must widen to the type of the elements of the array.</span></span> <span data-ttu-id="4c8f3-172">整数の一覧から `Double` 型の配列を作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-172">The following code example creates an array of type `Double` from a list of integers.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#4)]  
  
###  <span data-ttu-id="4c8f3-173"><a name="BKMK_NestedArrayLiterals"></a> 入れ子になった配列リテラル</span><span class="sxs-lookup"><span data-stu-id="4c8f3-173"><a name="BKMK_NestedArrayLiterals"></a> Nested Array Literals</span></span>  
 <span data-ttu-id="4c8f3-174">入れ子になった配列リテラルを使用すると、多次元配列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-174">You can create a multidimensional array by using nested array literals.</span></span> <span data-ttu-id="4c8f3-175">入れ子になった配列リテラルに含める次元および次元数 (ランク) は、結果の配列と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-175">Nested array literals must have a dimension and number of dimensions, or rank, that’s consistent with the resulting array.</span></span> <span data-ttu-id="4c8f3-176">配列リテラルを使用して整数の 2 次元配列を作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-176">The following code example creates a two-dimensional array of integers by using an array literal.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#7)]  
  
 <span data-ttu-id="4c8f3-177">上記の例では、入れ子になった配列リテラル内の要素の数が一致しないとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-177">In the previous example, an error would occur if the number of elements in the nested array literals didn’t match.</span></span> <span data-ttu-id="4c8f3-178">また、2 次元以外の配列変数が明示的に宣言された場合もエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-178">An error would also occur if you explicitly declared the array variable to be other than two-dimensional.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c8f3-179">入れ子になった配列リテラルで異なる次元を指定することによるエラーを回避するには、内側の配列をかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-179">You can avoid an error when you supply nested array literals of different dimensions by enclosing the inner array literals in parentheses.</span></span> <span data-ttu-id="4c8f3-180">次のコードに示すようにかっこで囲むと、配列リテラル式の評価が実行され、そこで得られた値が外側の配列リテラルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-180">The parentheses force the array literal expression to be evaluated, and the resulting values are used with the outer array literal, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#11)]  
  
 <span data-ttu-id="4c8f3-181">入れ子になった配列リテラルを使用して多次元配列を作成する場合、型の推定を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-181">When you create a multidimensional array by using nested array literals, you can use type inference.</span></span> <span data-ttu-id="4c8f3-182">型の推定を使用すると、推定される型は、入れ子レベルのすべての配列リテラルに含まれるすべての値の中で最も優先度の高い型になります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-182">When you use type inference, the inferred type is the dominant type for all the values in all the array literals for a nesting level.</span></span> <span data-ttu-id="4c8f3-183">`Double` 型と `Integer` 型の値から `Double`型の 2 次元配列を作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-183">The following code example creates a two-dimensional array of type `Double` from values that are of type `Integer` and `Double`.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#8)]  
  
 <span data-ttu-id="4c8f3-184">他の例については、「[方法: Visual Basic で配列変数を初期化する](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-184">For additional examples, see [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).</span></span>  
  
##  <span data-ttu-id="4c8f3-185"><a name="BKMK_Iterating"></a> 配列の反復処理</span><span class="sxs-lookup"><span data-stu-id="4c8f3-185"><a name="BKMK_Iterating"></a> Iterating Through an Array</span></span>  
 <span data-ttu-id="4c8f3-186">配列を反復処理するときには、配列の各要素に、最もインデックスが小さいものから順番にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-186">When you iterate through an array, you access each element in the array from the lowest index to the highest index.</span></span>  
  
 <span data-ttu-id="4c8f3-187">次の例では、[For...Next ステートメント](../../../../visual-basic/language-reference/statements/for-next-statement.md)を使用して 1 次元配列を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-187">The following example iterates through a one-dimensional array by using the [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span> <span data-ttu-id="4c8f3-188"><xref:System.Array.GetUpperBound%2A> メソッドでは、インデックスが保持できる一番高い値が返されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-188">The <xref:System.Array.GetUpperBound%2A> method returns the highest value that the index can have.</span></span> <span data-ttu-id="4c8f3-189">一番低いインデックス値は常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-189">The lowest index value is always 0.</span></span>  
  
 [!code-vb[VbVbalrArrays#41](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#41)]  
  
 <span data-ttu-id="4c8f3-190">次の例では、 `For...Next` ステートメントを使用して多次元配列を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-190">The following example iterates through a multidimensional array by using a `For...Next` statement.</span></span> <span data-ttu-id="4c8f3-191"><xref:System.Array.GetUpperBound%2A> メソッドには、次元を指定するパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-191">The <xref:System.Array.GetUpperBound%2A> method has a parameter that specifies the dimension.</span></span> <span data-ttu-id="4c8f3-192">`GetUpperBound(0)` は最初の次元の最も大きいインデックス値を返し、 `GetUpperBound(1)` は 2 番目の次元の最も大きいインデックス値を返します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-192">`GetUpperBound(0)` returns the high index value for the first dimension, and `GetUpperBound(1)` returns the high index value for the second dimension.</span></span>  
  
 [!code-vb[VbVbalrArrays#42](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#42)]  
  
 <span data-ttu-id="4c8f3-193">次の例では、[For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)を使用して 1 次元配列を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-193">The following example iterates through a one-dimensional array by using a [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 [!code-vb[VbVbalrArrays#43](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#43)]  
  
 <span data-ttu-id="4c8f3-194">次の例では、 `For Each...Next` ステートメントを使用して多次元配列を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-194">The following example iterates through a multidimensional array by using a `For Each...Next` statement.</span></span> <span data-ttu-id="4c8f3-195">ただし、 `For…Next` ステートメントを使用するより、前の例のように、入れ子になった `For Each…Next` ステートメントを使用した方が、多次元配列の要素をより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-195">However, you have more control over the elements of a multidimensional array if you use a nested `For…Next` statement, as in a previous example, instead of a `For Each…Next` statement.</span></span>  
  
 [!code-vb[VbVbalrArrays#44](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#44)]  
  
##  <span data-ttu-id="4c8f3-196"><a name="BKMK_ReturnValues"></a> 戻り値およびパラメーターとしての配列</span><span class="sxs-lookup"><span data-stu-id="4c8f3-196"><a name="BKMK_ReturnValues"></a> Arrays as Return Values and Parameters</span></span>  
 <span data-ttu-id="4c8f3-197">`Function` プロシージャから配列を返すには、[Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)の戻り値の型として配列のデータ型と次元数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-197">To return an array from a `Function` procedure, specify the array data type and the number of dimensions as the return type of the [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="4c8f3-198">関数内で、同じデータ型と次元数を持つローカルの配列変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-198">Within the function, declare a local array variable with same data type and number of dimensions.</span></span> <span data-ttu-id="4c8f3-199">[Return ステートメント](../../../../visual-basic/language-reference/statements/return-statement.md)には、かっこを使用せずにローカルの配列変数を含めます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-199">In the [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md), include the local array variable without parentheses.</span></span>  
  
 <span data-ttu-id="4c8f3-200">配列を `Sub` プロシージャまたは `Function` プロシージャのパラメーターとして指定するには、パラメーターを配列として定義して、データ型と次元数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-200">To specify an array as a parameter to a `Sub` or `Function` procedure, define the parameter as an array with a specified data type and number of dimensions.</span></span> <span data-ttu-id="4c8f3-201">プロシージャの呼び出しで、データ型と次元数が同じ配列変数を渡します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-201">In the call to the procedure, send an array variable with the same data type and number of dimensions.</span></span>  
  
 <span data-ttu-id="4c8f3-202">次の例では、 `GetNumbers` 関数が `Integer()`を返します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-202">In the following example, the `GetNumbers` function returns an `Integer()`.</span></span> <span data-ttu-id="4c8f3-203">この配列型は、 `Integer`型の 1 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-203">This array type is a one dimensional array of type `Integer`.</span></span> <span data-ttu-id="4c8f3-204">`ShowNumbers` プロシージャは、 `Integer()` の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-204">The `ShowNumbers` procedure accepts an `Integer()` argument.</span></span>  
  
 [!code-vb[VbVbalrArrays#51](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#51)]  
  
 <span data-ttu-id="4c8f3-205">次の例では、 `GetNumbersMultiDim` 関数が `Integer(,)`を返します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-205">In the following example, the `GetNumbersMultiDim` function returns an `Integer(,)`.</span></span> <span data-ttu-id="4c8f3-206">この配列型は、 `Integer`型の 2 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-206">This array type is a two dimensional array of type `Integer`.</span></span>  <span data-ttu-id="4c8f3-207">`ShowNumbersMultiDim` プロシージャは、 `Integer(,)` の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-207">The `ShowNumbersMultiDim` procedure accepts an `Integer(,)` argument.</span></span>  
  
 [!code-vb[VbVbalrArrays#52](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#52)]  
  
##  <span data-ttu-id="4c8f3-208"><a name="BKMK_JaggedArrays"></a> ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="4c8f3-208"><a name="BKMK_JaggedArrays"></a> Jagged Arrays</span></span>  
 <span data-ttu-id="4c8f3-209">他の配列を要素として保持する配列を、配列の配列またはジャグ配列と呼びます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-209">An array that holds other arrays as elements is known as an array of arrays or a jagged array.</span></span> <span data-ttu-id="4c8f3-210">ジャグ配列と、ジャグ配列の各要素は、1 次元でも多次元でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-210">A jagged array and each element in a jagged array can have one or more dimensions.</span></span> <span data-ttu-id="4c8f3-211">アプリケーションのデータ構造は、2 次元の配列であっても四角形の 2 次元配列ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-211">Sometimes the data structure in your application is two-dimensional but not rectangular.</span></span>  
  
 <span data-ttu-id="4c8f3-212">次の例には、各要素が日の配列である月の配列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-212">The following example has an array of months, each element of which is an array of days.</span></span> <span data-ttu-id="4c8f3-213">月によって日数が異なるため、月要素は四角形の 2 次元配列を形成しません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-213">Because different months have different numbers of days, the elements don’t form a rectangular two-dimensional array.</span></span> <span data-ttu-id="4c8f3-214">そのため、多次元配列の代わりにジャグ配列が使用されています。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-214">Therefore, a jagged array is used instead of a multidimensional array.</span></span>  
  
 [!code-vb[VbVbalrArrays#21](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#21)]  
  
##  <span data-ttu-id="4c8f3-215"><a name="BKMK_ZeroLength"></a> 長さ 0 の配列</span><span class="sxs-lookup"><span data-stu-id="4c8f3-215"><a name="BKMK_ZeroLength"></a> Zero-Length Arrays</span></span>  
 <span data-ttu-id="4c8f3-216">要素を持たない配列は、長さ 0 の配列と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-216">An array that contains no elements is also called a zero-length array.</span></span> <span data-ttu-id="4c8f3-217">長さ 0 の配列を保持する変数の値は、 `Nothing`ではありません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-217">A variable that holds a zero-length array doesn’t have the value `Nothing`.</span></span> <span data-ttu-id="4c8f3-218">要素を持たない配列を作成するには、次の例のように配列の次元のいずれかを -1 と宣言します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-218">To create an array that has no elements, declare one of the array's dimensions to be -1, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrArrays#14](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#14)]  
  
 <span data-ttu-id="4c8f3-219">次のような場合に、長さ 0 の配列を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-219">You might need to create a zero-length array under the following circumstances:</span></span>  
  
-   <span data-ttu-id="4c8f3-220"><xref:System.NullReferenceException> 例外を発生させずにコードで <xref:System.Array> クラスのメンバー ( <xref:System.Array.Length%2A> 、 <xref:System.Array.Rank%2A>など) にアクセスしたり [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 関数 ( <xref:Microsoft.VisualBasic.Information.UBound%2A>など) を呼び出したりする必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-220">Without risking a <xref:System.NullReferenceException> exception, your code must access members of the <xref:System.Array> class, such as <xref:System.Array.Length%2A> or <xref:System.Array.Rank%2A>, or call a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function such as <xref:Microsoft.VisualBasic.Information.UBound%2A>.</span></span>  
  
-   <span data-ttu-id="4c8f3-221">特別なケースとして、 `Nothing` をチェックする必要性をなくすことによって利用側のコードを簡素化する場合。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-221">You want to keep the consuming code simpler by not having to check for `Nothing` as a special case.</span></span>  
  
-   <span data-ttu-id="4c8f3-222">コードで、長さ 0 の配列を 1 つ以上のプロシージャに渡す必要があるアプリケーション プログラミング インターフェイス (API: Application Programming Interface) とやり取りする場合、または API の 1 つ以上のプロシージャから長さ 0 の配列が返される場合。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-222">Your code interacts with an application programming interface (API) that either requires you to pass a zero-length array to one or more procedures or returns a zero-length array from one or more procedures.</span></span>  
  
##  <span data-ttu-id="4c8f3-223"><a name="BKMK_ArraySize"></a> 配列のサイズ</span><span class="sxs-lookup"><span data-stu-id="4c8f3-223"><a name="BKMK_ArraySize"></a> Array Size</span></span>  
 <span data-ttu-id="4c8f3-224">配列のサイズは、そのすべての次元の長さの積です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-224">The size of an array is the product of the lengths of all its dimensions.</span></span> <span data-ttu-id="4c8f3-225">これは、現在配列に含まれている要素の総数を表します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-225">It represents the total number of elements currently contained in the array.</span></span>  
  
 <span data-ttu-id="4c8f3-226">次の例では 3 次元配列を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-226">The following example declares a three-dimensional array.</span></span>  
  
```vb
Dim prices(3, 4, 5) As Long  
```  
  
 <span data-ttu-id="4c8f3-227">変数 `prices` の配列の全体のサイズは、(3 + 1) x (4 + 1) x (5 + 1) = 120 です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-227">The overall size of the array in variable `prices` is (3 + 1) x (4 + 1) x (5 + 1) = 120.</span></span>  
  
 <span data-ttu-id="4c8f3-228">配列のサイズは、<xref:System.Array.Length%2A> プロパティを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-228">You can find the size of an array by using the <xref:System.Array.Length%2A> property.</span></span> <span data-ttu-id="4c8f3-229">多次元配列の各次元の長さは、 <xref:System.Array.GetLength%2A> メソッドを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-229">You can find the length of each dimension of a multi-dimensional array by using the <xref:System.Array.GetLength%2A> method.</span></span>  
  
 <span data-ttu-id="4c8f3-230">配列変数のサイズを変更するには、新しい配列オブジェクトを割り当てるか、 `ReDim` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-230">You can resize an array variable by assigning a new array object to it or by using the `ReDim` statement.</span></span>  
  
 <span data-ttu-id="4c8f3-231">配列のサイズを扱う際に考慮する必要がある点がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-231">There are several things to keep in mind when dealing with the size of an array.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="4c8f3-232">次元の長さ</span><span class="sxs-lookup"><span data-stu-id="4c8f3-232">Dimension Length</span></span>|<span data-ttu-id="4c8f3-233">各次元のインデックスは 0 ベースであり、範囲は 0 から上限です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-233">The index of each dimension is 0-based, which means it ranges from 0 through its upper bound.</span></span> <span data-ttu-id="4c8f3-234">したがって、次元の長さは、その次元に対する宣言された上限よりも 1 だけ大きくなります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-234">Therefore, the length of a given dimension is greater by 1 than the declared upper bound for that dimension.</span></span>|  
|<span data-ttu-id="4c8f3-235">長さの制限</span><span class="sxs-lookup"><span data-stu-id="4c8f3-235">Length Limits</span></span>|<span data-ttu-id="4c8f3-236">配列のすべての次元の長さは、`Integer` データ型の最大値に制限されます。最大値は (2 ^ 31) - 1 です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-236">The length of every dimension of an array is limited to the maximum value of the `Integer` data type, which is (2 ^ 31) - 1.</span></span> <span data-ttu-id="4c8f3-237">しかし、配列のサイズの総数も、システムで利用できるメモリによって制限されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-237">However, the total size of an array is also limited by the memory available on your system.</span></span> <span data-ttu-id="4c8f3-238">利用できる RAM の容量を超える配列を初期化しようとすると、共通言語ランタイムは <xref:System.OutOfMemoryException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-238">If you attempt to initialize an array that exceeds the amount of available RAM, the common language runtime throws an <xref:System.OutOfMemoryException> exception.</span></span>|  
|<span data-ttu-id="4c8f3-239">サイズおよび要素のサイズ</span><span class="sxs-lookup"><span data-stu-id="4c8f3-239">Size and Element Size</span></span>|<span data-ttu-id="4c8f3-240">配列のサイズは、その要素のデータ型には依存しません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-240">An array's size is independent of the data type of its elements.</span></span> <span data-ttu-id="4c8f3-241">サイズは常に、使用するストレージのバイト数ではなく、要素の合計数を表します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-241">The size always represents the total number of elements, not the number of bytes that they consume in storage.</span></span>|  
|<span data-ttu-id="4c8f3-242">メモリの使用量</span><span class="sxs-lookup"><span data-stu-id="4c8f3-242">Memory Consumption</span></span>|<span data-ttu-id="4c8f3-243">配列がどのようにメモリに格納されるかに関して、前提を置くことは安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-243">It is not safe to make any assumptions regarding how an array is stored in memory.</span></span> <span data-ttu-id="4c8f3-244">ストレージは、プラットフォームのデータ幅が異なると変わります。したがって、同じ配列でも、32 ビットのシステムよりも 64 ビットのシステムの方が多くのメモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-244">Storage varies on platforms of different data widths, so the same array can consume more memory on a 64-bit system than on a 32-bit system.</span></span> <span data-ttu-id="4c8f3-245">配列を初期化すると、システム構成に応じて、要素をできるだけ近くに集めるように、またはすべてがハードウェア自体の境界に合致するように、共通言語ランタイム (CLR: Common Language Runtime) によってストレージが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-245">Depending on system configuration when you initialize an array, the common language runtime (CLR) can assign storage either to pack elements as close together as possible, or to align them all on natural hardware boundaries.</span></span> <span data-ttu-id="4c8f3-246">また、配列は制御情報のためにストレージのオーバーヘッドを必要とします。このオーバーヘッドは、次元が追加されるごとに増加します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-246">Also, an array requires a storage overhead for its control information, and this overhead increases with each added dimension.</span></span>|  
  
##  <span data-ttu-id="4c8f3-247"><a name="BKMK_ArrayTypes"></a> 配列の型および他の型</span><span class="sxs-lookup"><span data-stu-id="4c8f3-247"><a name="BKMK_ArrayTypes"></a> Array Types and Other Types</span></span>  
 <span data-ttu-id="4c8f3-248">すべての配列にデータ型がありますが、要素のデータ型とは異なります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-248">Every array has a data type, but it differs from the data type of its elements.</span></span> <span data-ttu-id="4c8f3-249">すべての配列を包括する 1 つのデータ型はありません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-249">There is no single data type for all arrays.</span></span> <span data-ttu-id="4c8f3-250">代わりに、配列のデータ型は、配列の次元数 ( *ランク*) と配列の要素のデータ型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-250">Instead, the data type of an array is determined by the number of dimensions, or *rank*, of the array, and the data type of the elements in the array.</span></span> <span data-ttu-id="4c8f3-251">ランクと要素のデータ型が一致しない限り、2 つの配列変数が同じデータ型を持つと見なされることはありません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-251">Two array variables are considered to be of the same data type only when they have the same rank and their elements have the same data type.</span></span> <span data-ttu-id="4c8f3-252">配列の各次元の長さは、配列のデータ型には影響しません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-252">The lengths of the dimensions in an array do not influence the array data type.</span></span>  
  
 <span data-ttu-id="4c8f3-253">すべての配列は、<xref:System.Array?displayProperty=nameWithType> クラスから継承しています。また、`Array` 型として変数を宣言できますが、`Array` 型の配列は作成できません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-253">Every array inherits from the <xref:System.Array?displayProperty=nameWithType> class, and you can declare a variable to be of type `Array`, but you cannot create an array of type `Array`.</span></span> <span data-ttu-id="4c8f3-254">また、[ReDim ステートメント](../../../../visual-basic/language-reference/statements/redim-statement.md) は、`Array` 型として宣言された変数上では使用できません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-254">Also, the [ReDim Statement](../../../../visual-basic/language-reference/statements/redim-statement.md) cannot operate on a variable declared as type `Array`.</span></span> <span data-ttu-id="4c8f3-255">これらの理由やタイプ セーフを考慮して、すべての配列を、前の例の `Integer` などの特定の型として宣言することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-255">For these reasons, and for type safety, it is advisable to declare every array as a specific type, such as `Integer` in the preceding example.</span></span>  
  
 <span data-ttu-id="4c8f3-256">いくつかの方法で、配列またはその要素のいずれかのデータ型を知ることができます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-256">You can find out the data type of either an array or its elements in several ways.</span></span>  
  
-   <span data-ttu-id="4c8f3-257">変数の <xref:System.Object.GetType%2A?displayProperty=nameWithType> メソッドを呼び出して、実行時型の変数の <xref:System.Type> オブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-257">You can call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on the variable to receive a <xref:System.Type> object for the run-time type of the variable.</span></span> <span data-ttu-id="4c8f3-258"><xref:System.Type> オブジェクトでは、プロパティおよびメソッドに詳細情報が保持されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-258">The <xref:System.Type> object holds extensive information in its properties and methods.</span></span>  
  
-   <span data-ttu-id="4c8f3-259">変数を <xref:Microsoft.VisualBasic.Information.TypeName%2A> 関数に渡して、実行時型の名前が含まれる `String` を取得できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-259">You can pass the variable to the <xref:Microsoft.VisualBasic.Information.TypeName%2A> function to receive a `String` containing the name of run-time type.</span></span>  
  
-   <span data-ttu-id="4c8f3-260">変数を <xref:Microsoft.VisualBasic.Information.VarType%2A> 関数に渡して、変数の型の分類を表す `VariantType` 値を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-260">You can pass the variable to the <xref:Microsoft.VisualBasic.Information.VarType%2A> function to receive a `VariantType` value representing the type classification of the variable.</span></span>  
  
 <span data-ttu-id="4c8f3-261">`TypeName` 関数を呼び出して配列の型と配列の要素の型を確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-261">The following example calls the `TypeName` function to determine the type of the array and the type of the elements in the array.</span></span> <span data-ttu-id="4c8f3-262">配列の型は `Integer(,)` で、配列の要素の型は `Integer`です。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-262">The array type is `Integer(,)` and the elements in the array are of type `Integer`.</span></span>  
  
 [!code-vb[VbVbalrArrays#15](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#15)]  
  
##  <span data-ttu-id="4c8f3-263"><a name="BKMK_Collections"></a> 配列の代わりとしてのコレクション</span><span class="sxs-lookup"><span data-stu-id="4c8f3-263"><a name="BKMK_Collections"></a> Collections as an Alternative to Arrays</span></span>  
 <span data-ttu-id="4c8f3-264">配列は、数が固定されている厳密に型指定されたオブジェクトの作成および処理に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-264">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="4c8f3-265">コレクションは、オブジェクトのグループをより柔軟に処理できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-265">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="4c8f3-266">配列の場合とは違って、コレクションで扱うオブジェクトのグループは、アプリケーションのニーズの変化に応じて動的に拡大および縮小できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-266">Unlike arrays, the group of objects that you work with can grow and shrink dynamically as the needs of the application change.</span></span>  
  
 <span data-ttu-id="4c8f3-267">配列のサイズを変更する必要がある場合は、[ReDim ステートメント](../../../../visual-basic/language-reference/statements/redim-statement.md)を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-267">If you need to change the size of an array, you must use the [ReDim Statement](../../../../visual-basic/language-reference/statements/redim-statement.md).</span></span> <span data-ttu-id="4c8f3-268">これを行うと、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] により新しい配列が作成され、前の配列が解放されて廃棄されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-268">When you do this, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] creates a new array and releases the previous array for disposal.</span></span> <span data-ttu-id="4c8f3-269">これには、実行時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-269">This takes execution time.</span></span> <span data-ttu-id="4c8f3-270">したがって、操作を行う項目の数が頻繁に変更される場合、または必要な項目の最大数を予測できない場合、コレクションを使用するとパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-270">Therefore, if the number of items you are working with changes frequently, or you cannot predict the maximum number of items you need, you might obtain better performance using a collection.</span></span>  
  
 <span data-ttu-id="4c8f3-271">コレクションによっては、コレクションに含まれるオブジェクトのキーを割り当てると、そのキーを使用してオブジェクトを迅速に取り出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-271">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="4c8f3-272">含まれる要素が 1 つのデータ型だけのコレクションの場合は、 <xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間のクラスのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-272">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4c8f3-273">ジェネリック コレクションでは、タイプ セーフが強制されるため、他のデータ型を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-273">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="4c8f3-274">ジェネリック コレクションから要素を取得する場合は、データ型を判断したり、変換したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-274">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
 <span data-ttu-id="4c8f3-275">コレクションの詳細については、「[コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-275">For more information about collections, see [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).</span></span>  
  
### <a name="example"></a><span data-ttu-id="4c8f3-276">例</span><span class="sxs-lookup"><span data-stu-id="4c8f3-276">Example</span></span>  
 <span data-ttu-id="4c8f3-277">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のジェネリック クラス <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> を使用して、`Customer` オブジェクトの一覧コレクションを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-277">The following example uses the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] generic class <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> to create a list collection of `Customer` objects.</span></span>  
  
 [!code-vb[VbVbalrArrays#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#1)]  
  
 <span data-ttu-id="4c8f3-278">`CustomerFile` コレクションの宣言により、 `Customer`型だけの要素を含むことができることを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-278">The declaration of the `CustomerFile` collection specifies that it can contain elements only of type `Customer`.</span></span> <span data-ttu-id="4c8f3-279">また、200 要素分の初期容量も用意されています。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-279">It also provides for an initial capacity of 200 elements.</span></span> <span data-ttu-id="4c8f3-280">`AddNewCustomer` プロシージャにより、新しい要素の有効性がチェックされ、コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-280">The procedure `AddNewCustomer` checks the new element for validity and then adds it to the collection.</span></span> <span data-ttu-id="4c8f3-281">`PrintCustomers` プロシージャでは、コレクションを走査し、その要素を表示するために、 `For Each` ループが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-281">The procedure `PrintCustomers` uses a `For Each` loop to traverse the collection and display its elements.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="4c8f3-282">関連トピック</span><span class="sxs-lookup"><span data-stu-id="4c8f3-282">Related Topics</span></span>  
  
|<span data-ttu-id="4c8f3-283">用語</span><span class="sxs-lookup"><span data-stu-id="4c8f3-283">Term</span></span>|<span data-ttu-id="4c8f3-284">定義</span><span class="sxs-lookup"><span data-stu-id="4c8f3-284">Definition</span></span>|  
|----------|----------------|  
|[<span data-ttu-id="4c8f3-285">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c8f3-285">Array Dimensions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|<span data-ttu-id="4c8f3-286">配列のランクと次元について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-286">Explains rank and dimensions in arrays.</span></span>|  
|[<span data-ttu-id="4c8f3-287">方法: Visual Basic で配列変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="4c8f3-287">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|<span data-ttu-id="4c8f3-288">配列に初期値を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-288">Describes how to populate arrays with initial values.</span></span>|  
|[<span data-ttu-id="4c8f3-289">方法: 配列を並べ替える (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c8f3-289">How to: Sort An Array in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|<span data-ttu-id="4c8f3-290">配列の要素をアルファベット順に並べ替える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-290">Shows how to sort the elements of an array alphabetically.</span></span>|  
|[<span data-ttu-id="4c8f3-291">方法 : 配列を別の配列に代入する</span><span class="sxs-lookup"><span data-stu-id="4c8f3-291">How to: Assign One Array to Another Array</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|<span data-ttu-id="4c8f3-292">配列を別の配列変数に代入するときの手順と規則を説明します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-292">Describes the rules and steps for assigning an array to another array variable.</span></span>|  
|[<span data-ttu-id="4c8f3-293">配列のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="4c8f3-293">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|<span data-ttu-id="4c8f3-294">配列を使用しているときに発生する一般的な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c8f3-294">Discusses some common problems that arise when working with arrays.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c8f3-295">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c8f3-295">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="4c8f3-296">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="4c8f3-296">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="4c8f3-297">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="4c8f3-297">ReDim Statement</span></span>](../../../../visual-basic/language-reference/statements/redim-statement.md)
