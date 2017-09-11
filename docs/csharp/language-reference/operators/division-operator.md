---
title: "/ 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
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
ms.openlocfilehash: 2972261996467f987fa457213b1bcb482d9f1519
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="8186c-102">/ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8186c-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="8186c-103">除算演算子 (`/`) は、1 つ目のオペランドを 2 つ目のオペランドで除算します。</span><span class="sxs-lookup"><span data-stu-id="8186c-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="8186c-104">すべての数値型には定義済みの除算演算子があります。</span><span class="sxs-lookup"><span data-stu-id="8186c-104">All numeric types have predefined division operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8186c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="8186c-105">Remarks</span></span>  
 <span data-ttu-id="8186c-106">ユーザー定義型は `/` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="8186c-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="8186c-107">`/` 演算子のオーバーロードは、[/= 演算子](division-assignment-operator.md)を暗黙的にオーバーロードします。</span><span class="sxs-lookup"><span data-stu-id="8186c-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="8186c-108">2 つの整数を除算した場合、結果は常に整数になります。</span><span class="sxs-lookup"><span data-stu-id="8186c-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="8186c-109">たとえば、7 / 3 の結果は 2 となります。</span><span class="sxs-lookup"><span data-stu-id="8186c-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="8186c-110">7 / 3 の余りを計算するには、剰余演算子 ([%](../../../csharp/language-reference/operators/modulus-operator.md)) を使用します。</span><span class="sxs-lookup"><span data-stu-id="8186c-110">To determine the remainder of 7 / 3, use the remainder operator ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span></span> <span data-ttu-id="8186c-111">商を有理数または分数として取得するには、被除数または除数の型を `float` または `double` にします。</span><span class="sxs-lookup"><span data-stu-id="8186c-111">To obtain a quotient as a rational number or fraction, give the dividend or divisor type `float` or type `double`.</span></span> <span data-ttu-id="8186c-112">除数または被除数を 10 進数として表現する場合は、次の例のように、小数点の右側に数字を配置することで、暗黙的に型を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="8186c-112">You can assign the type implicitly if you express the dividend or divisor as a decimal by putting a digit to the right side of the decimal point, as the following example shows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8186c-113">例</span><span class="sxs-lookup"><span data-stu-id="8186c-113">Example</span></span>  
 <span data-ttu-id="8186c-114">[!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8186c-114">[!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8186c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8186c-115">See Also</span></span>  
 <span data-ttu-id="8186c-116">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8186c-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8186c-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8186c-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="8186c-118">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="8186c-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

