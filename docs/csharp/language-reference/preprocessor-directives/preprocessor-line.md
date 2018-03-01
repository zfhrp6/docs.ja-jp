---
title: "#line (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d2f42915d214349eebff40949482d7f603c0c2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="line-c-reference"></a><span data-ttu-id="2b94e-102">#line (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2b94e-102">#line (C# Reference)</span></span>
<span data-ttu-id="2b94e-103">`#line` を使用すると、コンパイラの行番号および (必要に応じて) エラーと警告に出力されるファイル名を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="2b94e-103">`#line` lets you modify the compiler's line number and (optionally) the file name output for errors and warnings.</span></span> <span data-ttu-id="2b94e-104">この例では、行番号に関連付けられている 2 つの警告を報告する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2b94e-104">This example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="2b94e-105">`#line 200` ディレクティブは行番号が 200 (既定では 7) になるように強制し、次の #line ディレクティブまでファイル名を "Special" として報告します。</span><span class="sxs-lookup"><span data-stu-id="2b94e-105">The `#line 200` directive forces the line number to be 200 (although the default is #7) and until the next #line directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="2b94e-106">#line default ディレクティブは、行の番号付けをその既定の番号付けに戻します。つまり、前のディレクティブで番号が付け直された行をカウントします。</span><span class="sxs-lookup"><span data-stu-id="2b94e-106">The #line default directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="2b94e-107">コメント</span><span class="sxs-lookup"><span data-stu-id="2b94e-107">Remarks</span></span>  
 <span data-ttu-id="2b94e-108">`#line` ディレクティブは、ビルド プロセスで自動化された中間ステップで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b94e-108">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="2b94e-109">たとえば、行が元のソース コード ファイルから削除されても、ファイル内の元の行番号付けに基づいてコンパイラに引き続き出力を生成させる場合は、行を削除してから `#line` を使用して元の行番号付けをシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="2b94e-109">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>  
  
 <span data-ttu-id="2b94e-110">開発者がコードをステップ実行すると、`#line hidden` と次の `#line` ディレクティブ (別の `#line hidden` ディレクティブではないと仮定) の間のすべての行がステップ オーバーされるように、`#line hidden` ディレクティブは、連続する行をデバッガーから隠します。</span><span class="sxs-lookup"><span data-stu-id="2b94e-110">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="2b94e-111">このオプションは、ユーザー定義のコードとコンピューターによって生成されたコードを ASP.NET が区別できるようするために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2b94e-111">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="2b94e-112">この機能を主に使用しているのは ASP.NET ですが、より多くのソース ジェネレーターが利用できる可能性はあります。</span><span class="sxs-lookup"><span data-stu-id="2b94e-112">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>  
  
 <span data-ttu-id="2b94e-113">`#line hidden` ディレクティブはエラーの報告でのファイル名や行番号には影響しません。</span><span class="sxs-lookup"><span data-stu-id="2b94e-113">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="2b94e-114">つまり、非表示のブロックでエラーが発生した場合、コンパイラはエラーの現在のファイル名と行番号を報告します。</span><span class="sxs-lookup"><span data-stu-id="2b94e-114">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>  
  
 <span data-ttu-id="2b94e-115">`#line filename` ディレクティブは、コンパイラ出力に表示するファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b94e-115">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="2b94e-116">既定では、ソース コード ファイルの実際の名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2b94e-116">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="2b94e-117">ファイル名は、二重引用符 ("") で囲み、前に行番号を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b94e-117">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>  
  
 <span data-ttu-id="2b94e-118">ソース コード ファイルは、任意の数の `#line` ディレクティブを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="2b94e-118">A source code file can have any number of `#line` directives.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="2b94e-119">例 1</span><span class="sxs-lookup"><span data-stu-id="2b94e-119">Example 1</span></span>  
 <span data-ttu-id="2b94e-120">次の例では、デバッガーがコード内の非表示の行を無視する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2b94e-120">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="2b94e-121">例を実行すると、次の 3 行のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b94e-121">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="2b94e-122">しかし、例に示されているようにブレークポイントを設定し、F10 キーを押してコードをステップ実行すると、デバッガーが非表示の行を無視することがわかります。</span><span class="sxs-lookup"><span data-stu-id="2b94e-122">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="2b94e-123">非表示の行にブレークポイントを設定した場合でも、デバッガーは無視することに注目してください。</span><span class="sxs-lookup"><span data-stu-id="2b94e-123">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>  
  
```csharp
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b94e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b94e-124">See Also</span></span>  
 [<span data-ttu-id="2b94e-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="2b94e-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2b94e-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2b94e-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2b94e-127">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="2b94e-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
