---
title: = 演算子 (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c7188abe54cb69678720b4dbbf4dbdea1be4abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1cce9-102">= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1cce9-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="1cce9-103">代入演算子 (`=`) では、右辺のオペランドの値が、左辺のオペランドで示された格納場所、プロパティ、またはインデクサーに格納され、その値が結果として返されます。</span><span class="sxs-lookup"><span data-stu-id="1cce9-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="1cce9-104">両側のオペランドは、同じ型である必要があります (または、右辺のオペランドが、左辺のオペランドの型に暗黙に変換できる必要があります)。</span><span class="sxs-lookup"><span data-stu-id="1cce9-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cce9-105">コメント</span><span class="sxs-lookup"><span data-stu-id="1cce9-105">Remarks</span></span>  
 <span data-ttu-id="1cce9-106">代入演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="1cce9-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="1cce9-107">ただし、暗黙の変換演算子を型に定義すると、その型で代入演算子を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1cce9-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="1cce9-108">詳細については、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cce9-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cce9-109">例</span><span class="sxs-lookup"><span data-stu-id="1cce9-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1cce9-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cce9-110">See Also</span></span>  
 [<span data-ttu-id="1cce9-111">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="1cce9-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1cce9-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1cce9-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1cce9-113">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="1cce9-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
