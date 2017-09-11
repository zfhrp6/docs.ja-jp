---
title: "unsafe (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
dev_langs:
- CSharp
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
caps.latest.revision: 19
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
ms.openlocfilehash: ceba9e518caf6618cf2f457b930ce08f18273d8c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="unsafe-c-reference"></a><span data-ttu-id="ae018-102">unsafe (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ae018-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="ae018-103">`unsafe` キーワードは、ポインターに関連するすべての操作に必要な、unsafe コンテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="ae018-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="ae018-104">詳しくは、「[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ae018-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="ae018-105">`unsafe` 修飾子は、型またはメンバーの宣言で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ae018-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="ae018-106">そのため、型やメンバーの全体的なテキスト範囲が unsafe コンテキストと見なされます。</span><span class="sxs-lookup"><span data-stu-id="ae018-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="ae018-107">たとえば、次に示すのは、`unsafe` 修飾子を使用して宣言されたメソッドです。</span><span class="sxs-lookup"><span data-stu-id="ae018-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="ae018-108">unsafe コンテキストのスコープはパラメーター リストからメソッドの末尾までなので、ポインターはパラメーター リストでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ae018-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="ae018-109">また、unsafe ブロックを使用して、そのブロック内で unsafe コードを使用できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ae018-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="ae018-110">例:</span><span class="sxs-lookup"><span data-stu-id="ae018-110">For example:</span></span>  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="ae018-111">unsafe コードをコンパイルするには、 [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae018-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="ae018-112">unsafe コードは、共通言語ランタイムでは検証できません。</span><span class="sxs-lookup"><span data-stu-id="ae018-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae018-113">例</span><span class="sxs-lookup"><span data-stu-id="ae018-113">Example</span></span>  
 <span data-ttu-id="ae018-114">[!code-cs[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ae018-114">[!code-cs[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ae018-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ae018-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae018-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae018-116">See Also</span></span>  
 <span data-ttu-id="ae018-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ae018-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ae018-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ae018-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ae018-119">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ae018-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="ae018-120">[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ae018-120">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 <span data-ttu-id="ae018-121">[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="ae018-121">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 [<span data-ttu-id="ae018-122">固定サイズ バッファー</span><span class="sxs-lookup"><span data-stu-id="ae018-122">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

