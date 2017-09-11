---
title: "方法 : ポインターを使用して配列要素にアクセスする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
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
ms.openlocfilehash: 73f14aba63b7f7677a889f18cc1b410e3ecf1438
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="87b26-102">方法 : ポインターを使用して配列要素にアクセスする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="87b26-102">How to: Access an Array Element with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="87b26-103">安全ではないコンテキストでは、次の例のように、ポインターを利用してメモリ内の要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="87b26-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 <span data-ttu-id="87b26-104">角かっこ内の式は `int`、`uint`、`long`、`ulong` に暗黙的に変換できるものでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="87b26-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="87b26-105">演算 p[e] は *(p+e) と等しくなります。</span><span class="sxs-lookup"><span data-stu-id="87b26-105">The operation p[e] is equivalent to *(p+e).</span></span> <span data-ttu-id="87b26-106">C や C++ と同様に、ポインターで要素にアクセスする行為では、範囲外のエラーがチェックされません。</span><span class="sxs-lookup"><span data-stu-id="87b26-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87b26-107">例</span><span class="sxs-lookup"><span data-stu-id="87b26-107">Example</span></span>  
 <span data-ttu-id="87b26-108">この例では、123 のメモリ場所が文字配列 `charPointer` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="87b26-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="87b26-109">この配列を利用し、2 つの [for](../../../csharp/language-reference/keywords/for.md) ループの小文字と大文字が表示されます。</span><span class="sxs-lookup"><span data-stu-id="87b26-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>  
  
 <span data-ttu-id="87b26-110">式 `charPointer[i]` は式 `*(charPointer + i)` と等しく、2 つの式のいずれを利用しても同じ結果が得られることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="87b26-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 <span data-ttu-id="87b26-111">[!code-cs[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="87b26-111">[!code-cs[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]</span></span>  
  
 <span data-ttu-id="87b26-112">[!code-cs[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="87b26-112">[!code-cs[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]</span></span>  
  
 <span data-ttu-id="87b26-113">**大文字:**</span><span class="sxs-lookup"><span data-stu-id="87b26-113">**Uppercase letters:**</span></span>  
<span data-ttu-id="87b26-114">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="87b26-114">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span></span>  
<span data-ttu-id="87b26-115">**小文字:**</span><span class="sxs-lookup"><span data-stu-id="87b26-115">**Lowercase letters:**</span></span>  
<span data-ttu-id="87b26-116">**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="87b26-116">**abcdefghijklmnopqrstuvwxyz**</span></span>   
## <a name="see-also"></a><span data-ttu-id="87b26-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="87b26-117">See Also</span></span>  
 <span data-ttu-id="87b26-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="87b26-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="87b26-119">[ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="87b26-119">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="87b26-120">[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="87b26-120">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="87b26-121">[型](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="87b26-121">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="87b26-122">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="87b26-122">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="87b26-123">[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="87b26-123">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="87b26-124">stackalloc</span><span class="sxs-lookup"><span data-stu-id="87b26-124">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

