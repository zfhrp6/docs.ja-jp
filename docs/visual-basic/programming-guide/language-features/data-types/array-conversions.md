---
title: 配列の変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: a179b7cf5b82132db88fb5412f0ca4be207f0987
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="af099-102">配列の変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af099-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="af099-103">別の配列型、配列型を変換するには、次の条件を満たしていれば。</span><span class="sxs-lookup"><span data-stu-id="af099-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
-   <span data-ttu-id="af099-104">**ランクが等しい。**</span><span class="sxs-lookup"><span data-stu-id="af099-104">**Equal Rank.**</span></span> <span data-ttu-id="af099-105">2 つの配列のランクは同じである必要があります、つまり、同じ次元数がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="af099-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="af099-106">ただし、それぞれの次元の長さが同じにする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="af099-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
-   <span data-ttu-id="af099-107">**要素のデータ型。**</span><span class="sxs-lookup"><span data-stu-id="af099-107">**Element Data Type.**</span></span> <span data-ttu-id="af099-108">両方の配列の要素のデータ型は、参照型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="af099-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="af099-109">変換することはできません、`Integer`配列を`Long`配列、またはにも、`Object`に少なくとも 1 つの値の型が関係するための配列。</span><span class="sxs-lookup"><span data-stu-id="af099-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="af099-110">詳細については、次を参照してください。[値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="af099-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
-   <span data-ttu-id="af099-111">**変換可能性です。**</span><span class="sxs-lookup"><span data-stu-id="af099-111">**Convertibility.**</span></span> <span data-ttu-id="af099-112">変換、拡張または縮小は、2 つの配列の要素の型の間でできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="af099-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="af099-113">この要件に失敗した例は、の間で変換しようとする`String`配列とクラスの配列から派生した<xref:System.Attribute?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="af099-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="af099-114">これらの 2 種類 nothing に共通あり、それらの間に任意の種類の変換が存在しないです。</span><span class="sxs-lookup"><span data-stu-id="af099-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="af099-115">1 つの配列型の間の変換は、拡大または自動それぞれの要素の変換を拡大または縮小するかどうかに応じて縮小します。</span><span class="sxs-lookup"><span data-stu-id="af099-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="af099-116">詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af099-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="af099-117">オブジェクトの配列への変換</span><span class="sxs-lookup"><span data-stu-id="af099-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="af099-118">宣言する場合、`Object`初期化せず、要素の型の配列が`Object`それが初期化されていない限りです。</span><span class="sxs-lookup"><span data-stu-id="af099-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="af099-119">を特定のクラスの配列を設定するとそのクラスの型になります。</span><span class="sxs-lookup"><span data-stu-id="af099-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="af099-120">しかし、基になる型は`Object`、関連のないクラスの別の配列を後で設定できます。</span><span class="sxs-lookup"><span data-stu-id="af099-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="af099-121">すべてのクラスを派生させるため`Object`、任意のクラス、配列の要素の型を変更するには、他のクラスです。</span><span class="sxs-lookup"><span data-stu-id="af099-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="af099-122">次の例では、変換が存在しない型の間で`student`と`String`から派生して両方`Object`ので、すべての割り当てが無効です。</span><span class="sxs-lookup"><span data-stu-id="af099-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="af099-123">基になる、配列の型</span><span class="sxs-lookup"><span data-stu-id="af099-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="af099-124">特定のクラスを含む配列を宣言していた場合は、そのクラスは、基になる要素の種類です。</span><span class="sxs-lookup"><span data-stu-id="af099-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="af099-125">設定した場合、後で別のクラスの配列を 2 つのクラス間の変換が必要があります。</span><span class="sxs-lookup"><span data-stu-id="af099-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="af099-126">次の例では、`students`は、`student`配列。</span><span class="sxs-lookup"><span data-stu-id="af099-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="af099-127">間で変換が存在しないため`String`と`student`、最後のステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="af099-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="af099-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="af099-128">See Also</span></span>  
 [<span data-ttu-id="af099-129">データの種類</span><span class="sxs-lookup"><span data-stu-id="af099-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="af099-130">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="af099-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="af099-131">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="af099-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="af099-132">文字列とその他の型との変換</span><span class="sxs-lookup"><span data-stu-id="af099-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="af099-133">方法: オブジェクトを Visual Basic での別の型に変換</span><span class="sxs-lookup"><span data-stu-id="af099-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="af099-134">データの種類</span><span class="sxs-lookup"><span data-stu-id="af099-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="af099-135">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="af099-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="af099-136">配列</span><span class="sxs-lookup"><span data-stu-id="af099-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
