---
title: "-define (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d4c7e4e646e6796cff6bbfbe05038ff361fa80c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="define-c-compiler-options"></a><span data-ttu-id="8c860-102">/define (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="8c860-102">/define (C# Compiler Options)</span></span>
<span data-ttu-id="8c860-103">**/define** オプションは、`name` をプログラムのすべてのソース コード ファイル内のシンボルとして定義します。</span><span class="sxs-lookup"><span data-stu-id="8c860-103">The **/define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c860-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c860-104">Syntax</span></span>  
  
```console  
/define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c860-105">引数</span><span class="sxs-lookup"><span data-stu-id="8c860-105">Arguments</span></span>  
 <span data-ttu-id="8c860-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="8c860-106">`name`, `name2`</span></span>  
 <span data-ttu-id="8c860-107">定義する 1 つまたは複数のシンボルの名前。</span><span class="sxs-lookup"><span data-stu-id="8c860-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c860-108">コメント</span><span class="sxs-lookup"><span data-stu-id="8c860-108">Remarks</span></span>  
 <span data-ttu-id="8c860-109">**/define** オプションには、[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) プリプロセッサ ディレクティブを使うのと同じ効果があります。ただし、コンパイラ オプションはプロジェクト内のすべてのファイルに対して有効である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="8c860-109">The **/define** option has the same effect as using a [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="8c860-110">ソース ファイルの [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) ディレクティブがこの定義を削除するまで、シンボルはソース ファイルで定義されたままになります。</span><span class="sxs-lookup"><span data-stu-id="8c860-110">A symbol remains defined in a source file until an [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="8c860-111">/define オプションを使うと、あるファイルで指定されている `#undef` ディレクティブは、プロジェクト内の他のソース コード ファイルには影響しません。</span><span class="sxs-lookup"><span data-stu-id="8c860-111">When you use the /define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="8c860-112">このオプションで作成されるシンボルを [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)、[#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)、および [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) で使う、ソース ファイルを条件付きでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="8c860-112">You can use symbols created by this option with [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), and [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="8c860-113">**/d** は **/define** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="8c860-113">**/d** is the short form of **/define**.</span></span>  
  
 <span data-ttu-id="8c860-114">**/define** では、シンボル名をセミコロンまたはコンマで区切ることにより、複数のシンボルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="8c860-114">You can define multiple symbols with **/define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="8c860-115">例:</span><span class="sxs-lookup"><span data-stu-id="8c860-115">For example:</span></span>  
  
```console  
/define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="8c860-116">C# コンパイラ自体では、ソース コードで使うことができるシンボルやマクロは定義されません。すべてのシンボル定義はユーザーが定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c860-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c860-117">C++ などの言語とは異なり、C# の `#define` では、シンボルに値を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="8c860-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="8c860-118">たとえば、マクロの作成や定数の定義に `#define` を使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="8c860-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="8c860-119">定数を定義する必要がある場合は、`enum` 変数を使います。</span><span class="sxs-lookup"><span data-stu-id="8c860-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="8c860-120">C++ スタイルのマクロを作成する場合は、ジェネリックなどで代用してください。</span><span class="sxs-lookup"><span data-stu-id="8c860-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="8c860-121">マクロはエラーを招きやすいため、C# では、マクロの使用は禁止され、代わりに、より安全な方法が提供されています。</span><span class="sxs-lookup"><span data-stu-id="8c860-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8c860-122">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="8c860-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="8c860-123">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="8c860-123">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="8c860-124">**[ビルド]** タブで、**[条件付きコンパイル シンボル]** ボックスに、定義するシンボルを入力します。</span><span class="sxs-lookup"><span data-stu-id="8c860-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="8c860-125">たとえば、次のコード例を使っている場合は、テキスト ボックスに「`xx`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8c860-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="8c860-126">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8c860-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c860-127">例</span><span class="sxs-lookup"><span data-stu-id="8c860-127">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: /define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c860-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c860-128">See Also</span></span>  
 [<span data-ttu-id="8c860-129">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="8c860-129">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="8c860-130">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="8c860-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
