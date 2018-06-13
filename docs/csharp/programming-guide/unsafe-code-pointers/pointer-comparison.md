---
title: ポインター比較 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: af264cd1572faafe25ee170b35cbeb48ed0fb2aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337705"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="ade93-102">ポインター比較 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ade93-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="ade93-103">次の演算子を適用して、任意の型のポインターを比較できます。</span><span class="sxs-lookup"><span data-stu-id="ade93-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="ade93-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="ade93-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="ade93-105">比較演算子は、2 つのオペランドのアドレスを符号なし整数のように比較します。</span><span class="sxs-lookup"><span data-stu-id="ade93-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ade93-106">例</span><span class="sxs-lookup"><span data-stu-id="ade93-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="ade93-107">出力例</span><span class="sxs-lookup"><span data-stu-id="ade93-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="ade93-108">参照</span><span class="sxs-lookup"><span data-stu-id="ade93-108">See Also</span></span>  
 [<span data-ttu-id="ade93-109">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ade93-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ade93-110">ポインター式</span><span class="sxs-lookup"><span data-stu-id="ade93-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="ade93-111">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="ade93-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="ade93-112">ポインターの操作</span><span class="sxs-lookup"><span data-stu-id="ade93-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="ade93-113">ポインター型</span><span class="sxs-lookup"><span data-stu-id="ade93-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="ade93-114">型</span><span class="sxs-lookup"><span data-stu-id="ade93-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="ade93-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="ade93-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="ade93-116">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="ade93-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="ade93-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="ade93-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
