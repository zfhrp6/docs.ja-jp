---
title: "方法 : ポインターを使用してメンバーにアクセスする (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 622d9910b09c9197b7f4ccd5e54e2675fbbbbccb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="047eb-102">方法 : ポインターを使用してメンバーにアクセスする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="047eb-102">How to: Access a Member with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="047eb-103">安全ではないコンテキストで宣言されている構造体のメンバーにアクセスするには、次の例のように、メンバー アクセス演算子を利用できます。`p` は、メンバー `x` を含む[構造体](../../../csharp/language-reference/keywords/struct.md)を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="047eb-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="047eb-104">例</span><span class="sxs-lookup"><span data-stu-id="047eb-104">Example</span></span>  
 <span data-ttu-id="047eb-105">この例では、2 つの座標 (`x` と `y`) を含む[構造体](../../../csharp/language-reference/keywords/struct.md) `CoOrds` が宣言され、インスタンス化されています。</span><span class="sxs-lookup"><span data-stu-id="047eb-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="047eb-106">メンバー アクセス演算子 `->` とインスタンス `home` を指すポインターを使用することで、`x` と `y` に値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="047eb-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="047eb-107">式 `p->x` は式 `(*p).x` と等しく、2 つの式のいずれを利用しても同じ結果が得られることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="047eb-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="047eb-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="047eb-108">See Also</span></span>  
 [<span data-ttu-id="047eb-109">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="047eb-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="047eb-110">ポインター式</span><span class="sxs-lookup"><span data-stu-id="047eb-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="047eb-111">ポインター型</span><span class="sxs-lookup"><span data-stu-id="047eb-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="047eb-112">型</span><span class="sxs-lookup"><span data-stu-id="047eb-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="047eb-113">unsafe</span><span class="sxs-lookup"><span data-stu-id="047eb-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="047eb-114">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="047eb-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="047eb-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="047eb-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
