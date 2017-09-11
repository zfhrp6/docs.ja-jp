---
title: "* 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
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
ms.openlocfilehash: 165ca8f797eb8d03ae1dec8c0ec5e1f4b31cb050
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="10d09-102">* 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="10d09-102">* Operator (C# Reference)</span></span>
<span data-ttu-id="10d09-103">そのオペランドの積を計算する乗算演算子 (`*`)。</span><span class="sxs-lookup"><span data-stu-id="10d09-103">The multiplication operator (`*`), which computes the product of its operands.</span></span>  <span data-ttu-id="10d09-104">また、ポインターへの読み書きを可能にする逆参照演算子。</span><span class="sxs-lookup"><span data-stu-id="10d09-104">Also, the dereference operator, which allows reading and writing to a pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10d09-105">コメント</span><span class="sxs-lookup"><span data-stu-id="10d09-105">Remarks</span></span>  
 <span data-ttu-id="10d09-106">すべての数値型には定義済みの乗算演算子があります。</span><span class="sxs-lookup"><span data-stu-id="10d09-106">All numeric types have predefined multiplication operators.</span></span>  
  
 <span data-ttu-id="10d09-107">`*` 演算子は、ポインターの種類の宣言、およびポインターの逆参照にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="10d09-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="10d09-108">この演算子は、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードの使用によって示され、[/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを必要とする、unsafe コンテキストでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="10d09-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="10d09-109">逆参照演算子は、間接演算子とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="10d09-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="10d09-110">ユーザー定義型は二項 `*` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="10d09-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="10d09-111">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="10d09-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10d09-112">例</span><span class="sxs-lookup"><span data-stu-id="10d09-112">Example</span></span>  
 <span data-ttu-id="10d09-113">[!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="10d09-113">[!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="10d09-114">例</span><span class="sxs-lookup"><span data-stu-id="10d09-114">Example</span></span>  
 <span data-ttu-id="10d09-115">[!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="10d09-115">[!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d09-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="10d09-116">See Also</span></span>  
 <span data-ttu-id="10d09-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="10d09-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="10d09-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="10d09-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="10d09-119">[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="10d09-119">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 [<span data-ttu-id="10d09-120">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="10d09-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

