---
title: "/netcf |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
dev_langs:
- VB
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: 18
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
ms.openlocfilehash: 375ec79fe2bf63bc03988ecaad877eb27f43d55b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="netcf"></a><span data-ttu-id="f5c48-102">/netcf</span><span class="sxs-lookup"><span data-stu-id="f5c48-102">/netcf</span></span>
<span data-ttu-id="f5c48-103">[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] が対象になるようにコンパイラを設定します。</span><span class="sxs-lookup"><span data-stu-id="f5c48-103">Sets the compiler to target the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c48-104">構文</span><span class="sxs-lookup"><span data-stu-id="f5c48-104">Syntax</span></span>  
  
```  
/netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5c48-105">コメント</span><span class="sxs-lookup"><span data-stu-id="f5c48-105">Remarks</span></span>  
 <span data-ttu-id="f5c48-106">`/netcf`オプションにより、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ターゲットへのコンパイラ、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]完全ではなく[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f5c48-106">The `/netcf` option causes the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to target the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] rather than the full [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="f5c48-107">完全にのみ存在する言語機能[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]は無効になります。</span><span class="sxs-lookup"><span data-stu-id="f5c48-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="f5c48-108">`/netcf`オプションは、併用できるように設計されています。 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)します。</span><span class="sxs-lookup"><span data-stu-id="f5c48-108">The `/netcf` option is designed to be used with [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="f5c48-109">言語機能を無効にしています`/netcf`同一の言語機能を対象となるファイル内に存在しない`/sdkpath`します。</span><span class="sxs-lookup"><span data-stu-id="f5c48-109">The language features disabled by `/netcf` are the same language features not present in the files targeted with `/sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5c48-110">`/netcf`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="f5c48-110">The `/netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="f5c48-111">`/netcf`場合は、オプションが設定されて、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]デバイス プロジェクトが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f5c48-111">The `/netcf` option is set when a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="f5c48-112">`/netcf`オプションは、次の言語機能を変更します。</span><span class="sxs-lookup"><span data-stu-id="f5c48-112">The `/netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="f5c48-113">[エンド\<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)プログラムの実行を終了するには、キーワードが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="f5c48-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="f5c48-114">次のプログラムをコンパイルしても実行できる`/netcf`とコンパイル時に失敗したが、`/netcf`です。</span><span class="sxs-lookup"><span data-stu-id="f5c48-114">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     <span data-ttu-id="f5c48-115">[!code-vb[VbVbalrCompiler #&34;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f5c48-115">[!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]</span></span>  
  
-   <span data-ttu-id="f5c48-116">遅延バインディングするには、すべての形式が無効になります。</span><span class="sxs-lookup"><span data-stu-id="f5c48-116">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="f5c48-117">認識される遅延バインディングのシナリオが発生した場合に、コンパイル時エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f5c48-117">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="f5c48-118">次のプログラムをコンパイルしても実行できる`/netcf`とコンパイル時に失敗したが、`/netcf`です。</span><span class="sxs-lookup"><span data-stu-id="f5c48-118">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     <span data-ttu-id="f5c48-119">[!code-vb[VbVbalrCompiler&#35;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f5c48-119">[!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]</span></span>  
  
-   <span data-ttu-id="f5c48-120">[自動](../../../visual-basic/language-reference/modifiers/auto.md)、 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)、および[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾子が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="f5c48-120">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="f5c48-121">構文、[宣言ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)ステートメントが変更にも`Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`です。</span><span class="sxs-lookup"><span data-stu-id="f5c48-121">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="f5c48-122">次のコードは、の効果を示しています。`/netcf`によるコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f5c48-122">The following code shows the effect of `/netcf` on a compilation.</span></span>  
  
     <span data-ttu-id="f5c48-123">[!code-vb[VbVbalrCompiler&#36;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f5c48-123">[!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]</span></span>  
  
-   <span data-ttu-id="f5c48-124">削除された Visual Basic 6.0 キーワードを使用して[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、別のエラーが生成されますと`/netcf`を使用します。</span><span class="sxs-lookup"><span data-stu-id="f5c48-124">Using Visual Basic 6.0 keywords that were removed from [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] generates a different error when `/netcf` is used.</span></span> <span data-ttu-id="f5c48-125">これには、次のキーワードのエラー メッセージが影響します。</span><span class="sxs-lookup"><span data-stu-id="f5c48-125">This affects the error messages for the following keywords:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f5c48-126">例</span><span class="sxs-lookup"><span data-stu-id="f5c48-126">Example</span></span>  
 <span data-ttu-id="f5c48-127">次のコードのコンパイル`Myfile.vb`で、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]の既定のインストール ディレクトリで見つかった Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを使用して、 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] C ドライブにします。</span><span class="sxs-lookup"><span data-stu-id="f5c48-127">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] on the C drive.</span></span> <span data-ttu-id="f5c48-128">通常の最新バージョンを使用すると、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f5c48-128">Typically, you would use the most recent version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5c48-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5c48-129">See Also</span></span>  
 <span data-ttu-id="f5c48-130">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5c48-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="f5c48-131"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="f5c48-131"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="f5c48-132"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span><span class="sxs-lookup"><span data-stu-id="f5c48-132"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span></span>
