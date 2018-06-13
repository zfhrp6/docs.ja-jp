---
title: ReDim ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 9536ea8a6274e0b4a2589caf5aefa271a3567d32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605395"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="f7a57-102">ReDim ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7a57-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="f7a57-103">配列変数の記憶域を再割り当てします。</span><span class="sxs-lookup"><span data-stu-id="f7a57-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a57-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7a57-104">Syntax</span></span>  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="f7a57-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="f7a57-105">Parts</span></span>  
  
|<span data-ttu-id="f7a57-106">用語</span><span class="sxs-lookup"><span data-stu-id="f7a57-106">Term</span></span>|<span data-ttu-id="f7a57-107">定義</span><span class="sxs-lookup"><span data-stu-id="f7a57-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="f7a57-108">任意。</span><span class="sxs-lookup"><span data-stu-id="f7a57-108">Optional.</span></span> <span data-ttu-id="f7a57-109">最後の次元のサイズだけを変更したときに、既存の配列のデータを保持するために使用する修飾子</span><span class="sxs-lookup"><span data-stu-id="f7a57-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="f7a57-110">必須。</span><span class="sxs-lookup"><span data-stu-id="f7a57-110">Required.</span></span> <span data-ttu-id="f7a57-111">配列変数名。</span><span class="sxs-lookup"><span data-stu-id="f7a57-111">Name of the array variable.</span></span> <span data-ttu-id="f7a57-112">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7a57-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="f7a57-113">必須。</span><span class="sxs-lookup"><span data-stu-id="f7a57-113">Required.</span></span> <span data-ttu-id="f7a57-114">再定義された配列の各次元の境界を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="f7a57-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7a57-115">コメント</span><span class="sxs-lookup"><span data-stu-id="f7a57-115">Remarks</span></span>  
 <span data-ttu-id="f7a57-116">`ReDim` ステートメントを使用し、既に宣言されている配列の 1 つまたは複数の次元のサイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="f7a57-117">大きな配列があり、その要素の一部が必要ない場合、`ReDim` で配列のサイズを減らし、メモリを解放できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="f7a57-118">一方で、配列に要素を追加する必要がある場合、`ReDim` は要素を追加できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="f7a57-119">`ReDim` ステートメントは配列のみを対象としています。</span><span class="sxs-lookup"><span data-stu-id="f7a57-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="f7a57-120">スカラー (単一の値のみが含まれる変数)、コレクション、構造体では有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="f7a57-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="f7a57-121">`Array` 型の変数を宣言する場合、`ReDim` ステートメントには新しい配列を作成するために十分な型情報が与えられません。</span><span class="sxs-lookup"><span data-stu-id="f7a57-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="f7a57-122">`ReDim` はプロシージャ レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="f7a57-123">そのため、変数の宣言コンテキストはプロシージャにする必要があります。ソース ファイル、名前空間、インターフェイス、クラス、構造体、モジュール、ブロックにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f7a57-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="f7a57-124">詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7a57-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f7a57-125">ルール</span><span class="sxs-lookup"><span data-stu-id="f7a57-125">Rules</span></span>  
  
-   <span data-ttu-id="f7a57-126">**複数の変数。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-126">**Multiple Variables.**</span></span> <span data-ttu-id="f7a57-127">同じ宣言ステートメントで複数の配列変数のサイズを変更し、各変数の `name` 部分と `boundlist` 部分を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="f7a57-128">複数の変数を指定するときは、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="f7a57-128">Multiple variables are separated by commas.</span></span>  
  
-   <span data-ttu-id="f7a57-129">**配列の境界。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-129">**Array Bounds.**</span></span> <span data-ttu-id="f7a57-130">`boundlist` の各エントリでその次元の上限と下限を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="f7a57-131">下限は常に 0 (ゼロ) です。</span><span class="sxs-lookup"><span data-stu-id="f7a57-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="f7a57-132">上限は次元の長さ (上限に 1 を足したもの) ではなく、その次元で可能な最大インデックス値です。</span><span class="sxs-lookup"><span data-stu-id="f7a57-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="f7a57-133">各次元のインデックスは 0 ～ 上限値の範囲で変わります。</span><span class="sxs-lookup"><span data-stu-id="f7a57-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="f7a57-134">`boundlist` の次元数は配列の次元の元の数 (r順位) に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7a57-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
-   <span data-ttu-id="f7a57-135">**データ型。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-135">**Data Types.**</span></span> <span data-ttu-id="f7a57-136">`ReDim` ステートメントでは、配列変数またはその要素のデータ型を変更できません。</span><span class="sxs-lookup"><span data-stu-id="f7a57-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
-   <span data-ttu-id="f7a57-137">**初期化します。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-137">**Initialization.**</span></span> <span data-ttu-id="f7a57-138">`ReDim` ステートメントは配列要素の新しい初期化値を提供できません。</span><span class="sxs-lookup"><span data-stu-id="f7a57-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
-   <span data-ttu-id="f7a57-139">**ランク付けします。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-139">**Rank.**</span></span> <span data-ttu-id="f7a57-140">`ReDim` ステートメントは配列の順位 (次元数) を変更できません。</span><span class="sxs-lookup"><span data-stu-id="f7a57-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
-   <span data-ttu-id="f7a57-141">**サイズ変更と保持します。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="f7a57-142">`Preserve` を使用する場合、配列の最後の次元だけのサイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="f7a57-143">他のすべての次元については、既存の配列の境界を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7a57-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="f7a57-144">たとえば、配列に次元が 1 つだけある場合、その次元のサイズを変更し、配列のすべてのコンテンツを保持できます。最後で唯一の次元を変更するためです。</span><span class="sxs-lookup"><span data-stu-id="f7a57-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="f7a57-145">ただし、配列に次元が 2 つ以上あるときは、`Preserve` を使用する場合、最後の次元だけのサイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
-   <span data-ttu-id="f7a57-146">**プロパティ。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-146">**Properties.**</span></span> <span data-ttu-id="f7a57-147">値の配列を保持するプロパティで `ReDim` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="f7a57-148">動作</span><span class="sxs-lookup"><span data-stu-id="f7a57-148">Behavior</span></span>  
  
-   <span data-ttu-id="f7a57-149">**配列置換。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-149">**Array Replacement.**</span></span> <span data-ttu-id="f7a57-150">`ReDim` 既存の配列を解放し、同じランクを持つ新しい配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="f7a57-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="f7a57-151">新しい配列は配列変数で解放された配列に取って代わります。</span><span class="sxs-lookup"><span data-stu-id="f7a57-151">The new array replaces the released array in the array variable.</span></span>  
  
-   <span data-ttu-id="f7a57-152">**保持しない初期化。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="f7a57-153">`Preserve` を指定しない場合、`ReDim` はそのデータ型の既定値を使用し、新しい配列の要素を初期化します。</span><span class="sxs-lookup"><span data-stu-id="f7a57-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
-   <span data-ttu-id="f7a57-154">**保持する初期化します。**</span><span class="sxs-lookup"><span data-stu-id="f7a57-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="f7a57-155">`Preserve` を指定する場合、Visual Basic は既存の配列から新しい配列に要素をコピーします。</span><span class="sxs-lookup"><span data-stu-id="f7a57-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7a57-156">例</span><span class="sxs-lookup"><span data-stu-id="f7a57-156">Example</span></span>  
 <span data-ttu-id="f7a57-157">次の例では、配列の既存データを失うことなく動的配列の最後の次元のサイズを増やし、その後、一部のデータを損失しサイズを減らします。</span><span class="sxs-lookup"><span data-stu-id="f7a57-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="f7a57-158">最後に、サイズを減らして元の値に戻し、すべての配列要素を再初期化します。</span><span class="sxs-lookup"><span data-stu-id="f7a57-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 <span data-ttu-id="f7a57-159">`Dim` ステートメントは次の 3 つの次元を持つ新しい配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="f7a57-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="f7a57-160">各次元は 10 の境界で宣言されます。そのため、各次元の配列インデックスの範囲は 0 ～ 10 になります。</span><span class="sxs-lookup"><span data-stu-id="f7a57-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="f7a57-161">次の説明では、3 つの次元が「層」、「行」、「列」になります。</span><span class="sxs-lookup"><span data-stu-id="f7a57-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="f7a57-162">最初の `ReDim` は、変数 `intArray` の既存の配列を置換する新しい配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="f7a57-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="f7a57-163">`ReDim` は既存の配列から新しい配列にすべての要素をコピーします。</span><span class="sxs-lookup"><span data-stu-id="f7a57-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="f7a57-164">また、さらに 10 個の列を各層の各行の終わりに追加し、これらの列の要素を 0 (配列の要素型である `Integer` の初期値) に初期化します。</span><span class="sxs-lookup"><span data-stu-id="f7a57-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="f7a57-165">2 番目の `ReDim` は新しい配列をもう 1 つ作成し、適合するすべての要素をコピーします。</span><span class="sxs-lookup"><span data-stu-id="f7a57-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="f7a57-166">ただし、5 つの列がすべての層のすべての行の終わりから失われます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="f7a57-167">これらの列を使用して完了した場合、これは問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="f7a57-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="f7a57-168">大きな配列のサイズを減らし、不要になったメモリを解放できます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="f7a57-169">3 番目の `ReDim` は新しい配列をもう 1 つ作成し、すべての層のすべての行の終わりから別の 5 つの列を削除します。</span><span class="sxs-lookup"><span data-stu-id="f7a57-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="f7a57-170">このとき、既存の要素はコピーされません。</span><span class="sxs-lookup"><span data-stu-id="f7a57-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="f7a57-171">このステートメントは配列を元のサイズに戻します。</span><span class="sxs-lookup"><span data-stu-id="f7a57-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="f7a57-172">ステートメントに `Preserve` 修飾子が含まれないため、すべての配列要素が元の初期値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f7a57-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="f7a57-173">その他の例では、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7a57-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a57-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7a57-174">See Also</span></span>  
 <xref:System.IndexOutOfRangeException>  
 [<span data-ttu-id="f7a57-175">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="f7a57-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="f7a57-176">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="f7a57-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="f7a57-177">Erase ステートメント</span><span class="sxs-lookup"><span data-stu-id="f7a57-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [<span data-ttu-id="f7a57-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="f7a57-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="f7a57-179">配列</span><span class="sxs-lookup"><span data-stu-id="f7a57-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
