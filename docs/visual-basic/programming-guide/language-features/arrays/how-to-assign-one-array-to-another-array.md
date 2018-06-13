---
title: '方法: 配列を別の配列に代入する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647931"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="a2e3c-102">方法: 配列を別の配列に代入する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2e3c-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>
<span data-ttu-id="a2e3c-103">配列がオブジェクトであるため、他のオブジェクト型のような代入ステートメントで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="a2e3c-104">配列変数、配列要素と、ランクと長さの情報を構成するデータへのポインターを保持し、割り当ては、このポインターだけをコピーします。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>  
  
### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="a2e3c-105">別の配列に 1 つの配列を割り当てる</span><span class="sxs-lookup"><span data-stu-id="a2e3c-105">To assign one array to another array</span></span>  
  
1.  <span data-ttu-id="a2e3c-106">2 つの配列に同じランク (次元数) と互換性のある要素のデータ型があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>  
  
2.  <span data-ttu-id="a2e3c-107">標準の代入ステートメントを使用して、コピー先の配列を元の配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="a2e3c-108">かっこ付きのいずれかの配列名は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-108">Do not follow either array name with parentheses.</span></span>  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 <span data-ttu-id="a2e3c-109">1 つの配列を別に代入すると、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-109">When you assign one array to another, the following rules apply:</span></span>  
  
-   <span data-ttu-id="a2e3c-110">**ランクが等しい。**</span><span class="sxs-lookup"><span data-stu-id="a2e3c-110">**Equal Ranks.**</span></span> <span data-ttu-id="a2e3c-111">コピー先の配列のランク (次元数) は、元の配列と同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>  
  
     <span data-ttu-id="a2e3c-112">2 つの配列のランクが等しい、提供されたディメンションは同等である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="a2e3c-113">指定した次元にある要素の数を割り当て中に変更できます。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-113">The number of elements in a given dimension can change during assignment.</span></span>  
  
-   <span data-ttu-id="a2e3c-114">**要素の型。**</span><span class="sxs-lookup"><span data-stu-id="a2e3c-114">**Element Types.**</span></span> <span data-ttu-id="a2e3c-115">両方のいずれかの配列にいる必要があります*型参照*要素または両方の配列にいる必要があります*値の型*要素。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="a2e3c-116">詳細については、次を参照してください。[値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
    -   <span data-ttu-id="a2e3c-117">両方の配列には、値型の要素がある、要素のデータ型があります正確に同じです。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="a2e3c-118">唯一の例外は、の配列を割り当てることができます`Enum`の基本型の配列に要素`Enum`です。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>  
  
    -   <span data-ttu-id="a2e3c-119">両方の配列には、参照型の要素がある、ソース要素の型が変換先の要素の型から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="a2e3c-120">そうでは、ときに、その要素として同じ継承関係がある 2 つの配列。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="a2e3c-121">これと呼ばれる*配列の共変性*です。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-121">This is called *array covariance*.</span></span>  
  
 <span data-ttu-id="a2e3c-122">コンパイラは、エラー場合は、上記の規則に違反している、たとえば、データ型は互換性がない場合や、ランクが等しくないことを報告します。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="a2e3c-123">割り当てを試行する前に、配列に互換性があるかどうかを確認するコードにエラー処理を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="a2e3c-124">使用することも、 [TryCast 演算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)例外がスローされないようにする場合は、キーワード。</span><span class="sxs-lookup"><span data-stu-id="a2e3c-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e3c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2e3c-125">See Also</span></span>  
 [<span data-ttu-id="a2e3c-126">配列</span><span class="sxs-lookup"><span data-stu-id="a2e3c-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="a2e3c-127">配列のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a2e3c-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="a2e3c-128">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="a2e3c-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="a2e3c-129">配列変換</span><span class="sxs-lookup"><span data-stu-id="a2e3c-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
