---
title: '!= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b69d0b12734e690f0ba0209ccbbc7627ff92fe8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2c1ca-102">!= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2c1ca-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="2c1ca-103">非等値演算子 (`!=`) は、そのオペランドが等しい場合には false を返し、それ以外の場合は true を返します。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="2c1ca-104">非等値演算子は、文字列とオブジェクトを含むすべての型に対して事前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="2c1ca-105">ユーザー定義型は `!=` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c1ca-106">コメント</span><span class="sxs-lookup"><span data-stu-id="2c1ca-106">Remarks</span></span>  
 <span data-ttu-id="2c1ca-107">組み込みの値型の場合、非等値演算子 (`!=`) ではオペランドの値が異なる場合に true が返され、それ以外の場合は false が返されます。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="2c1ca-108">`string` 以外の参照型の場合、`!=` では 2 つのオペランドが異なるオブジェクトを参照する場合に true が返されます。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="2c1ca-109">`string` 型の場合は、`!=` は文字列の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="2c1ca-110">ユーザー定義の値の型は `!=` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="2c1ca-111">ユーザー定義参照型もオーバーロードはできますが、既定では、組み込み参照型とユーザー定義参照型のいずれに対しても `!=` は前述のとおりに機能します。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="2c1ca-112">`!=` をオーバーロードする場合は、[==](../../../csharp/language-reference/operators/equality-comparison-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="2c1ca-113">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c1ca-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c1ca-114">例</span><span class="sxs-lookup"><span data-stu-id="2c1ca-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2c1ca-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c1ca-115">See Also</span></span>  
 [<span data-ttu-id="2c1ca-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="2c1ca-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2c1ca-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2c1ca-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2c1ca-118">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="2c1ca-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
