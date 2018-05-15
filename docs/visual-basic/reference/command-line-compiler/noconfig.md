---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: bce2d98a8915e80cdecd7b67029b0c872cf70140
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-noconfig"></a><span data-ttu-id="f6eda-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="f6eda-102">-noconfig</span></span>
<span data-ttu-id="f6eda-103">コンパイラいない自動的を参照することはよく使用される指定[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリまたはインポート、`System`と`Microsoft.VisualBasic`名前空間。</span><span class="sxs-lookup"><span data-stu-id="f6eda-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6eda-104">構文</span><span class="sxs-lookup"><span data-stu-id="f6eda-104">Syntax</span></span>  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="f6eda-105">コメント</span><span class="sxs-lookup"><span data-stu-id="f6eda-105">Remarks</span></span>  
 <span data-ttu-id="f6eda-106">`-noconfig`オプション Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルでコンパイルしていないコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="f6eda-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="f6eda-107">Vbc.rsp ファイルを参照して、一般的に使用される[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリとインポート、`System`と`Microsoft.VisualBasic`名前空間。</span><span class="sxs-lookup"><span data-stu-id="f6eda-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="f6eda-108">コンパイラは、System.dll アセンブリを暗黙的に参照しない限り、`-nostdlib`オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6eda-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="f6eda-109">`-nostdlib`オプションは、コンパイラが Vbc.rsp でコンパイルするか、System.dll アセンブリを自動的に参照を指定します。</span><span class="sxs-lookup"><span data-stu-id="f6eda-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6eda-110">Mscorlib.dll および Microsoft.VisualBasic.dll のアセンブリは、常に参照されます。</span><span class="sxs-lookup"><span data-stu-id="f6eda-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="f6eda-111">Vbc.exe のコンパイルごとに含める必要がある追加のコンパイラ オプションを指定する Vbc.rsp ファイルを変更することができます (を指定する場合を除いて、`-noconfig`オプション)。</span><span class="sxs-lookup"><span data-stu-id="f6eda-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="f6eda-112">詳しくは、「[@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f6eda-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="f6eda-113">コンパイラに渡されるオプションの処理、`vbc`最後コマンドします。</span><span class="sxs-lookup"><span data-stu-id="f6eda-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="f6eda-114">そのため、コマンドラインに指定したオプションは、Vbc.rsp ファイル内の同じオプションの設定を上書きします。</span><span class="sxs-lookup"><span data-stu-id="f6eda-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6eda-115">`-noconfig`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="f6eda-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6eda-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6eda-116">See Also</span></span>  
 [<span data-ttu-id="f6eda-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6eda-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [<span data-ttu-id="f6eda-118">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="f6eda-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f6eda-119">@ (応答ファイルの指定)</span><span class="sxs-lookup"><span data-stu-id="f6eda-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [<span data-ttu-id="f6eda-120">-参照 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6eda-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
