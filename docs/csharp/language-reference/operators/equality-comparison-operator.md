---
title: == 演算子 (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca22846325968519a1f7625461867c0d83a1a9f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cc4aa-102">== 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="cc4aa-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="cc4aa-103">組み込みの値型の場合、等値演算子 (`==`) ではオペランドの値が等しい場合に true が返され、それ以外の場合は `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="cc4aa-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="cc4aa-104">[string](../../../csharp/language-reference/keywords/string.md) 以外の参照型の場合、`==` では 2 つのオペランドが同じオブジェクトを参照する場合に `true` が返されます。</span><span class="sxs-lookup"><span data-stu-id="cc4aa-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="cc4aa-105">`string` 型の場合は、`==` は文字列の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="cc4aa-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc4aa-106">コメント</span><span class="sxs-lookup"><span data-stu-id="cc4aa-106">Remarks</span></span>  
 <span data-ttu-id="cc4aa-107">ユーザー定義の値の型は `==` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="cc4aa-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="cc4aa-108">ユーザー定義参照型もオーバーロードはできますが、既定では、組み込み参照型とユーザー定義参照型のいずれに対しても `==` は前述のとおりに機能します。</span><span class="sxs-lookup"><span data-stu-id="cc4aa-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="cc4aa-109">`==` をオーバーロードする場合は、[!=](../../../csharp/language-reference/operators/not-equal-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc4aa-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="cc4aa-110">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc4aa-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc4aa-111">例</span><span class="sxs-lookup"><span data-stu-id="cc4aa-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cc4aa-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc4aa-112">See Also</span></span>  
 [<span data-ttu-id="cc4aa-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="cc4aa-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cc4aa-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cc4aa-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cc4aa-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="cc4aa-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
