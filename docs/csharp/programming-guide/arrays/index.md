---
title: "配列 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: 33
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1035caae15b64d1311305cfe4c1f1a74c80ed19a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="4a8c5-102">配列 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4a8c5-102">Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="4a8c5-103">配列データ構造体には、同じ型の複数の変数を格納できます。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="4a8c5-104">配列は、要素の型を指定することで宣言します。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="4a8c5-105">次の例では、1 次元配列、多次元配列、およびジャグ配列を作成しています。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-105">The following examples create single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 <span data-ttu-id="4a8c5-106">[!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a8c5-106">[!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]</span></span>  
  
## <a name="array-overview"></a><span data-ttu-id="4a8c5-107">配列の概要</span><span class="sxs-lookup"><span data-stu-id="4a8c5-107">Array Overview</span></span>  
 <span data-ttu-id="4a8c5-108">配列には、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-108">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="4a8c5-109">配列は、[1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)、[多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)、または[ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-109">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="4a8c5-110">次元数と各次元の長さは、配列インスタンスの作成時に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-110">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="4a8c5-111">インスタンスの有効期間中にこれらの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-111">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="4a8c5-112">数値配列要素の既定値はゼロに設定され、参照要素は null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-112">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="4a8c5-113">ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-113">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="4a8c5-114">配列には、ゼロから始まるインデックスが付けられます。`n` 個の要素を含む配列には、`0` から `n-1` までのインデックスが付けられます。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-114">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="4a8c5-115">配列の要素および配列型は、どのような型でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-115">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="4a8c5-116">配列型は、抽象基本型 <xref:System.Array> から派生した[参照型](../../../csharp/language-reference/keywords/reference-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-116">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="4a8c5-117">この型は <xref:System.Collections.IEnumerable> と <xref:System.Collections.Generic.IEnumerable%601> を実装するので、C# のすべての配列で [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 反復処理を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4a8c5-117">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4a8c5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a8c5-118">Related Sections</span></span>  
  
-   [<span data-ttu-id="4a8c5-119">オブジェクトとしての配列</span><span class="sxs-lookup"><span data-stu-id="4a8c5-119">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="4a8c5-120">配列での foreach の使用</span><span class="sxs-lookup"><span data-stu-id="4a8c5-120">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="4a8c5-121">引数としての配列の受け渡し</span><span class="sxs-lookup"><span data-stu-id="4a8c5-121">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [<span data-ttu-id="4a8c5-122">ref と out を使用した配列の引き渡し</span><span class="sxs-lookup"><span data-stu-id="4a8c5-122">Passing Arrays Using ref and out</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a><span data-ttu-id="4a8c5-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="4a8c5-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4a8c5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a8c5-124">See Also</span></span>  
 <span data-ttu-id="4a8c5-125">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4a8c5-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4a8c5-126">[コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span><span class="sxs-lookup"><span data-stu-id="4a8c5-126">[Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span></span>  
 [<span data-ttu-id="4a8c5-127">Array コレクション型</span><span class="sxs-lookup"><span data-stu-id="4a8c5-127">Array Collection Type</span></span>](http://msdn.microsoft.com/en-us/8a9964de-8941-47b1-a3cf-a01bc88db9e8)

