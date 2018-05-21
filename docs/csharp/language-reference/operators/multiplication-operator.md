---
title: '* 演算子 (C# リファレンス)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 6c5d4de587b67e5ade158c163a87e8dea6bece5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9a16f-102">\* 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9a16f-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="9a16f-103">乗算演算子 (`*`) は、そのオペランドの積を計算します。</span><span class="sxs-lookup"><span data-stu-id="9a16f-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="9a16f-104">すべての数値型には定義済みの乗算演算子があります。</span><span class="sxs-lookup"><span data-stu-id="9a16f-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="9a16f-105">また、`*` はポインターへの読み書きを可能にする逆参照演算子としても機能します。</span><span class="sxs-lookup"><span data-stu-id="9a16f-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="9a16f-106">コメント</span><span class="sxs-lookup"><span data-stu-id="9a16f-106">Remarks</span></span>  
 <span data-ttu-id="9a16f-107">`*` 演算子は、ポインターの種類の宣言、およびポインターの逆参照にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a16f-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="9a16f-108">この演算子は、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードの使用によって示され、[/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを必要とする、unsafe コンテキストでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a16f-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="9a16f-109">逆参照演算子は、間接演算子とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9a16f-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="9a16f-110">ユーザー定義型は二項 `*` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="9a16f-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="9a16f-111">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="9a16f-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a16f-112">例</span><span class="sxs-lookup"><span data-stu-id="9a16f-112">Example</span></span>  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="9a16f-113">例</span><span class="sxs-lookup"><span data-stu-id="9a16f-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9a16f-114">参照</span><span class="sxs-lookup"><span data-stu-id="9a16f-114">See Also</span></span>  
 [<span data-ttu-id="9a16f-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="9a16f-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9a16f-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9a16f-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9a16f-117">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="9a16f-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="9a16f-118">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="9a16f-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
