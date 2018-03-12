---
title: "?: 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bbd434e02ece4843bab4ffded6877f81f622950c
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b2720-102">?: 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b2720-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="b2720-103">一般に三項条件演算子として知られる、条件演算子 (`?:`) では、ブール式の値に応じて 2 つの値のいずれかが返されます。</span><span class="sxs-lookup"><span data-stu-id="b2720-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="b2720-104">条件演算子の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b2720-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="b2720-105">コメント</span><span class="sxs-lookup"><span data-stu-id="b2720-105">Remarks</span></span>  
 <span data-ttu-id="b2720-106">`condition` は、`true` または `false` に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2720-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="b2720-107">`condition` が `true` の場合、`first_expression` が評価され、これが結果となります。</span><span class="sxs-lookup"><span data-stu-id="b2720-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="b2720-108">`condition` が `false` の場合、`second_expression` が評価され、これが結果となります。</span><span class="sxs-lookup"><span data-stu-id="b2720-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="b2720-109">2 つの式のどちらか一方だけが評価されます。</span><span class="sxs-lookup"><span data-stu-id="b2720-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="b2720-110">`first_expression` の型と `second_expression` の型とは、同じ型であるか、または一方の型から他方の型への暗黙の型変換が存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2720-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="b2720-111">`if-else` の構築が必要となる場面で条件演算子を使用すると、計算をより簡潔に表現できます。</span><span class="sxs-lookup"><span data-stu-id="b2720-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="b2720-112">たとえば、次のコードは、まず `if` ステートメントを使用し、次に条件演算子を使用して、整数を正または負に分類します。</span><span class="sxs-lookup"><span data-stu-id="b2720-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 <span data-ttu-id="b2720-113">条件演算子の結合規則は右から左になります。</span><span class="sxs-lookup"><span data-stu-id="b2720-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="b2720-114">`a ? b : c ? d : e` という式は、`a ? b : (c ? d : e)` ではなく、`(a ? b : c) ? d : e` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="b2720-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="b2720-115">条件演算子は、オーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="b2720-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2720-116">例</span><span class="sxs-lookup"><span data-stu-id="b2720-116">Example</span></span>  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b2720-117">参照</span><span class="sxs-lookup"><span data-stu-id="b2720-117">See Also</span></span>  
 [<span data-ttu-id="b2720-118">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="b2720-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b2720-119">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b2720-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b2720-120">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="b2720-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="b2720-121">if-else</span><span class="sxs-lookup"><span data-stu-id="b2720-121">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
 [<span data-ttu-id="b2720-122">?. 演算子と ? 演算子</span><span class="sxs-lookup"><span data-stu-id="b2720-122">?. and ?Operators</span></span>](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [<span data-ttu-id="b2720-123">??演算子</span><span class="sxs-lookup"><span data-stu-id="b2720-123">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)
