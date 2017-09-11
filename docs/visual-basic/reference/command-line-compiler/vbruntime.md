---
title: "/vbruntime |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- /vbruntime
dev_langs:
- VB
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cb07ed8c2f6070079cc51c290ff5a61305c5a5d3
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="vbruntime"></a><span data-ttu-id="5be50-102">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="5be50-102">/vbruntime</span></span>
<span data-ttu-id="5be50-103">コンパイラが Visual Basic Runtime Library を参照せずにコンパイルするか、特定のランタイム ライブラリを参照してコンパイルするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5be50-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5be50-104">構文</span><span class="sxs-lookup"><span data-stu-id="5be50-104">Syntax</span></span>  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="5be50-105">引数</span><span class="sxs-lookup"><span data-stu-id="5be50-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="5be50-106">Visual Basic ランタイム ライブラリへの参照なしでコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="5be50-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="5be50-107">既定の Visual Basic ランタイム ライブラリへの参照を使用してコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="5be50-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="5be50-108">Visual Basic ランタイム ライブラリへの参照なしでコンパイルされ、アセンブリに Visual Basic ランタイム ライブラリのコア機能を埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="5be50-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="5be50-109">指定したライブラリ (DLL) への参照を使用してコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="5be50-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5be50-110">コメント</span><span class="sxs-lookup"><span data-stu-id="5be50-110">Remarks</span></span>  
 <span data-ttu-id="5be50-111">`/vbruntime`コンパイラ オプションでは、コンパイラがコンパイルを Visual Basic ランタイム ライブラリへの参照がないことを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="5be50-111">The `/vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="5be50-112">Visual Basic ランタイム ライブラリを参照しないでコンパイルする場合、Visual Basic ランタイム ヘルパー呼び出しを生成するコードや言語の構造にエラーまたは警告が記録されます。</span><span class="sxs-lookup"><span data-stu-id="5be50-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="5be50-113">(A *Visual Basic ランタイム ヘルパー*特定言語のセマンティックを実行する実行時に呼び出される Microsoft.VisualBasic.dll で定義されている関数です)。</span><span class="sxs-lookup"><span data-stu-id="5be50-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="5be50-114">`/vbruntime+`オプションを指定しない場合に発生するのと同じ動作を出力する`/vbruntime`スイッチを指定します。</span><span class="sxs-lookup"><span data-stu-id="5be50-114">The `/vbruntime+` option produces the same behavior that occurs if no `/vbruntime` switch is specified.</span></span> <span data-ttu-id="5be50-115">使用することができます、`/vbruntime+`前オーバーライド オプションを指定`/vbruntime`スイッチです。</span><span class="sxs-lookup"><span data-stu-id="5be50-115">You can use the `/vbruntime+` option to override previous `/vbruntime` switches.</span></span>  
  
 <span data-ttu-id="5be50-116">ほとんどのオブジェクト、`My`型は、使用する場合は使用できません、`/vbruntime-`または`vbruntime:``path`オプション。</span><span class="sxs-lookup"><span data-stu-id="5be50-116">Most objects of the `My` type are unavailable when you use the `/vbruntime-` or `vbruntime:``path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="5be50-117">Visual Basic ランタイムのコア機能を埋め込む</span><span class="sxs-lookup"><span data-stu-id="5be50-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="5be50-118">`/vbruntime*`オプションでは、ランタイム ライブラリへの参照なしでコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="5be50-118">The `/vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="5be50-119">代わりに、Visual Basic ランタイム ライブラリのコア機能は、ユーザー アセンブリに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="5be50-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="5be50-120">Visual Basic ランタイムが含まれていないプラットフォームで、アプリケーションが実行されている場合は、このオプションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5be50-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="5be50-121">次のランタイムのメンバーが埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="5be50-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="5be50-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions>クラス</xref:Microsoft.VisualBasic.CompilerServices.Conversions></span><span class="sxs-lookup"><span data-stu-id="5be50-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="5be50-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>メソッド</xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29></span><span class="sxs-lookup"><span data-stu-id="5be50-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="5be50-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>メソッド</xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="5be50-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="5be50-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>メソッド</xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29></span><span class="sxs-lookup"><span data-stu-id="5be50-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="5be50-126"><xref:Microsoft.VisualBasic.Constants.vbBack>定数</xref:Microsoft.VisualBasic.Constants.vbBack></span><span class="sxs-lookup"><span data-stu-id="5be50-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="5be50-127"><xref:Microsoft.VisualBasic.Constants.vbCr>定数</xref:Microsoft.VisualBasic.Constants.vbCr></span><span class="sxs-lookup"><span data-stu-id="5be50-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="5be50-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf>定数</xref:Microsoft.VisualBasic.Constants.vbCrLf></span><span class="sxs-lookup"><span data-stu-id="5be50-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="5be50-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed>定数</xref:Microsoft.VisualBasic.Constants.vbFormFeed></span><span class="sxs-lookup"><span data-stu-id="5be50-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="5be50-130"><xref:Microsoft.VisualBasic.Constants.vbLf>定数</xref:Microsoft.VisualBasic.Constants.vbLf></span><span class="sxs-lookup"><span data-stu-id="5be50-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="5be50-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine>定数</xref:Microsoft.VisualBasic.Constants.vbNewLine></span><span class="sxs-lookup"><span data-stu-id="5be50-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="5be50-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar>定数</xref:Microsoft.VisualBasic.Constants.vbNullChar></span><span class="sxs-lookup"><span data-stu-id="5be50-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="5be50-133"><xref:Microsoft.VisualBasic.Constants.vbNullString>定数</xref:Microsoft.VisualBasic.Constants.vbNullString></span><span class="sxs-lookup"><span data-stu-id="5be50-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="5be50-134"><xref:Microsoft.VisualBasic.Constants.vbTab>定数</xref:Microsoft.VisualBasic.Constants.vbTab></span><span class="sxs-lookup"><span data-stu-id="5be50-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="5be50-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab>定数</xref:Microsoft.VisualBasic.Constants.vbVerticalTab></span><span class="sxs-lookup"><span data-stu-id="5be50-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="5be50-136">一部のオブジェクトの`My`型</span><span class="sxs-lookup"><span data-stu-id="5be50-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="5be50-137">使用してコンパイルした場合、`/vbruntime*`オプションと、コードは、コア機能に埋め込まれていない Visual Basic ランタイム ライブラリのメンバーを参照、コンパイラはメンバーが使用できないことを示すエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="5be50-137">If you compile using the `/vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="5be50-138">指定したライブラリを参照します。</span><span class="sxs-lookup"><span data-stu-id="5be50-138">Referencing a specified library</span></span>  
 <span data-ttu-id="5be50-139">使用することができます、 `path` Visual Basic ランタイム ライブラリの既定ではなくカスタムのランタイム ライブラリへの参照をコンパイルする引数。</span><span class="sxs-lookup"><span data-stu-id="5be50-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="5be50-140">場合の値、`path`引数が、DLL への完全修飾パスでは、コンパイラは、ランタイム ライブラリとそのファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="5be50-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="5be50-141">場合の値、`path`引数が、DLL への完全修飾パスではない、Visual Basic コンパイラは、現在のフォルダーで識別された DLL の最初に検索します。</span><span class="sxs-lookup"><span data-stu-id="5be50-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="5be50-142">使用して、指定したパスの検索、 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="5be50-142">It will then search in the path that you have specified by using the [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="5be50-143">場合、`/sdkpath`コンパイラ オプションは使用しない場合、コンパイラは、特定の DLL を .NET Framework フォルダーに検索されます (`%systemroot%\Microsoft.NET\Framework\versionNumber`)。</span><span class="sxs-lookup"><span data-stu-id="5be50-143">If the `/sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5be50-144">例</span><span class="sxs-lookup"><span data-stu-id="5be50-144">Example</span></span>  
 <span data-ttu-id="5be50-145">次の例では、使用する方法、`/vbruntime`カスタム ライブラリへの参照を使用してコンパイルするにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="5be50-145">The following example shows how to use the `/vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="5be50-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="5be50-146">See Also</span></span>  
 <span data-ttu-id="5be50-147">[Visual Basic コア – Visual Studio 2010 SP1 での新しいコンパイル モード](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx) </span><span class="sxs-lookup"><span data-stu-id="5be50-147">[Visual Basic Core – New compilation mode in Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx) </span></span>  
<span data-ttu-id="5be50-148"> [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="5be50-148"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="5be50-149"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="5be50-149"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="5be50-150"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span><span class="sxs-lookup"><span data-stu-id="5be50-150"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span></span>
