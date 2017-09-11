---
title: "-- 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
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
ms.openlocfilehash: 100e68f3b07164b0cfb398a32f47137f2726943f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="---operator-c-reference"></a><span data-ttu-id="95fd0-102">-- 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="95fd0-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="95fd0-103">デクリメント演算子 (`--`) は、オペランドを 1 ずつデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="95fd0-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="95fd0-104">デクリメント演算子はそのオペランド ( `--variable` および `variable--`) の前後に指定できます。</span><span class="sxs-lookup"><span data-stu-id="95fd0-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="95fd0-105">1 番目の形式は前置デクリメント演算です。</span><span class="sxs-lookup"><span data-stu-id="95fd0-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="95fd0-106">この演算の結果は、デクリメント "後" のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="95fd0-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="95fd0-107">2 番目の形式は後置デクリメント演算です。</span><span class="sxs-lookup"><span data-stu-id="95fd0-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="95fd0-108">この演算の結果は、デクリメント "前" のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="95fd0-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95fd0-109">コメント</span><span class="sxs-lookup"><span data-stu-id="95fd0-109">Remarks</span></span>  
 <span data-ttu-id="95fd0-110">数値型と列挙型には事前定義のデクリメント演算子があります。</span><span class="sxs-lookup"><span data-stu-id="95fd0-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="95fd0-111">ユーザー定義型は `--` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="95fd0-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="95fd0-112">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="95fd0-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95fd0-113">例</span><span class="sxs-lookup"><span data-stu-id="95fd0-113">Example</span></span>  
 <span data-ttu-id="95fd0-114">[!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="95fd0-114">[!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fd0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="95fd0-115">See Also</span></span>  
 <span data-ttu-id="95fd0-116">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="95fd0-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="95fd0-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="95fd0-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="95fd0-118">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="95fd0-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

