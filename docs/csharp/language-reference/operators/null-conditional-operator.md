---
title: ?? 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8fa751654acaf5939fb8f8068c7323e365f7bdab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f519f-103">??</span><span class="sxs-lookup"><span data-stu-id="f519f-103">??</span></span> <span data-ttu-id="f519f-104">演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f519f-104">Operator (C# Reference)</span></span>
<span data-ttu-id="f519f-105">`??` 演算子は、null 合体演算子と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f519f-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="f519f-106">左側のオペランドが null 値でない場合には左側のオペランドを返し、null 値である場合には右側のオペランドを返します。</span><span class="sxs-lookup"><span data-stu-id="f519f-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f519f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f519f-107">Remarks</span></span>  
 <span data-ttu-id="f519f-108">null 許容型は、型のドメインの値を表すことができ、値は未定義でもかまいません (その場合、値は null になります)。</span><span class="sxs-lookup"><span data-stu-id="f519f-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="f519f-109">`??` 演算子の構文を使用して、左側のオペランドが null 許容型でその値が null である場合に、適切な値 (右側のオペランド) を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="f519f-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="f519f-110">`??` 演算子を使用せずに、null 非許容値型に対して null 許容値型を割り当てると、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f519f-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="f519f-111">null 許容値型が定義されていない場合にキャストを使用すると、`InvalidOperationException` 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f519f-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="f519f-112">詳細については、「[Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f519f-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="f519f-113">?? の結果は、</span><span class="sxs-lookup"><span data-stu-id="f519f-113">The result of a ??</span></span> <span data-ttu-id="f519f-114">たとえ両方の引数が定数であった場合でも、定数とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="f519f-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f519f-115">例</span><span class="sxs-lookup"><span data-stu-id="f519f-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f519f-116">参照</span><span class="sxs-lookup"><span data-stu-id="f519f-116">See Also</span></span>  
 [<span data-ttu-id="f519f-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f519f-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f519f-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f519f-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f519f-119">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="f519f-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="f519f-120">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="f519f-120">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="f519f-121">'Lifted' の正確な意味</span><span class="sxs-lookup"><span data-stu-id="f519f-121">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
