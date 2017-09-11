---
title: "#<a name=\"define-c-reference\"></a>define (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#define'
dev_langs:
- CSharp
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: 22
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
ms.openlocfilehash: 8ace15f79480c9aeb0fcb4c7d46c207d4904cef0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="define-c-reference"></a><span data-ttu-id="867dd-102">#define (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="867dd-102">#define (C# Reference)</span></span>
<span data-ttu-id="867dd-103">`#define` は、シンボルを定義するために使用します。</span><span class="sxs-lookup"><span data-stu-id="867dd-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="867dd-104">次の例に示すように、定義したシンボルを式として [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ディレクティブに渡すと、式は `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="867dd-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
  
 <span data-ttu-id="867dd-105">`#`  `define`   `DEBUG`</span><span class="sxs-lookup"><span data-stu-id="867dd-105">`#`  `define`   `DEBUG`</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="867dd-106">コメント</span><span class="sxs-lookup"><span data-stu-id="867dd-106">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="867dd-107">`#define` ディレクティブを使用して、通常 C および C++ で行うように定数値を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="867dd-107">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="867dd-108">C# の定数は、クラスまたは構造体の静的メンバーとして定義することができます。</span><span class="sxs-lookup"><span data-stu-id="867dd-108">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="867dd-109">そのような定数がいくつかある場合は、それを保持するための "Constants" クラスを個別に作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="867dd-109">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="867dd-110">シンボルを使用して、コンパイル条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="867dd-110">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="867dd-111">シンボルは、[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) または [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) で評価できます。</span><span class="sxs-lookup"><span data-stu-id="867dd-111">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="867dd-112">また、`conditional` 属性を使用して、条件付きコンパイルを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="867dd-112">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="867dd-113">シンボルを定義することはできますが、シンボルに値は代入できません。</span><span class="sxs-lookup"><span data-stu-id="867dd-113">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="867dd-114">`#define` ディレクティブは、ファイル内で、プリプロセッサ ディレクティブではない他の命令よりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="867dd-114">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="867dd-115">また、シンボルは [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) コンパイラ オプションでも定義できます。</span><span class="sxs-lookup"><span data-stu-id="867dd-115">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="867dd-116">[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) を使うと、シンボルを未定義状態にできます。</span><span class="sxs-lookup"><span data-stu-id="867dd-116">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="867dd-117">`/define` または `#define` で定義されたシンボルは、同じ名前の変数とは競合しません。</span><span class="sxs-lookup"><span data-stu-id="867dd-117">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="867dd-118">変数名をプリプロセッサ ディレクティブに渡すことはできません。シンボルはプリプロセッサ ディレクティブだけで評価されます。</span><span class="sxs-lookup"><span data-stu-id="867dd-118">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="867dd-119">`#define` で定義されたシンボルのスコープは、そのシンボルが定義されたファイル内だけです。</span><span class="sxs-lookup"><span data-stu-id="867dd-119">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="867dd-120">次の例に示すように、`#define` ディレクティブは、ファイルの先頭で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="867dd-120">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 <span data-ttu-id="867dd-121">シンボルの定義を解除する方法の例については、「[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="867dd-121">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="867dd-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="867dd-122">See Also</span></span>  
 <span data-ttu-id="867dd-123">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="867dd-123">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="867dd-124">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="867dd-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="867dd-125">[C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md) </span><span class="sxs-lookup"><span data-stu-id="867dd-125">[C# Preprocessor Directives](../../../csharp/language-reference/preprocessor-directives/index.md) </span></span>  
 <span data-ttu-id="867dd-126">[const](../../../csharp/language-reference/keywords/const.md) </span><span class="sxs-lookup"><span data-stu-id="867dd-126">[const](../../../csharp/language-reference/keywords/const.md) </span></span>  
 <span data-ttu-id="867dd-127">[方法 : トレースとデバッグを指定して条件付きコンパイルを実行する](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) </span><span class="sxs-lookup"><span data-stu-id="867dd-127">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) </span></span>  
 <span data-ttu-id="867dd-128">[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) </span><span class="sxs-lookup"><span data-stu-id="867dd-128">[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) </span></span>  
 [<span data-ttu-id="867dd-129">#if</span><span class="sxs-lookup"><span data-stu-id="867dd-129">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)

