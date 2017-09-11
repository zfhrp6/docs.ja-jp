---
title: "方法 : ポインターを使用してメンバーにアクセスする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: 16
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
ms.openlocfilehash: ca24b7d930e7b6c61a3db89a431f1ec3aaec77c8
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="012b3-102">方法 : ポインターを使用してメンバーにアクセスする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="012b3-102">How to: Access a Member with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="012b3-103">安全ではないコンテキストで宣言されている構造体のメンバーにアクセスするには、次の例のように、メンバー アクセス演算子を利用できます。`p` は、メンバー `x` を含む[構造体](../../../csharp/language-reference/keywords/struct.md)を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="012b3-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="012b3-104">例</span><span class="sxs-lookup"><span data-stu-id="012b3-104">Example</span></span>  
 <span data-ttu-id="012b3-105">この例では、2 つの座標 (`x` と `y`) を含む[構造体](../../../csharp/language-reference/keywords/struct.md) `CoOrds` が宣言され、インスタンス化されています。</span><span class="sxs-lookup"><span data-stu-id="012b3-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="012b3-106">メンバー アクセス演算子 `->` とインスタンス `home` を指すポインターを使用することで、`x` と `y` に値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="012b3-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="012b3-107">式 `p->x` は式 `(*p).x` と等しく、2 つの式のいずれを利用しても同じ結果が得られることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="012b3-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 <span data-ttu-id="012b3-108">[!code-cs[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="012b3-108">[!code-cs[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]</span></span>  
  
 <span data-ttu-id="012b3-109">[!code-cs[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="012b3-109">[!code-cs[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="012b3-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="012b3-110">See Also</span></span>  
 <span data-ttu-id="012b3-111">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="012b3-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="012b3-112">[ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="012b3-112">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="012b3-113">[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="012b3-113">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="012b3-114">[型](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="012b3-114">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="012b3-115">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="012b3-115">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="012b3-116">[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="012b3-116">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="012b3-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="012b3-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

