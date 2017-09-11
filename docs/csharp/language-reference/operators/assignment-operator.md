---
title: "= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
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
ms.openlocfilehash: e40b2f221717461443a5d0247b3401eb527a7b5a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="a5033-102">= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a5033-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="a5033-103">代入演算子 (`=`) では、右辺のオペランドの値が、左辺のオペランドで示された格納場所、プロパティ、またはインデクサーに格納され、その値が結果として返されます。</span><span class="sxs-lookup"><span data-stu-id="a5033-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="a5033-104">両側のオペランドは、同じ型である必要があります (または、右辺のオペランドが、左辺のオペランドの型に暗黙に変換できる必要があります)。</span><span class="sxs-lookup"><span data-stu-id="a5033-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5033-105">コメント</span><span class="sxs-lookup"><span data-stu-id="a5033-105">Remarks</span></span>  
 <span data-ttu-id="a5033-106">代入演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="a5033-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="a5033-107">ただし、暗黙の変換演算子を型に定義すると、その型で代入演算子を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a5033-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="a5033-108">詳しくは、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a5033-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5033-109">例</span><span class="sxs-lookup"><span data-stu-id="a5033-109">Example</span></span>  
 <span data-ttu-id="a5033-110">[!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a5033-110">[!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5033-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5033-111">See Also</span></span>  
 <span data-ttu-id="a5033-112">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="a5033-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="a5033-113">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a5033-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="a5033-114">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="a5033-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

