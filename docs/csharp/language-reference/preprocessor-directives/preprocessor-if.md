---
title: "#<a name=\"if-c-reference\"></a>if (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#if'
dev_langs:
- CSharp
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
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
ms.openlocfilehash: f70dac98d5731370ae961f795b08a71946867d9b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="if-c-reference"></a><span data-ttu-id="10869-102">#if (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="10869-102">#if (C# Reference)</span></span>
<span data-ttu-id="10869-103">C# コンパイラでは、`#if` ディレクティブ、次いで [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) ディレクティブが検出されると、これらのディレクティブ間のコードがコンパイルされます (指定されたシンボルが定義されている場合に限る)。</span><span class="sxs-lookup"><span data-stu-id="10869-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) directive, it will compile the code between the directives only if the specified symbol is defined.</span></span>  <span data-ttu-id="10869-104">C や C++ とは異なり、シンボルに数値を代入することはできません。C# の #if ステートメントはブール値であり、シンボルが定義済みかどうかのテストのみを行います。</span><span class="sxs-lookup"><span data-stu-id="10869-104">Unlike C and C++, you cannot assign a numeric value to a symbol; the #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="10869-105">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="10869-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 <span data-ttu-id="10869-106">[==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (等しい) および [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (等しくない) の各演算子は、[true](../../../csharp/language-reference/keywords/true.md) か [false](../../../csharp/language-reference/keywords/false.md) のどちらであるかのテストにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="10869-106">You can use the operators [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (equality), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (inequality) only to test for [true](../../../csharp/language-reference/keywords/true.md) or [false](../../../csharp/language-reference/keywords/false.md) .</span></span> <span data-ttu-id="10869-107">true は、シンボルが定義されていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="10869-107">True means the symbol is defined.</span></span> <span data-ttu-id="10869-108">ステートメント `#if DEBUG` と `#if (DEBUG == true)` の意味は同じです。</span><span class="sxs-lookup"><span data-stu-id="10869-108">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="10869-109">[&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (かつ)、[&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (または)、および [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="10869-109">You can use the operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (and), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (or), and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="10869-110">(not) の各演算子を使用すると、複数のシンボルが定義されているかどうかを評価できます。</span><span class="sxs-lookup"><span data-stu-id="10869-110">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="10869-111">シンボルと演算子は、かっこを使用してグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="10869-111">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10869-112">コメント</span><span class="sxs-lookup"><span data-stu-id="10869-112">Remarks</span></span>  
 <span data-ttu-id="10869-113">`#if` と [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)、[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)、[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)、[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) の各ディレクティブを組み合わせると、1 つ以上のシンボルが存在するかどうかに応じてコードを含めたり除外したりできます。</span><span class="sxs-lookup"><span data-stu-id="10869-113">`#if`, along with the [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), and [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="10869-114">これは、デバッグ ビルドのコードをコンパイルする場合や、特定の構成でコンパイルを行う場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="10869-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>  
  
 <span data-ttu-id="10869-115">`#if` ディレクティブで始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="10869-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>  
  
 <span data-ttu-id="10869-116">`#define` を使用するとシンボルを定義できます。定義したシンボルを `#if` ディレクティブに渡す式として使用すると、この式は `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="10869-116">`#define` lets you define a symbol, such that, by using the symbol as the expression passed to the `#if` directive, the expression will evaluate to `true`.</span></span>  
  
 <span data-ttu-id="10869-117">シンボルは、[/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) コンパイラ オプションでも定義できます。</span><span class="sxs-lookup"><span data-stu-id="10869-117">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="10869-118">[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) を使うと、シンボルを未定義状態にできます。</span><span class="sxs-lookup"><span data-stu-id="10869-118">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="10869-119">`/define` または `#define` で定義されたシンボルは、同じ名前の変数とは競合しません。</span><span class="sxs-lookup"><span data-stu-id="10869-119">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="10869-120">変数名をプリプロセッサ ディレクティブに渡すことはできません。シンボルはプリプロセッサ ディレクティブだけで評価されます。</span><span class="sxs-lookup"><span data-stu-id="10869-120">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="10869-121">`#define` を使用して作成したシンボルのスコープは、そのシンボルが定義されているファイルです。</span><span class="sxs-lookup"><span data-stu-id="10869-121">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10869-122">例</span><span class="sxs-lookup"><span data-stu-id="10869-122">Example</span></span>  
  
```csharp
// preprocessor_if.cs  
#define DEBUG#define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
 <span data-ttu-id="10869-123">**DEBUG and MYTEST are defined**</span><span class="sxs-lookup"><span data-stu-id="10869-123">**DEBUG and MYTEST are defined**</span></span>   
## <a name="see-also"></a><span data-ttu-id="10869-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="10869-124">See Also</span></span>  
 <span data-ttu-id="10869-125">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="10869-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="10869-126">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="10869-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="10869-127">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="10869-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

