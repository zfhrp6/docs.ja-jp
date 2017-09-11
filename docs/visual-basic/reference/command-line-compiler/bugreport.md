---
title: "/bugreport |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
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
ms.openlocfilehash: b959ef7958cffbbb31f3907eaf8749ca93ac538d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="bugreport"></a><span data-ttu-id="877c8-102">/bugreport</span><span class="sxs-lookup"><span data-stu-id="877c8-102">/bugreport</span></span>
<span data-ttu-id="877c8-103">バグのレポートをファイルするときに使用できるファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="877c8-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="877c8-104">構文</span><span class="sxs-lookup"><span data-stu-id="877c8-104">Syntax</span></span>  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="877c8-105">引数</span><span class="sxs-lookup"><span data-stu-id="877c8-105">Arguments</span></span>  
  
|<span data-ttu-id="877c8-106">用語</span><span class="sxs-lookup"><span data-stu-id="877c8-106">Term</span></span>|<span data-ttu-id="877c8-107">定義</span><span class="sxs-lookup"><span data-stu-id="877c8-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="877c8-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="877c8-108">Required.</span></span> <span data-ttu-id="877c8-109">バグのレポートを格納するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="877c8-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="877c8-110">ファイル名を引用符で囲みます ("") 名前にスペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="877c8-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="877c8-111">コメント</span><span class="sxs-lookup"><span data-stu-id="877c8-111">Remarks</span></span>  
 <span data-ttu-id="877c8-112">次の情報が追加`file`:</span><span class="sxs-lookup"><span data-stu-id="877c8-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="877c8-113">コンパイルですべてのソース コード ファイルのコピー。</span><span class="sxs-lookup"><span data-stu-id="877c8-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="877c8-114">コンパイル時に使用するコンパイラ オプションの一覧。</span><span class="sxs-lookup"><span data-stu-id="877c8-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="877c8-115">コンパイラ、共通言語ランタイム、およびオペレーティング システムのバージョン情報。</span><span class="sxs-lookup"><span data-stu-id="877c8-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="877c8-116">コンパイラが存在する場合に出力します。</span><span class="sxs-lookup"><span data-stu-id="877c8-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="877c8-117">対象が表示されたら、問題の説明です。</span><span class="sxs-lookup"><span data-stu-id="877c8-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="877c8-118">表示されたらどの問題を考えるの説明を修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="877c8-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="877c8-119">すべてのソース コード ファイルのコピーが含まれているため`file`、できるだけ小さなプログラムに思われるコード障害を再現することもできます。</span><span class="sxs-lookup"><span data-stu-id="877c8-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="877c8-120">`/bugreport`オプションには、重要な情報を含むファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="877c8-120">The `/bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="877c8-121">これにより、現在の時刻、コンパイラのバージョンが含まれます。[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]バージョン、オペレーティング システムのバージョン、ユーザー名、コマンドライン引数をコンパイラが実行されて、すべてのソース コードと参照アセンブリのいずれかのバイナリ形式です。</span><span class="sxs-lookup"><span data-stu-id="877c8-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="877c8-122">このオプションは、Web.config ファイルのサーバー側のコンパイルでのコマンド ライン オプションを指定することでアクセスできる、[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="877c8-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] application.</span></span> <span data-ttu-id="877c8-123">これを防ぐためには、ユーザーが、サーバーでのコンパイルが行われないよう、Machine.config ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="877c8-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="877c8-124">このオプションを使用する場合`/errorreport:prompt`、 `/errorreport:queue`、または`/errorreport:send`、アプリケーションでの情報は、内部コンパイラ エラーが発生して`file`はマイクロソフトに送信します。</span><span class="sxs-lookup"><span data-stu-id="877c8-124">If this option is used with `/errorreport:prompt`, `/errorreport:queue`, or `/errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="877c8-125">その情報がマイクロソフトのエンジニアが、エラーの原因の特定に役立つし、の次回のリリースを向上させるための[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="877c8-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="877c8-126">既定では、マイクロソフトに情報は送信されません。</span><span class="sxs-lookup"><span data-stu-id="877c8-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="877c8-127">ただしを使用してアプリケーションをコンパイルするときに`/errorreport:queue`、既定で有効にする、アプリケーションがエラー レポートを収集します。</span><span class="sxs-lookup"><span data-stu-id="877c8-127">However, when you compile an application by using `/errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="877c8-128">次に、コンピューターの管理者がログインすると、エラー レポート システム管理者がログオン以降に発生したすべてのエラー レポートをマイクロソフトに転送できるようにするポップアップ ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="877c8-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="877c8-129">`/bugreport`オプションは、Visual Studio 開発環境内から使用できません。 は、コマンドラインからコンパイルする場合のみです。</span><span class="sxs-lookup"><span data-stu-id="877c8-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="877c8-130">例</span><span class="sxs-lookup"><span data-stu-id="877c8-130">Example</span></span>  
 <span data-ttu-id="877c8-131">次の例をコンパイル`T2.vb`ファイルにすべてのバグのレポートの情報を格納`Problem.txt`します。</span><span class="sxs-lookup"><span data-stu-id="877c8-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="877c8-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="877c8-132">See Also</span></span>  
 <span data-ttu-id="877c8-133">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="877c8-133">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="877c8-134"> [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span><span class="sxs-lookup"><span data-stu-id="877c8-134"> [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span></span>  
<span data-ttu-id="877c8-135"> [/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md) </span><span class="sxs-lookup"><span data-stu-id="877c8-135"> [/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md) </span></span>  
<span data-ttu-id="877c8-136"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="877c8-136"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="877c8-137"> [(ASP.NET 設定スキーマ) securityPolicy の trustLevel 要素](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)</span><span class="sxs-lookup"><span data-stu-id="877c8-137"> [trustLevel Element for securityPolicy (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)</span></span>
