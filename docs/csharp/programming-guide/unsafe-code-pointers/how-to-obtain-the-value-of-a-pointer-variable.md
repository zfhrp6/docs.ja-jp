---
title: "方法 : ポインター変数の値を取得する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
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
ms.openlocfilehash: 4cff42de07f2edb279ddd1cafefe9f4b67a38ce1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="99c5e-102">方法 : ポインター変数の値を取得する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="99c5e-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="99c5e-103">ポインターが指す位置にある変数を取得するには、ポインター間接演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="99c5e-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="99c5e-104">この式は次の形式になります。`p` はポインター型です。</span><span class="sxs-lookup"><span data-stu-id="99c5e-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="99c5e-105">ポインター型以外の型の式では、単項間接演算子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="99c5e-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="99c5e-106">また、[void](../../../csharp/language-reference/keywords/void.md) ポインターに適用することもできません。</span><span class="sxs-lookup"><span data-stu-id="99c5e-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="99c5e-107">間接演算子を [null](../../../csharp/language-reference/keywords/null.md) ポインターに適用すると、結果は実装によって異なります。</span><span class="sxs-lookup"><span data-stu-id="99c5e-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99c5e-108">例</span><span class="sxs-lookup"><span data-stu-id="99c5e-108">Example</span></span>  
 <span data-ttu-id="99c5e-109">次の例では、`char` 型の変数に、さまざまな型のポインターを使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="99c5e-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="99c5e-110">変数に割り当てられる物理アドレスが変更できるため、`theChar` のアドレスが実行ごとに異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="99c5e-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 <span data-ttu-id="99c5e-111">[!code-cs[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="99c5e-111">[!code-cs[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]</span></span>  
  
 <span data-ttu-id="99c5e-112">[!code-cs[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="99c5e-112">[!code-cs[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]</span></span>  
  
 <span data-ttu-id="99c5e-113">**theChar の値 = Z** </span><span class="sxs-lookup"><span data-stu-id="99c5e-113">**Value of theChar = Z** </span></span>  
<span data-ttu-id="99c5e-114">**theChar のアドレス = 12F718**</span><span class="sxs-lookup"><span data-stu-id="99c5e-114">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="99c5e-115">**pChar の値 = Z** </span><span class="sxs-lookup"><span data-stu-id="99c5e-115">**Value of pChar = Z** </span></span>  
<span data-ttu-id="99c5e-116">**pInt の値 = 90**</span><span class="sxs-lookup"><span data-stu-id="99c5e-116">**Value of pInt = 90**</span></span>    
## <a name="see-also"></a><span data-ttu-id="99c5e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="99c5e-117">See Also</span></span>  
 <span data-ttu-id="99c5e-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="99c5e-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="99c5e-119">[ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="99c5e-119">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="99c5e-120">[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="99c5e-120">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="99c5e-121">[型](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="99c5e-121">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="99c5e-122">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="99c5e-122">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="99c5e-123">[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="99c5e-123">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="99c5e-124">stackalloc</span><span class="sxs-lookup"><span data-stu-id="99c5e-124">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

