---
title: "?: 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 794ff53fe471ef23163503f59599b528df127e2e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="43dfb-102">?: 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="43dfb-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="43dfb-103">条件演算子 (`?:`) では、ブール式の値に応じて 2 つの値のいずれかが返されます。</span><span class="sxs-lookup"><span data-stu-id="43dfb-103">The conditional operator (`?:`) returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="43dfb-104">条件演算子の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="43dfb-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="43dfb-105">コメント</span><span class="sxs-lookup"><span data-stu-id="43dfb-105">Remarks</span></span>  
 <span data-ttu-id="43dfb-106">`condition` は、`true` または `false` に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="43dfb-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="43dfb-107">`condition` が `true` の場合、`first_expression` が評価され、これが結果となります。</span><span class="sxs-lookup"><span data-stu-id="43dfb-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="43dfb-108">`condition` が `false` の場合、`second_expression` が評価され、これが結果となります。</span><span class="sxs-lookup"><span data-stu-id="43dfb-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="43dfb-109">2 つの式のどちらか一方だけが評価されます。</span><span class="sxs-lookup"><span data-stu-id="43dfb-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="43dfb-110">`first_expression` の型と `second_expression` の型とは、同じ型であるか、または一方の型から他方の型への暗黙の型変換が存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="43dfb-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="43dfb-111">`if-else` の構築が必要となる場面で条件演算子を使用すると、計算をより簡潔に表現できます。</span><span class="sxs-lookup"><span data-stu-id="43dfb-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="43dfb-112">たとえば、次のコードは、まず `if` ステートメントを使用し、次に条件演算子を使用して、整数を正または負に分類します。</span><span class="sxs-lookup"><span data-stu-id="43dfb-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```  
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
  
 <span data-ttu-id="43dfb-113">条件演算子の結合規則は右から左になります。</span><span class="sxs-lookup"><span data-stu-id="43dfb-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="43dfb-114">`a ? b : c ? d : e` という式は、`a ? b : (c ? d : e)` ではなく、`(a ? b : c) ? d : e` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="43dfb-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="43dfb-115">条件演算子は、オーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="43dfb-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43dfb-116">例</span><span class="sxs-lookup"><span data-stu-id="43dfb-116">Example</span></span>  
 <span data-ttu-id="43dfb-117">[!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="43dfb-117">[!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43dfb-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="43dfb-118">See Also</span></span>  
 <span data-ttu-id="43dfb-119">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="43dfb-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="43dfb-120">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="43dfb-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="43dfb-121">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="43dfb-121">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="43dfb-122">[if-else](../../../csharp/language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="43dfb-122">[if-else](../../../csharp/language-reference/keywords/if-else.md) </span></span>  
 <span data-ttu-id="43dfb-123">[?. 演算子と ? 演算子](../../../csharp/language-reference/operators/null-conditional-operators.md) </span><span class="sxs-lookup"><span data-stu-id="43dfb-123">[?. and ?Operators](../../../csharp/language-reference/operators/null-conditional-operators.md) </span></span>  
 [<span data-ttu-id="43dfb-124">??演算子</span><span class="sxs-lookup"><span data-stu-id="43dfb-124">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)

