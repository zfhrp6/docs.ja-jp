---
title: '方法 : ポインターを使用して配列要素にアクセスする (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 92eb7a79c0e7522d1474537aeefbfdb083a11dc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332040"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="28418-102">方法 : ポインターを使用して配列要素にアクセスする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="28418-102">How to: Access an Array Element with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="28418-103">安全ではないコンテキストでは、次の例のように、ポインターを利用してメモリ内の要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="28418-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 <span data-ttu-id="28418-104">角かっこ内の式は `int`、`uint`、`long`、`ulong` に暗黙的に変換できるものでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="28418-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="28418-105">演算 p[e] は \*(p+e) と等しくなります。</span><span class="sxs-lookup"><span data-stu-id="28418-105">The operation p[e] is equivalent to \*(p+e).</span></span> <span data-ttu-id="28418-106">C や C++ と同様に、ポインターで要素にアクセスする行為では、範囲外のエラーがチェックされません。</span><span class="sxs-lookup"><span data-stu-id="28418-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28418-107">例</span><span class="sxs-lookup"><span data-stu-id="28418-107">Example</span></span>  
 <span data-ttu-id="28418-108">この例では、123 のメモリ場所が文字配列 `charPointer` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="28418-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="28418-109">この配列を利用し、2 つの [for](../../../csharp/language-reference/keywords/for.md) ループの小文字と大文字が表示されます。</span><span class="sxs-lookup"><span data-stu-id="28418-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>  
  
 <span data-ttu-id="28418-110">式 `charPointer[i]` は式 `*(charPointer + i)` と等しく、2 つの式のいずれを利用しても同じ結果が得られることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="28418-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 <span data-ttu-id="28418-111">**大文字:**</span><span class="sxs-lookup"><span data-stu-id="28418-111">**Uppercase letters:**</span></span>  
<span data-ttu-id="28418-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="28418-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span></span>  
<span data-ttu-id="28418-113">**小文字:**</span><span class="sxs-lookup"><span data-stu-id="28418-113">**Lowercase letters:**</span></span>  
<span data-ttu-id="28418-114">**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="28418-114">**abcdefghijklmnopqrstuvwxyz**</span></span>   
## <a name="see-also"></a><span data-ttu-id="28418-115">参照</span><span class="sxs-lookup"><span data-stu-id="28418-115">See Also</span></span>  
 [<span data-ttu-id="28418-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="28418-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="28418-117">ポインター式</span><span class="sxs-lookup"><span data-stu-id="28418-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="28418-118">ポインター型</span><span class="sxs-lookup"><span data-stu-id="28418-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="28418-119">型</span><span class="sxs-lookup"><span data-stu-id="28418-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="28418-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="28418-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="28418-121">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="28418-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="28418-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="28418-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
