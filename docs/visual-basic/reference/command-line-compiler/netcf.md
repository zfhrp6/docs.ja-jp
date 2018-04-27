---
title: -netcf
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f07fc7988c4329397e464f05d334648e98cb129d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="-netcf"></a><span data-ttu-id="dc35b-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="dc35b-102">-netcf</span></span>
<span data-ttu-id="dc35b-103">[!INCLUDE[Compact](~/includes/compact-md.md)] が対象になるようにコンパイラを設定します。</span><span class="sxs-lookup"><span data-stu-id="dc35b-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc35b-104">構文</span><span class="sxs-lookup"><span data-stu-id="dc35b-104">Syntax</span></span>  
  
```  
-netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="dc35b-105">コメント</span><span class="sxs-lookup"><span data-stu-id="dc35b-105">Remarks</span></span>  
 <span data-ttu-id="dc35b-106">`-netcf`オプションは、ターゲットに Visual Basic コンパイラ、[!INCLUDE[Compact](~/includes/compact-md.md)]完全ではなく[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="dc35b-106">The `-netcf` option causes the Visual Basic compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="dc35b-107">言語機能は完全にのみ存在する[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]は無効になります。</span><span class="sxs-lookup"><span data-stu-id="dc35b-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="dc35b-108">`-netcf`オプションで使用するように設計された[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)です。</span><span class="sxs-lookup"><span data-stu-id="dc35b-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="dc35b-109">無効になっている言語機能`-netcf`、同じ言語機能を対象となるファイル内に存在しない`-sdkpath`です。</span><span class="sxs-lookup"><span data-stu-id="dc35b-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc35b-110">`-netcf`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="dc35b-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="dc35b-111">`-netcf` Visual Basic プロジェクトのデバイスが読み込まれるときに、オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="dc35b-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="dc35b-112">`-netcf`オプションは次の言語機能を変更します。</span><span class="sxs-lookup"><span data-stu-id="dc35b-112">The `-netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="dc35b-113">[終了\<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)プログラムの実行を終了するには、キーワードが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="dc35b-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="dc35b-114">次のプログラムをコンパイルしてなしで実行されます`-netcf`はコンパイル時に失敗した`-netcf`です。</span><span class="sxs-lookup"><span data-stu-id="dc35b-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   <span data-ttu-id="dc35b-115">遅延バインディングするには、すべての形式が無効です。</span><span class="sxs-lookup"><span data-stu-id="dc35b-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="dc35b-116">認識された遅延バインディングのシナリオが発生した場合に、コンパイル時エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="dc35b-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="dc35b-117">次のプログラムをコンパイルしてなしで実行されます`-netcf`はコンパイル時に失敗した`-netcf`です。</span><span class="sxs-lookup"><span data-stu-id="dc35b-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   <span data-ttu-id="dc35b-118">[自動](../../../visual-basic/language-reference/modifiers/auto.md)、 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)、および[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾子が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="dc35b-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="dc35b-119">構文、 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)ステートメントが変更にも`Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`します。</span><span class="sxs-lookup"><span data-stu-id="dc35b-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="dc35b-120">次のコードは、の効果を示しています。 `-netcf` 、コンパイル時にします。</span><span class="sxs-lookup"><span data-stu-id="dc35b-120">The following code shows the effect of `-netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   <span data-ttu-id="dc35b-121">Visual Basic から削除された Visual Basic 6.0 のキーワードを使用して、別のエラーが生成されるとき`-netcf`を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc35b-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="dc35b-122">これには、次のキーワードのエラー メッセージに影響します。</span><span class="sxs-lookup"><span data-stu-id="dc35b-122">This affects the error messages for the following keywords:</span></span>  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a><span data-ttu-id="dc35b-123">例</span><span class="sxs-lookup"><span data-stu-id="dc35b-123">Example</span></span>  
 <span data-ttu-id="dc35b-124">次のコードのコンパイル`Myfile.vb`で、[!INCLUDE[Compact](~/includes/compact-md.md)]の既定のインストール ディレクトリで見つかった mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを使用して、[!INCLUDE[Compact](~/includes/compact-md.md)]が C ドライブにします。</span><span class="sxs-lookup"><span data-stu-id="dc35b-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="dc35b-125">通常の最新バージョンを使用すると、[!INCLUDE[Compact](~/includes/compact-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="dc35b-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc35b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc35b-126">See Also</span></span>  
 [<span data-ttu-id="dc35b-127">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="dc35b-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="dc35b-128">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="dc35b-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="dc35b-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="dc35b-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
