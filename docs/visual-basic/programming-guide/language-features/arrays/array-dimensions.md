---
title: Visual Basic における配列の次元
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: cf295288dd034d744dceb71b5c58278be5cc2a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651757"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="18caa-102">Visual Basic における配列の次元</span><span class="sxs-lookup"><span data-stu-id="18caa-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="18caa-103">A*ディメンション*は、方向、配列の要素の仕様を変更できます。</span><span class="sxs-lookup"><span data-stu-id="18caa-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="18caa-104">月の日付ごとの売上を合計を保持する配列には、1 つのディメンション (月の日) があります。</span><span class="sxs-lookup"><span data-stu-id="18caa-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="18caa-105">月の日付ごとに、売り上げ高を部門によって合計を保持する配列には、2 つのディメンション (部署番号と月の日) があります。</span><span class="sxs-lookup"><span data-stu-id="18caa-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="18caa-106">配列がディメンションの数が呼び出されますその*ランク*です。</span><span class="sxs-lookup"><span data-stu-id="18caa-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18caa-107">使用することができます、<xref:System.Array.Rank%2A>配列には、次元数を決定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="18caa-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="18caa-108">ディメンションの使用</span><span class="sxs-lookup"><span data-stu-id="18caa-108">Working with Dimensions</span></span>  
 <span data-ttu-id="18caa-109">指定することによって、配列の要素を指定する、*インデックス*または*添字*の各次元です。</span><span class="sxs-lookup"><span data-stu-id="18caa-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="18caa-110">要素は、各ディメンションに従ってそのディメンションの最も大きいインデックスをインデックス 0 から連続しています。</span><span class="sxs-lookup"><span data-stu-id="18caa-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="18caa-111">次の図は、異なるランクを持つ配列の概念の構造を表示します。</span><span class="sxs-lookup"><span data-stu-id="18caa-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="18caa-112">図内の各要素は、これにアクセスするインデックス値を示します。</span><span class="sxs-lookup"><span data-stu-id="18caa-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="18caa-113">たとえば、インデックスを指定することによって、2 次元配列の 2 番目の行の最初の要素をアクセス`(1, 0)`です。</span><span class="sxs-lookup"><span data-stu-id="18caa-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="18caa-114">![1 つのグラフィック ダイアグラム&#45;次元配列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="18caa-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="18caa-115">1 次元配列</span><span class="sxs-lookup"><span data-stu-id="18caa-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="18caa-116">![2 つのグラフィック ダイアグラム&#45;次元配列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="18caa-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="18caa-117">2 次元配列</span><span class="sxs-lookup"><span data-stu-id="18caa-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="18caa-118">![3 つのグラフィック ダイアグラム&#45;次元配列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="18caa-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="18caa-119">3 次元配列</span><span class="sxs-lookup"><span data-stu-id="18caa-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="18caa-120">1 つのディメンション</span><span class="sxs-lookup"><span data-stu-id="18caa-120">One Dimension</span></span>  
 <span data-ttu-id="18caa-121">多くのアレイは、各年齢のユーザーの数などの 1 つだけディメンションを持ちます。</span><span class="sxs-lookup"><span data-stu-id="18caa-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="18caa-122">要素を指定する唯一の要件は、その要素がカウントを保持する期間です。</span><span class="sxs-lookup"><span data-stu-id="18caa-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="18caa-123">そのため、このような配列は、1 つだけのインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="18caa-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="18caa-124">次の例を保持する変数の宣言、 *1 次元配列*年齢の年齢が 0 ~ 120 の数します。</span><span class="sxs-lookup"><span data-stu-id="18caa-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="18caa-125">2 つのディメンション</span><span class="sxs-lookup"><span data-stu-id="18caa-125">Two Dimensions</span></span>  
 <span data-ttu-id="18caa-126">一部の配列では、キャンパスの各建物のフロアごとのオフィスの数など、2 次元があります。</span><span class="sxs-lookup"><span data-stu-id="18caa-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="18caa-127">要素の仕様は、建物番号と、切り捨ての両方が必要ですし、各要素は、ビルとフロアの組み合わせの数を保持します。</span><span class="sxs-lookup"><span data-stu-id="18caa-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="18caa-128">したがって、このような配列には、2 つのインデックスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="18caa-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="18caa-129">次の例を保持する変数の宣言、 *2 次元配列*オフィスの数の 0 ~ 40 のビルとフロアが 0 ~ 5 です。</span><span class="sxs-lookup"><span data-stu-id="18caa-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="18caa-130">2 次元の配列とも呼ばれますが、*四角形配列*です。</span><span class="sxs-lookup"><span data-stu-id="18caa-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="18caa-131">3 つのディメンション</span><span class="sxs-lookup"><span data-stu-id="18caa-131">Three Dimensions</span></span>  
 <span data-ttu-id="18caa-132">いくつかの配列では、3 次元空間の値など、3 つの次元を持ちます。</span><span class="sxs-lookup"><span data-stu-id="18caa-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="18caa-133">このような配列では、ここでは、x、y、および物理領域の z 座標を表す 3 つのインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="18caa-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="18caa-134">次の例を保持する変数の宣言、 *3 次元配列*3 次元のボリューム内のさまざまな時点での気温します。</span><span class="sxs-lookup"><span data-stu-id="18caa-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="18caa-135">複数の 3 つのディメンション</span><span class="sxs-lookup"><span data-stu-id="18caa-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="18caa-136">配列には、最大 32 次元を持つことができます、ケースはまれ 3 以上です。</span><span class="sxs-lookup"><span data-stu-id="18caa-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18caa-137">配列にディメンションを追加するときに配列に必要な合計ストレージ増大は多次元配列を払ってください。</span><span class="sxs-lookup"><span data-stu-id="18caa-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="18caa-138">別のディメンションを使用します。</span><span class="sxs-lookup"><span data-stu-id="18caa-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="18caa-139">当月の日の売上を追跡したいとします。</span><span class="sxs-lookup"><span data-stu-id="18caa-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="18caa-140">次の例として、月の日付ごとに 1 つを示しています、31 の要素の 1 次元配列を宣言することがあります。</span><span class="sxs-lookup"><span data-stu-id="18caa-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="18caa-141">今すぐ毎日についてだけでなく、1 か月のすべての月、年のに対しても、同じ情報を追跡したいとします。</span><span class="sxs-lookup"><span data-stu-id="18caa-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="18caa-142">次の例のように 12 行 (月) と 31 列 (日)、2 次元配列を宣言することがあります。</span><span class="sxs-lookup"><span data-stu-id="18caa-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="18caa-143">ようになりましたことに決定したと仮定しますお使いの配列は 1 年間以上の情報を保持します。</span><span class="sxs-lookup"><span data-stu-id="18caa-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="18caa-144">5 年の売上額を追跡する場合は、次の例のように 5 層、12 の行と列を含む 31、3 次元の配列を宣言する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18caa-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="18caa-145">なお、各インデックスが 0、最大の各次元に異なりますので`salesAmounts`そのディメンションの 1 つ必要な長さより小さい値として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="18caa-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="18caa-146">配列のサイズは、新しい次元ごとに増加にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="18caa-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="18caa-147">前の例では、3 つのサイズは、それぞれ 31、372、および 1,860 要素です。</span><span class="sxs-lookup"><span data-stu-id="18caa-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18caa-148">使用せずに配列を作成することができます、`Dim`ステートメントまたは`New`句。</span><span class="sxs-lookup"><span data-stu-id="18caa-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="18caa-149">たとえばを呼び出すことができます、<xref:System.Array.CreateInstance%2A>メソッド、または別のコンポーネントをこのように作成された配列、コードを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="18caa-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="18caa-150">このような配列には、0 以外の下限を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="18caa-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="18caa-151">常にテストできます、次元の下限値を使用して、<xref:System.Array.GetLowerBound%2A>メソッドまたは`LBound`関数。</span><span class="sxs-lookup"><span data-stu-id="18caa-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18caa-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="18caa-152">See Also</span></span>  
 [<span data-ttu-id="18caa-153">配列</span><span class="sxs-lookup"><span data-stu-id="18caa-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="18caa-154">配列のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="18caa-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
