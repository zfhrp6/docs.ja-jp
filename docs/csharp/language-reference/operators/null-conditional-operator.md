---
title: "?? 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ??_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: 17
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
ms.openlocfilehash: 86e50b97d7ded8adc74f031faf026b69ccdd0c87
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="9ce18-103">??</span><span class="sxs-lookup"><span data-stu-id="9ce18-103">??</span></span> <span data-ttu-id="9ce18-104">演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9ce18-104">Operator (C# Reference)</span></span>
<span data-ttu-id="9ce18-105">`??` 演算子は、null 合体演算子と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9ce18-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="9ce18-106">左側のオペランドが null 値でない場合には左側のオペランドを返し、null 値である場合には右側のオペランドを返します。</span><span class="sxs-lookup"><span data-stu-id="9ce18-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ce18-107">コメント</span><span class="sxs-lookup"><span data-stu-id="9ce18-107">Remarks</span></span>  
 <span data-ttu-id="9ce18-108">null 許容型は、型のドメインの値を表すことができ、値は未定義でもかまいません (その場合、値は null になります)。</span><span class="sxs-lookup"><span data-stu-id="9ce18-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="9ce18-109">`??` 演算子の構文を使用して、左側のオペランドが null 許容型でその値が null である場合に、適切な値 (右側のオペランド) を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="9ce18-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullible type whose value is null.</span></span> <span data-ttu-id="9ce18-110">`??` 演算子を使用せずに、null 非許容値型に対して null 許容値型を割り当てると、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9ce18-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="9ce18-111">null 許容値型が定義されていない場合にキャストを使用すると、`InvalidOperationException` 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9ce18-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="9ce18-112">詳細については、「[ull 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ce18-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="9ce18-113">?? の結果は、</span><span class="sxs-lookup"><span data-stu-id="9ce18-113">The result of a ??</span></span> <span data-ttu-id="9ce18-114">たとえ両方の引数が定数であった場合でも、定数とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="9ce18-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce18-115">例</span><span class="sxs-lookup"><span data-stu-id="9ce18-115">Example</span></span>  
 <span data-ttu-id="9ce18-116">[!code-cs[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9ce18-116">[!code-cs[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce18-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ce18-117">See Also</span></span>  
 <span data-ttu-id="9ce18-118">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9ce18-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9ce18-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9ce18-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9ce18-120">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="9ce18-120">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="9ce18-121">[Null 許容型](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="9ce18-121">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="9ce18-122">'Lifted' の正確な意味</span><span class="sxs-lookup"><span data-stu-id="9ce18-122">What Exactly Does 'Lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkID=112382)

