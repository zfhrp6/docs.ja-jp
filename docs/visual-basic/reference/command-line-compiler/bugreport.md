---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 0383a5e369ee4a8146764c13b2f12f48ebe52190
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-bugreport"></a><span data-ttu-id="1d37a-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="1d37a-102">-bugreport</span></span>
<span data-ttu-id="1d37a-103">バグのレポートをファイルするときに使用できるファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d37a-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d37a-104">構文</span><span class="sxs-lookup"><span data-stu-id="1d37a-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d37a-105">引数</span><span class="sxs-lookup"><span data-stu-id="1d37a-105">Arguments</span></span>  
  
|<span data-ttu-id="1d37a-106">用語</span><span class="sxs-lookup"><span data-stu-id="1d37a-106">Term</span></span>|<span data-ttu-id="1d37a-107">定義</span><span class="sxs-lookup"><span data-stu-id="1d37a-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="1d37a-108">必須。</span><span class="sxs-lookup"><span data-stu-id="1d37a-108">Required.</span></span> <span data-ttu-id="1d37a-109">バグのレポートを格納するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="1d37a-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="1d37a-110">ファイル名を引用符で囲みます ("")、名前にスペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="1d37a-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d37a-111">コメント</span><span class="sxs-lookup"><span data-stu-id="1d37a-111">Remarks</span></span>  
 <span data-ttu-id="1d37a-112">次の情報に追加されます`file`:</span><span class="sxs-lookup"><span data-stu-id="1d37a-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="1d37a-113">コンパイルですべてのソース コード ファイルのコピー。</span><span class="sxs-lookup"><span data-stu-id="1d37a-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="1d37a-114">コンパイルで使用するコンパイラ オプションの一覧。</span><span class="sxs-lookup"><span data-stu-id="1d37a-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="1d37a-115">コンパイラ、共通言語ランタイム、およびオペレーティング システムのバージョン情報。</span><span class="sxs-lookup"><span data-stu-id="1d37a-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="1d37a-116">コンパイラの出力 (指定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="1d37a-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="1d37a-117">対象のされたら、問題の説明です。</span><span class="sxs-lookup"><span data-stu-id="1d37a-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="1d37a-118">問題を検討する方法の説明は修正する必要があります、するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1d37a-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="1d37a-119">すべてのソース コード ファイルのコピーが含まれているため`file`、できるだけ小さなプログラムに思われるコードの障害を再現することがあります。</span><span class="sxs-lookup"><span data-stu-id="1d37a-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d37a-120">`-bugreport`オプションは、機密性の高い情報を含むファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="1d37a-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="1d37a-121">これにより、現在の時刻、コンパイラのバージョンが含まれます。[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]バージョン、オペレーティング システムのバージョン、ユーザー名、コマンドライン引数を、コンパイラが実行された、すべてのソース コードでは、参照されるアセンブリのいずれかのバイナリ形式です。</span><span class="sxs-lookup"><span data-stu-id="1d37a-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="1d37a-122">このオプションは、Web.config ファイルのサーバー側のコンパイルでのコマンド ライン オプションを指定することによってアクセスできる、[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="1d37a-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="1d37a-123">これを回避するには、ユーザーがサーバーでのコンパイルが行われないよう、Machine.config ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="1d37a-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="1d37a-124">このオプションを使用する場合`-errorreport:prompt`、 `-errorreport:queue`、または`-errorreport:send`、アプリケーションでの情報は、内部コンパイラ エラーが発生して`file`がマイクロソフトに送信します。</span><span class="sxs-lookup"><span data-stu-id="1d37a-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="1d37a-125">その情報はマイクロソフトのエンジニアが、エラーの原因を特定し、Visual Basic の次回リリースの改善に役立てます。</span><span class="sxs-lookup"><span data-stu-id="1d37a-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="1d37a-126">既定では、Microsoft に情報は送信されません。</span><span class="sxs-lookup"><span data-stu-id="1d37a-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="1d37a-127">ただしを使用してアプリケーションをコンパイルするときに`-errorreport:queue`、既定で有効にする、アプリケーションがエラー レポートを収集します。</span><span class="sxs-lookup"><span data-stu-id="1d37a-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="1d37a-128">次に、コンピューターの管理者がログインすると、エラー レポート システムにより、管理者は、ログオン以降に発生したすべてのエラー レポートを Microsoft に転送するポップアップ ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d37a-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d37a-129">`/bugreport`オプションは、Visual Studio 開発環境からは利用できません。 使用可能なコマンドラインからコンパイルするときにのみです。</span><span class="sxs-lookup"><span data-stu-id="1d37a-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d37a-130">例</span><span class="sxs-lookup"><span data-stu-id="1d37a-130">Example</span></span>  
 <span data-ttu-id="1d37a-131">次の例をコンパイル`T2.vb`ファイルにバグ レポートのすべての情報を格納`Problem.txt`です。</span><span class="sxs-lookup"><span data-stu-id="1d37a-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d37a-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d37a-132">See Also</span></span>  
 [<span data-ttu-id="1d37a-133">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1d37a-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1d37a-134">デバッグ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d37a-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="1d37a-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="1d37a-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [<span data-ttu-id="1d37a-136">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="1d37a-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="1d37a-137">securityPolicy (ASP.NET 設定スキーマ) の trustLevel 要素</span><span class="sxs-lookup"><span data-stu-id="1d37a-137">trustLevel Element for securityPolicy (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
