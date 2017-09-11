---
title: "!= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '!=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: 14
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
ms.openlocfilehash: 49c5c9668c6b1169220ee4fa0babf167292a9813
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="309ba-102">!= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="309ba-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="309ba-103">非等値演算子 (`!=`) は、そのオペランドが等しい場合には false を返し、それ以外の場合は true を返します。</span><span class="sxs-lookup"><span data-stu-id="309ba-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="309ba-104">非等値演算子は、文字列とオブジェクトを含むすべての型に対して事前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="309ba-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="309ba-105">ユーザー定義型は `!=` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="309ba-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="309ba-106">コメント</span><span class="sxs-lookup"><span data-stu-id="309ba-106">Remarks</span></span>  
 <span data-ttu-id="309ba-107">組み込みの値型の場合、非等値演算子 (`!=`) ではオペランドの値が異なる場合に true が返され、それ以外の場合は false が返されます。</span><span class="sxs-lookup"><span data-stu-id="309ba-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="309ba-108">`string` 以外の参照型の場合、`!=` では 2 つのオペランドが異なるオブジェクトを参照する場合に true が返されます。</span><span class="sxs-lookup"><span data-stu-id="309ba-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="309ba-109">`string` 型の場合は、`!=` は文字列の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="309ba-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="309ba-110">ユーザー定義の値の型は `!=` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="309ba-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="309ba-111">ユーザー定義参照型もオーバーロードはできますが、既定では、組み込み参照型とユーザー定義参照型のいずれに対しても `!=` は前述のとおりに機能します。</span><span class="sxs-lookup"><span data-stu-id="309ba-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="309ba-112">`!=` をオーバーロードする場合は、[==](../../../csharp/language-reference/operators/equality-comparison-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="309ba-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="309ba-113">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="309ba-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="309ba-114">例</span><span class="sxs-lookup"><span data-stu-id="309ba-114">Example</span></span>  
 <span data-ttu-id="309ba-115">[!code-cs[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="309ba-115">[!code-cs[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309ba-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="309ba-116">See Also</span></span>  
 <span data-ttu-id="309ba-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="309ba-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="309ba-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="309ba-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="309ba-119">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="309ba-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

