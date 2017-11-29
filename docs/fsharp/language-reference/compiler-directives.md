---
title: "コンパイラ ディレクティブ (F#)"
description: "F# の言語プリプロセッサ ディレクティブ、条件付きコンパイル ディレクティブは、行ディレクティブとコンパイラ ディレクティブについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 93aef07a-6747-4ce4-a10f-a05168978af6
ms.openlocfilehash: b4305d24163f9b23631d5efb6e838f55127cd9f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="compiler-directives"></a><span data-ttu-id="26235-104">コンパイラ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="26235-104">Compiler Directives</span></span>

<span data-ttu-id="26235-105">このトピックでは、プロセッサ ディレクティブとコンパイラ ディレクティブについて説明します。</span><span class="sxs-lookup"><span data-stu-id="26235-105">This topic describes processor directives and compiler directives.</span></span>


## <a name="preprocessor-directives"></a><span data-ttu-id="26235-106">プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="26235-106">Preprocessor Directives</span></span>
<span data-ttu-id="26235-107">プリプロセッサ ディレクティブは、# シンボルで始まり、独立した行に記述されます。</span><span class="sxs-lookup"><span data-stu-id="26235-107">A preprocessor directive is prefixed with the # symbol and appears on a line by itself.</span></span> <span data-ttu-id="26235-108">プリプロセッサ ディレクティブは、コンパイラ自体の前に実行されるプリプロセッサにより解釈されます。</span><span class="sxs-lookup"><span data-stu-id="26235-108">It is interpreted by the preprocessor, which runs before the compiler itself.</span></span>

<span data-ttu-id="26235-109">次の表に、F# で使用できるプリプロセッサ ディレクティブの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="26235-109">The following table lists the preprocessor directives that are available in F#.</span></span>


|<span data-ttu-id="26235-110">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="26235-110">Directive</span></span>|<span data-ttu-id="26235-111">説明</span><span class="sxs-lookup"><span data-stu-id="26235-111">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="26235-112">`#if`*シンボル*</span><span class="sxs-lookup"><span data-stu-id="26235-112">`#if` *symbol*</span></span>|<span data-ttu-id="26235-113">条件付きコンパイルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="26235-113">Supports conditional compilation.</span></span> <span data-ttu-id="26235-114">後のセクションのコードで、`#if`場合に値が含まれる、*シンボル*が定義されています。</span><span class="sxs-lookup"><span data-stu-id="26235-114">Code in the section after the `#if` is included if the *symbol* is defined.</span></span>|
|`#else`|<span data-ttu-id="26235-115">条件付きコンパイルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="26235-115">Supports conditional compilation.</span></span> <span data-ttu-id="26235-116">前の `#if` で使用したシンボルが定義されていない場合に含めるコードのセクションをマークします。</span><span class="sxs-lookup"><span data-stu-id="26235-116">Marks a section of code to include if the symbol used with the previous `#if` is not defined.</span></span>|
|`#endif`|<span data-ttu-id="26235-117">条件付きコンパイルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="26235-117">Supports conditional compilation.</span></span> <span data-ttu-id="26235-118">コードの条件付きセクションの末尾をマークします。</span><span class="sxs-lookup"><span data-stu-id="26235-118">Marks the end of a conditional section of code.</span></span>|
|<span data-ttu-id="26235-119">`#`[行]*int*、</span><span class="sxs-lookup"><span data-stu-id="26235-119">`#`[line] *int*,</span></span><br/><span data-ttu-id="26235-120">`#`[行]*int* *文字列*、</span><span class="sxs-lookup"><span data-stu-id="26235-120">`#`[line] *int* *string*,</span></span><br/><span data-ttu-id="26235-121">`#`[行]*int* *逐語的文字列*</span><span class="sxs-lookup"><span data-stu-id="26235-121">`#`[line] *int* *verbatim-string*</span></span>|<span data-ttu-id="26235-122">デバッグ用に、元のソース コードの行とファイル名を示します。</span><span class="sxs-lookup"><span data-stu-id="26235-122">Indicates the original source code line and file name, for debugging.</span></span> <span data-ttu-id="26235-123">この機能は、F# ソース コードを生成するツール用に用意されています。</span><span class="sxs-lookup"><span data-stu-id="26235-123">This feature is provided for tools that generate F# source code.</span></span>|
|<span data-ttu-id="26235-124">`#nowarn`*warningcode*</span><span class="sxs-lookup"><span data-stu-id="26235-124">`#nowarn` *warningcode*</span></span>|<span data-ttu-id="26235-125">コンパイラ警告を無効にします。</span><span class="sxs-lookup"><span data-stu-id="26235-125">Disables a compiler warning or warnings.</span></span> <span data-ttu-id="26235-126">警告を無効にするには、コンパイラ出力で警告の番号を確認し、その番号を引用符で囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="26235-126">To disable a warning, find its number from the compiler output and include it in quotation marks.</span></span> <span data-ttu-id="26235-127">"FS" プレフィックスを省略します。</span><span class="sxs-lookup"><span data-stu-id="26235-127">Omit the "FS" prefix.</span></span> <span data-ttu-id="26235-128">1 つの行で複数の警告番号を無効にするには、それぞれの番号を引用符で囲んだうえで各文字列をスペースで区切ります。</span><span class="sxs-lookup"><span data-stu-id="26235-128">To disable multiple warning numbers on the same line, include each number in quotation marks, and separate each string by a space.</span></span> <span data-ttu-id="26235-129">例:</span><span class="sxs-lookup"><span data-stu-id="26235-129">For example:</span></span>

`#nowarn "9" "40"`


<span data-ttu-id="26235-130">警告の無効化の効果は、ディレクティブの前にあるファイルの部分を含む、ファイル全体に適用されます |。</span><span class="sxs-lookup"><span data-stu-id="26235-130">The effect of disabling a warning applies to the entire file, including portions of the file that precede the directive.|</span></span>

## <a name="conditional-compilation-directives"></a><span data-ttu-id="26235-131">条件付きコンパイル ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="26235-131">Conditional Compilation Directives</span></span>
<span data-ttu-id="26235-132">Visual StudioCode エディターで淡色表示にはこれらのディレクティブのいずれかによって非アクティブ化コードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="26235-132">Code that is deactivated by one of these directives appears dimmed in the Visual StudioCode Editor.</span></span>


>[!NOTE] 
<span data-ttu-id="26235-133">条件付きコンパイル ディレクティブの動作は、他の言語と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="26235-133">The behavior of the conditional compilation directives is not the same as it is in other languages.</span></span> <span data-ttu-id="26235-134">たとえば、シンボルを含むブール式を使用することはできません。また、`true` および `false` には特別な意味はありません。</span><span class="sxs-lookup"><span data-stu-id="26235-134">For example, you cannot use Boolean expressions involving symbols, and `true` and `false` have no special meaning.</span></span> <span data-ttu-id="26235-135">`if` ディレクティブで使用するシンボルは、コマンド ラインまたはプロジェクト設定で定義する必要があります。`define` プリプロセッサ ディレクティブは存在しません。</span><span class="sxs-lookup"><span data-stu-id="26235-135">Symbols that you use in the `if` directive must be defined by the command line or in the project settings; there is no `define` preprocessor directive.</span></span>


<span data-ttu-id="26235-136">次のコードは、`#if` ディレクティブ、`#else` ディレクティブ、および `#endif` ディレクティブの使用例を示しています。</span><span class="sxs-lookup"><span data-stu-id="26235-136">The following code illustrates the use of the `#if`, `#else`, and `#endif` directives.</span></span> <span data-ttu-id="26235-137">この例では、`function1` の定義の 2 つのバージョンがコードに含まれています。</span><span class="sxs-lookup"><span data-stu-id="26235-137">In this example, the code contains two versions of the definition of `function1`.</span></span> <span data-ttu-id="26235-138">ときに`VERSION1`を使用して定義、 [-コンパイラ オプションを定義する](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)、コードの間、`#if`ディレクティブと`#else`ディレクティブがアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="26235-138">When `VERSION1` is defined by using the [-define compiler option](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), the code between the `#if` directive and the `#else` directive is activated.</span></span> <span data-ttu-id="26235-139">それ以外の場合、`#else` と `#endif` の間にあるコードがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="26235-139">Otherwise, the code between `#else` and `#endif` is activated.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

<span data-ttu-id="26235-140">F# には、`#define` プリプロセッサ ディレクティブはありません。</span><span class="sxs-lookup"><span data-stu-id="26235-140">There is no `#define` preprocessor directive in F#.</span></span> <span data-ttu-id="26235-141">`#if` ディレクティブで使用するシンボルを定義するには、コンパイラ オプションまたはプロジェクト設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26235-141">You must use the compiler option or project settings to define the symbols used by the `#if` directive.</span></span>

<span data-ttu-id="26235-142">条件付きコンパイル ディレクティブは、入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="26235-142">Conditional compilation directives can be nested.</span></span> <span data-ttu-id="26235-143">プリプロセッサ ディレクティブでは、インデントに意味はありません。</span><span class="sxs-lookup"><span data-stu-id="26235-143">Indentation is not significant for preprocessor directives.</span></span>


## <a name="line-directives"></a><span data-ttu-id="26235-144">行ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="26235-144">Line Directives</span></span>
<span data-ttu-id="26235-145">ビルド時にコンパイラは、各エラーが発生した行番号を参照して、F# コード内のエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="26235-145">When building, the compiler reports errors in F# code by referencing line numbers on which each error occurs.</span></span> <span data-ttu-id="26235-146">これらの行番号は、ファイル内の最初の行から 1 で始まります。</span><span class="sxs-lookup"><span data-stu-id="26235-146">These line numbers start at 1 for the first line in a file.</span></span> <span data-ttu-id="26235-147">ただし、別のツールから F# ソース コードを生成している場合、生成されたコードの行番号は、通常、重要ではありません。これは、生成された F# コード内のエラーは、別のソースから発生する可能性が高いためです。</span><span class="sxs-lookup"><span data-stu-id="26235-147">However, if you are generating F# source code from another tool, the line numbers in the generated code are generally not of interest, because the errors in the generated F# code most likely arise from another source.</span></span> <span data-ttu-id="26235-148">`#line` ディレクティブを使用すると、F# ソース コードを生成するツールの作成者が、元の行番号およびソース ファイルに関する情報を、生成された F# コードに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="26235-148">The `#line` directive provides a way for authors of tools that generate F# source code to pass information about the original line numbers and source files to the generated F# code.</span></span>

<span data-ttu-id="26235-149">`#line` ディレクティブを使用する場合、ファイル名を引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="26235-149">When you use the `#line` directive, file names must be enclosed in quotation marks.</span></span> <span data-ttu-id="26235-150">パスでバックスラッシュ文字を使用するには、文字列の前に逐語的トークン (`@`) がある場合を除き、バックスラッシュ文字をエスケープする必要があります。エスケープするには、バックスラッシュ文字を 1 つではなく、2 つ使用します。</span><span class="sxs-lookup"><span data-stu-id="26235-150">Unless the verbatim token (`@`) appears in front of the string, you must escape backslash characters by using two backslash characters instead of one in order to use them in the path.</span></span> <span data-ttu-id="26235-151">有効な行トークンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="26235-151">The following are valid line tokens.</span></span> <span data-ttu-id="26235-152">これらの例では、ツールを使用して元のファイル `Script1` を実行したときに F# コード ファイルが自動生成され、これらのディレクティブがある位置のコードが `Script1` ファイルの 25 行目のトークンから生成されるものと仮定します。</span><span class="sxs-lookup"><span data-stu-id="26235-152">In these examples, assume that the original file `Script1` results in an automatically generated F# code file when it is run through a tool, and that the code at the location of these directives is generated from some tokens at line 25 in file `Script1`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

<span data-ttu-id="26235-153">これらのトークンは、この場所で生成された F# コードが、`Script1` 内の行 `25` またはその近くにあるなんらかの構成要素から派生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="26235-153">These tokens indicate that the F# code generated at this location is derived from some constructs at or near line `25` in `Script1`.</span></span>


## <a name="compiler-directives"></a><span data-ttu-id="26235-154">コンパイラ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="26235-154">Compiler Directives</span></span>
<span data-ttu-id="26235-155">コンパイラ ディレクティブは、# 記号で始まるという点でプリプロセッサ ディレクティブに似ていますが、プリプロセッサが解釈するのではなく、コンパイラが解釈して対応できるように放置されます。</span><span class="sxs-lookup"><span data-stu-id="26235-155">Compiler directives resemble preprocessor directives, because they are prefixed with a # sign, but instead of being interpreted by the preprocessor, they are left for the compiler to interpret and act on.</span></span>

<span data-ttu-id="26235-156">次の表に、F# で使用できるコンパイラ ディレクティブの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="26235-156">The following table lists the compiler directive that is available in F#.</span></span>


|<span data-ttu-id="26235-157">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="26235-157">Directive</span></span>|<span data-ttu-id="26235-158">説明</span><span class="sxs-lookup"><span data-stu-id="26235-158">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="26235-159">`#light`["on"</span><span class="sxs-lookup"><span data-stu-id="26235-159">`#light` ["on"</span></span>|<span data-ttu-id="26235-160">"off"]</span><span class="sxs-lookup"><span data-stu-id="26235-160">"off"]</span></span>|<span data-ttu-id="26235-161">他のバージョンの ML との互換性を保つために、軽量構文を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="26235-161">Enables or disables lightweight syntax, for compatibility with other versions of ML.</span></span> <span data-ttu-id="26235-162">既定では、軽量構文は有効です。</span><span class="sxs-lookup"><span data-stu-id="26235-162">By default, lightweight syntax is enabled.</span></span> <span data-ttu-id="26235-163">冗語構文は常に有効です。</span><span class="sxs-lookup"><span data-stu-id="26235-163">Verbose syntax is always enabled.</span></span> <span data-ttu-id="26235-164">したがって、軽量構文と冗語構文の両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="26235-164">Therefore, you can use both lightweight syntax and verbose syntax.</span></span> <span data-ttu-id="26235-165">ディレクティブ `#light` は `#light "on"` と同等です。</span><span class="sxs-lookup"><span data-stu-id="26235-165">The directive `#light` by itself is equivalent to `#light "on"`.</span></span> <span data-ttu-id="26235-166">`#light "off"` を指定した場合は、すべての言語構成要素に冗語構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26235-166">If you specify `#light "off"`, you must use verbose syntax for all language constructs.</span></span> <span data-ttu-id="26235-167">F# のドキュメント内の構文は、軽量構文の使用を前提として記述されています。</span><span class="sxs-lookup"><span data-stu-id="26235-167">Syntax in the documentation for F# is presented with the assumption that you are using lightweight syntax.</span></span> <span data-ttu-id="26235-168">詳細については、次を参照してください。[冗語構文](verbose-syntax.md)です。</span><span class="sxs-lookup"><span data-stu-id="26235-168">For more information, see [Verbose Syntax](verbose-syntax.md).</span></span>|
<span data-ttu-id="26235-169">インタープリター (fsi.exe) ディレクティブは、次を参照してください。 [f# による対話型プログラミング](../tutorials/fsharp-interactive/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="26235-169">For interpreter (fsi.exe) directives, see [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="26235-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="26235-170">See Also</span></span>
[<span data-ttu-id="26235-171">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="26235-171">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="26235-172">コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="26235-172">Compiler Options</span></span>](compiler-options.md)

