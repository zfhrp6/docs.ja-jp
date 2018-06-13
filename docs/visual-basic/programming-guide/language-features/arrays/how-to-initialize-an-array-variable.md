---
title: '方法: Visual Basic で配列変数を初期化する'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: ee8cb91fd2fae9637a0d0e33fca63a4cdb9d2fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651571"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="52ded-102">方法: Visual Basic で配列変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="52ded-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="52ded-103">配列リテラルを `New` 句に含めること、および配列の初期値を指定することで、配列変数を初期化します。</span><span class="sxs-lookup"><span data-stu-id="52ded-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="52ded-104">型を指定するか、配列リテラル内の値から推論することを許可できます。</span><span class="sxs-lookup"><span data-stu-id="52ded-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="52ded-105">型を推論する方法の詳細についてを参照してください「を設定する、配列に初期値」[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="52ded-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="52ded-106">配列リテラルを使用して配列変数を初期化するには</span><span class="sxs-lookup"><span data-stu-id="52ded-106">To initialize an array variable by using an array literal</span></span>  
  
-   <span data-ttu-id="52ded-107">`New` 句で、または配列値を割り当てるときに、中かっこ (`{}`) の中に要素の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="52ded-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="52ded-108">変数を宣言、作成、および初期化して `Char` 型の要素を持つ配列を含めるいくつかの方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="52ded-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     <span data-ttu-id="52ded-109">各ステートメントを実行すると、長さが 3 の配列が作成され、インデックス 0 からインデックス 2 の各要素に初期値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="52ded-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="52ded-110">上限および値の両方を指定した場合、インデックス 0 から上限までの、すべての要素の値を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="52ded-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="52ded-111">配列リテラルで要素の値を指定した場合は、インデックスの上限を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="52ded-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="52ded-112">上限が指定されていない場合、配列リテラル内の値の数に基づいて配列のサイズが推論されます。</span><span class="sxs-lookup"><span data-stu-id="52ded-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="52ded-113">配列リテラルを使用して多次元配列変数を初期化するには</span><span class="sxs-lookup"><span data-stu-id="52ded-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
-   <span data-ttu-id="52ded-114">中かっこ (`{}`) で囲んだ値を入れ子にして中かっこの中に含めます。</span><span class="sxs-lookup"><span data-stu-id="52ded-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="52ded-115">入れ子になったすべての配列リテラルが、型と長さが同じ配列として推論されるようにします。</span><span class="sxs-lookup"><span data-stu-id="52ded-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="52ded-116">多次元配列を初期化するいくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="52ded-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   <span data-ttu-id="52ded-117">配列の範囲は明示的に指定することも省略することもできます。省略した場合、配列リテラル内の値に基づいてコンパイラによって配列の範囲が推論されます。</span><span class="sxs-lookup"><span data-stu-id="52ded-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="52ded-118">上限と値の両方を指定する場合は、すべての次元について、インデックス 0 ～上限までの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52ded-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="52ded-119">変数を宣言、作成、および初期化して `Short` 型の要素を持つ 2 次元配列を含めるいくつかの方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="52ded-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     <span data-ttu-id="52ded-120">各ステートメントを実行すると、初期化された 6 つの要素 (インデックスは `(0,0)`、`(0,1)`、`(0,2)`、`(1,0)`、`(1,1)`、および `(1,2)`) が格納された配列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="52ded-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="52ded-121">配列のそれぞれの位置には値 `10` が格納されます。</span><span class="sxs-lookup"><span data-stu-id="52ded-121">Each array location contains the value `10`.</span></span>  
  
-   <span data-ttu-id="52ded-122">次の例では、多次元配列を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="52ded-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="52ded-123">Visual Basic で記述された Windows コンソール アプリケーションでは、コードを `Sub Main()` メソッド内に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="52ded-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="52ded-124">最終コメントは出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="52ded-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="52ded-125">配列リテラルを使用してジャグ配列変数を初期化するには</span><span class="sxs-lookup"><span data-stu-id="52ded-125">To initialize a jagged array variable by using array literals</span></span>  
  
-   <span data-ttu-id="52ded-126">中かっこ (`{}`) で囲んだオブジェクトの値を入れ子にします。</span><span class="sxs-lookup"><span data-stu-id="52ded-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="52ded-127">ジャグ配列の場合、長さが異なる配列を指定する配列リテラルを入れ子にすることもできますが、入れ子になった配列リテラルがかっこ (`()`) で囲まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="52ded-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="52ded-128">かっこで囲むことで、入れ子になった配列リテラルが強制的に評価され、結果の配列がジャグ配列の初期値として使用されるようになります。</span><span class="sxs-lookup"><span data-stu-id="52ded-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="52ded-129">ジャグ配列を初期化する 2 つの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="52ded-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   <span data-ttu-id="52ded-130">次の例では、ジャグ配列を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="52ded-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="52ded-131">Visual Basic で記述された Windows コンソール アプリケーションでは、コードを `Sub Main()` メソッド内に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="52ded-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="52ded-132">コードの最終コメントは出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="52ded-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="52ded-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="52ded-133">See Also</span></span>  
 [<span data-ttu-id="52ded-134">配列</span><span class="sxs-lookup"><span data-stu-id="52ded-134">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="52ded-135">配列のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="52ded-135">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
