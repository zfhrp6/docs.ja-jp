---
title: '#if プリプロセッサ ディレクティブ (C# リファレンス)'
ms.date: 02/13/2017
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 2ae0af6971dbf549b52e8168e035d8582bdab61d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287684"
---
# <a name="if-c-reference"></a><span data-ttu-id="ecb62-102">#if (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ecb62-102">#if (C# Reference)</span></span>

<span data-ttu-id="ecb62-103">C# コンパイラでは、`#if` ディレクティブ、次いで [#endif](preprocessor-endif.md) ディレクティブが検出されると、これらのディレクティブ間のコードがコンパイルされます (指定されたシンボルが定義されている場合に限る)。</span><span class="sxs-lookup"><span data-stu-id="ecb62-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="ecb62-104">C および C++ とは異なり、シンボルに数値を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="ecb62-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="ecb62-105">C# の #if ステートメントはブール値で、シンボルが定義されているかどうかのみをテストします。</span><span class="sxs-lookup"><span data-stu-id="ecb62-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="ecb62-106">例:</span><span class="sxs-lookup"><span data-stu-id="ecb62-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="ecb62-107">[==](../operators/equality-comparison-operator.md) (等しい) および [!=](../operators/not-equal-operator.md) (等しくない) の各演算子は、[true](../keywords/true.md) か [false](../keywords/false.md) のどちらであるかのテストにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-107">You can use the operators [==](../operators/equality-comparison-operator.md) (equality) and [!=](../operators/not-equal-operator.md) (inequality) only to test for [true](../keywords/true.md) or [false](../keywords/false.md).</span></span> <span data-ttu-id="ecb62-108">true は、シンボルが定義されていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ecb62-108">True means the symbol is defined.</span></span> <span data-ttu-id="ecb62-109">ステートメント `#if DEBUG` と `#if (DEBUG == true)` の意味は同じです。</span><span class="sxs-lookup"><span data-stu-id="ecb62-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="ecb62-110">[&&](../operators/conditional-and-operator.md) (かつ)、[&#124;&#124;](../operators/conditional-or-operator.md) (または)、および [!](../operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="ecb62-110">You can use the operators [&&](../operators/conditional-and-operator.md) (and), [&#124;&#124;](../operators/conditional-or-operator.md) (or), and [!](../operators/logical-negation-operator.md)</span></span> <span data-ttu-id="ecb62-111">(not) の各演算子を使用すると、複数のシンボルが定義されているかどうかを評価できます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="ecb62-112">シンボルと演算子は、かっこを使用してグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="ecb62-113">コメント</span><span class="sxs-lookup"><span data-stu-id="ecb62-113">Remarks</span></span>

<span data-ttu-id="ecb62-114">`#if` と [#else](preprocessor-else.md)、[#elif](preprocessor-elif.md)、[#endif](preprocessor-endif.md)、[#define](preprocessor-define.md)、[#undef](preprocessor-undef.md) の各ディレクティブを組み合わせると、1 つ以上のシンボルが存在するかどうかに応じてコードを含めたり除外したりできます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="ecb62-115">これは、デバッグ ビルドのコードをコンパイルする場合や、特定の構成でコンパイルを行う場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="ecb62-116">`#if` ディレクティブで始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecb62-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="ecb62-117">`#define` を使用するとシンボルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="ecb62-118">定義したシンボルを `#if` ディレクティブに渡す式として使用すると、この式は `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="ecb62-119">シンボルは、[/define](../compiler-options/define-compiler-option.md) コンパイラ オプションでも定義できます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-119">You can also define a symbol with the [/define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="ecb62-120">[#undef](preprocessor-undef.md) を使うと、シンボルを未定義状態にできます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="ecb62-121">`/define` または `#define` で定義されたシンボルは、同じ名前の変数とは競合しません。</span><span class="sxs-lookup"><span data-stu-id="ecb62-121">A symbol that you define with `/define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="ecb62-122">変数名をプリプロセッサ ディレクティブに渡すことはできません。シンボルはプリプロセッサ ディレクティブだけで評価されます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="ecb62-123">`#define` を使用して作成したシンボルのスコープは、そのシンボルが定義されているファイルです。</span><span class="sxs-lookup"><span data-stu-id="ecb62-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="ecb62-124">また、ビルド システムも、各種[ターゲット フレームワーク](../../../standard/frameworks.md)を表す、定義済みプリプロセッサ シンボルを認識します。</span><span class="sxs-lookup"><span data-stu-id="ecb62-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="ecb62-125">これは、複数の .NET の実装やバージョンをターゲットとできるアプリケーションを作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="ecb62-126">他の定義済みシンボルとしては、DEBUG 定数と TRACE 定数があります。</span><span class="sxs-lookup"><span data-stu-id="ecb62-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="ecb62-127">`#define` を使用して、プロジェクトに設定された値を上書きできます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="ecb62-128">たとえば、DEBUG シンボルは、ビルド構成プロパティ ("デバッグ" モードまたは "リリース" モード) に応じて自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ecb62-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="ecb62-129">使用例</span><span class="sxs-lookup"><span data-stu-id="ecb62-129">Examples</span></span>

<span data-ttu-id="ecb62-130">次の例は、ファイルで MYTEST シンボルを定義し、MYTEST シンボルと DEBUG シンボルの値をテストする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ecb62-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="ecb62-131">この例の出力は、プロジェクトをデバッグとリリースのどちらの構成モードでビルドするかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ecb62-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

```csharp
#define MYTEST
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

<span data-ttu-id="ecb62-132">次の例は、各種ターゲット フレームワークをテストし、可能な場合には新しい API を使用できるようにする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ecb62-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a><span data-ttu-id="ecb62-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecb62-133">See also</span></span>

[<span data-ttu-id="ecb62-134">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="ecb62-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="ecb62-135">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ecb62-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="ecb62-136">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="ecb62-136">C# Preprocessor Directives</span></span>](index.md)  
<span data-ttu-id="ecb62-137">[方法 : トレースとデバッグを指定して条件付きコンパイルを実行する](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)。</span><span class="sxs-lookup"><span data-stu-id="ecb62-137">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span></span>
