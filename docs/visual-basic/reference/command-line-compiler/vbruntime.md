---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d28d0556a662099e4e5e74b22583fc3c8b4c313f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656114"
---
# <a name="-vbruntime"></a><span data-ttu-id="3ad53-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="3ad53-102">-vbruntime</span></span>
<span data-ttu-id="3ad53-103">コンパイラが Visual Basic Runtime Library を参照せずにコンパイルするか、特定のランタイム ライブラリを参照してコンパイルするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3ad53-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ad53-104">構文</span><span class="sxs-lookup"><span data-stu-id="3ad53-104">Syntax</span></span>  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="3ad53-105">引数</span><span class="sxs-lookup"><span data-stu-id="3ad53-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="3ad53-106">Visual Basic ランタイム ライブラリへの参照なしでコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="3ad53-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="3ad53-107">既定の Visual Basic ランタイム ライブラリへの参照を使用してコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="3ad53-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="3ad53-108">Visual Basic ランタイム ライブラリへの参照なしでコンパイルして、コア機能を Visual Basic ランタイム ライブラリからアセンブリに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="3ad53-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="3ad53-109">指定したライブラリ (DLL) への参照を使用してコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="3ad53-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ad53-110">コメント</span><span class="sxs-lookup"><span data-stu-id="3ad53-110">Remarks</span></span>  
 <span data-ttu-id="3ad53-111">`-vbruntime`コンパイラ オプションでは、コンパイラがコンパイルを Visual Basic ランタイム ライブラリへの参照がないことを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3ad53-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="3ad53-112">Visual Basic ランタイム ライブラリへの参照がないことをコンパイルする場合は、エラーまたは警告が Visual Basic ランタイム ヘルパーへの呼び出しを生成するコードや言語の構造に記録されます。</span><span class="sxs-lookup"><span data-stu-id="3ad53-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="3ad53-113">(A *Visual Basic ランタイム ヘルパー*特定言語のセマンティックを実行する実行時に呼び出される Microsoft.VisualBasic.dll で定義されている関数です)。</span><span class="sxs-lookup"><span data-stu-id="3ad53-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="3ad53-114">`-vbruntime+`オプションがない場合に発生するのと同じ動作を生成する`-vbruntime`スイッチを指定します。</span><span class="sxs-lookup"><span data-stu-id="3ad53-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="3ad53-115">使用することができます、`-vbruntime+`以前オーバーライド オプションを指定`-vbruntime`スイッチ。</span><span class="sxs-lookup"><span data-stu-id="3ad53-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="3ad53-116">ほとんどのオブジェクト、`My`型は、使用する場合は使用できません、`-vbruntime-`または`-vbruntime:path`オプション。</span><span class="sxs-lookup"><span data-stu-id="3ad53-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="3ad53-117">Visual Basic ランタイム コア機能の埋め込み</span><span class="sxs-lookup"><span data-stu-id="3ad53-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="3ad53-118">`-vbruntime*`オプションでは、ランタイム ライブラリへの参照なしでコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="3ad53-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="3ad53-119">代わりに、Visual Basic ランタイム ライブラリのコア機能は、ユーザー アセンブリに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="3ad53-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="3ad53-120">Visual Basic ランタイムが含まれていないプラットフォームで、アプリケーションが実行する場合は、このオプションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3ad53-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="3ad53-121">次のランタイムのメンバーが埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="3ad53-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="3ad53-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> クラス</span><span class="sxs-lookup"><span data-stu-id="3ad53-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="3ad53-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> メソッド</span><span class="sxs-lookup"><span data-stu-id="3ad53-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="3ad53-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> メソッド</span><span class="sxs-lookup"><span data-stu-id="3ad53-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="3ad53-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> メソッド</span><span class="sxs-lookup"><span data-stu-id="3ad53-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="3ad53-126"><xref:Microsoft.VisualBasic.Constants.vbBack> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="3ad53-127"><xref:Microsoft.VisualBasic.Constants.vbCr> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="3ad53-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="3ad53-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="3ad53-130"><xref:Microsoft.VisualBasic.Constants.vbLf> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="3ad53-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="3ad53-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="3ad53-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="3ad53-134"><xref:Microsoft.VisualBasic.Constants.vbTab> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="3ad53-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> 定数</span><span class="sxs-lookup"><span data-stu-id="3ad53-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="3ad53-136">一部のオブジェクトの`My`型</span><span class="sxs-lookup"><span data-stu-id="3ad53-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="3ad53-137">使用してコンパイルする場合、`-vbruntime*`オプションと、コードは、コア機能に埋め込まれていない、Visual Basic ランタイム ライブラリからメンバーを参照、コンパイラはメンバーが使用できないことを示すエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="3ad53-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="3ad53-138">指定したライブラリを参照します。</span><span class="sxs-lookup"><span data-stu-id="3ad53-138">Referencing a specified library</span></span>  
 <span data-ttu-id="3ad53-139">使用することができます、`path`既定の Visual Basic ランタイム ライブラリではなく、カスタム ランタイム ライブラリへの参照を使用してコンパイルする引数。</span><span class="sxs-lookup"><span data-stu-id="3ad53-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="3ad53-140">場合の値、`path`引数が、DLL への完全修飾パスでは、コンパイラは、ランタイム ライブラリとそのファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="3ad53-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="3ad53-141">場合の値、`path`引数は、DLL への完全修飾パスではありません、Visual Basic コンパイラは最初に、現在のフォルダーで識別された DLL を検索します。</span><span class="sxs-lookup"><span data-stu-id="3ad53-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="3ad53-142">使用して、指定したパスの検索、 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="3ad53-142">It will then search in the path that you have specified by using the [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="3ad53-143">場合、`-sdkpath`コンパイラ オプションを使用しない、コンパイラは、.NET Framework フォルダーで識別された DLL の検索 (`%systemroot%\Microsoft.NET\Framework\versionNumber`)。</span><span class="sxs-lookup"><span data-stu-id="3ad53-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ad53-144">例</span><span class="sxs-lookup"><span data-stu-id="3ad53-144">Example</span></span>  
 <span data-ttu-id="3ad53-145">次の例を使用する方法を示しています、`-vbruntime`カスタム ライブラリへの参照を使用してコンパイルするにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="3ad53-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ad53-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ad53-146">See Also</span></span>  
 [<span data-ttu-id="3ad53-147">Visual Basic コア – Visual Studio 2010 SP1 で新規のコンパイル モード</span><span class="sxs-lookup"><span data-stu-id="3ad53-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [<span data-ttu-id="3ad53-148">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="3ad53-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3ad53-149">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="3ad53-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="3ad53-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="3ad53-150">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
