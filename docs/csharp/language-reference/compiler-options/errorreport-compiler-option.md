---
title: "-errorreport (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: "35"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d2fcb3f0bf4491de23b70c8beebf7ae495b2aa0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="c5515-102">-errorreport (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="c5515-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="c5515-103">このオプションは、C# 内部コンパイラ エラーを Microsoft に報告する方法として便利です。</span><span class="sxs-lookup"><span data-stu-id="c5515-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5515-104">Windows Vista と Windows Server 2008 の場合、Windows エラー報告 (WER) 経由で行った設定が Visual Studio のエラー報告設定によって上書きされることはありません。</span><span class="sxs-lookup"><span data-stu-id="c5515-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="c5515-105">WER 設定は、常に Visual Studio のエラー報告設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="c5515-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5515-106">構文</span><span class="sxs-lookup"><span data-stu-id="c5515-106">Syntax</span></span>  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5515-107">引数</span><span class="sxs-lookup"><span data-stu-id="c5515-107">Arguments</span></span>  
 <span data-ttu-id="c5515-108">**none**</span><span class="sxs-lookup"><span data-stu-id="c5515-108">**none**</span></span>  
 <span data-ttu-id="c5515-109">内部コンパイラ エラーに関するレポートは、収集されず、マイクロソフトに送信されません。</span><span class="sxs-lookup"><span data-stu-id="c5515-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>  
  
 <span data-ttu-id="c5515-110">**prompt**</span><span class="sxs-lookup"><span data-stu-id="c5515-110">**prompt**</span></span>  
 <span data-ttu-id="c5515-111">内部コンパイラ エラーを受信したときにレポートを送信するかどうか確認するメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="c5515-111">Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="c5515-112">**prompt** は、開発環境でアプリケーションをコンパイルする場合の既定値です。</span><span class="sxs-lookup"><span data-stu-id="c5515-112">**prompt** is the default when you compile an application in the development environment.</span></span>  
  
 <span data-ttu-id="c5515-113">**queue**</span><span class="sxs-lookup"><span data-stu-id="c5515-113">**queue**</span></span>  
 <span data-ttu-id="c5515-114">エラー レポートを待ち行列に入れます。</span><span class="sxs-lookup"><span data-stu-id="c5515-114">Queues the error report.</span></span> <span data-ttu-id="c5515-115">管理者資格情報でログオンすると、前回のログオン以降に発生したすべてのエラーを報告できます。</span><span class="sxs-lookup"><span data-stu-id="c5515-115">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="c5515-116">エラー レポートを送信するためのダイアログ ボックスが表示されるのは、3 日に一度だけです。</span><span class="sxs-lookup"><span data-stu-id="c5515-116">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="c5515-117">**queue** は、コマンド ラインでアプリケーションをコンパイルする場合の既定値です。</span><span class="sxs-lookup"><span data-stu-id="c5515-117">**queue** is the default when you compile an application at the command line.</span></span>  
  
 <span data-ttu-id="c5515-118">**send**</span><span class="sxs-lookup"><span data-stu-id="c5515-118">**send**</span></span>  
 <span data-ttu-id="c5515-119">内部コンパイラ エラーのレポートをマイクロソフトに自動的に送信します。</span><span class="sxs-lookup"><span data-stu-id="c5515-119">Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="c5515-120">このオプションを有効にするには、まずマイクロソフトのデータ収集ポリシーに同意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5515-120">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="c5515-121">コンピューターで **-errorreport:send** を初めて指定すると、マイクロソフトのデータ収集ポリシーが記載されている Web サイトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5515-121">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>  
    
## <a name="remarks"></a><span data-ttu-id="c5515-122">コメント</span><span class="sxs-lookup"><span data-stu-id="c5515-122">Remarks</span></span>  
 <span data-ttu-id="c5515-123">コンパイラがソース コード ファイルを処理できないと、内部コンパイラ エラー (ICE: Internal Compiler Error) が発生します。</span><span class="sxs-lookup"><span data-stu-id="c5515-123">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="c5515-124">ICE が発生した場合、コードの修正に利用できる出力ファイルや診断は生成されません。</span><span class="sxs-lookup"><span data-stu-id="c5515-124">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>  
  
 <span data-ttu-id="c5515-125">以前のリリースでは、ICE が発生した場合、マイクロソフト製品サポート サービスに連絡して問題を報告することを推奨していました。</span><span class="sxs-lookup"><span data-stu-id="c5515-125">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="c5515-126">**-errorreport** を使用すると、ICE 情報を Visual C# チームに提供できます。</span><span class="sxs-lookup"><span data-stu-id="c5515-126">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="c5515-127">エラー レポートは、今後リリースされるコンパイラの機能向上に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c5515-127">Your error reports can help improve future compiler releases.</span></span>  
  
 <span data-ttu-id="c5515-128">コンピューターまたはユーザー ポリシーによるアクセス許可によっては、レポートを送信できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5515-128">A user's ability to send reports depends on computer and user policy permissions.</span></span>  
  
 <span data-ttu-id="c5515-129">エラー デバッガーの詳細については、「[Windows のワトソン博士 (Drwtsn32.exe) ツールについて](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5515-129">For more information about error debugger, see [Description of the Dr. Watson for Windows (Drwtsn32.exe) Tool](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c5515-130">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="c5515-130">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c5515-131">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="c5515-131">Open the project's **Properties** page.</span></span> <span data-ttu-id="c5515-132">詳細については、「[Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)」([ビルド] ページ (プロジェクト デザイナー) (C#)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5515-132">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="c5515-133">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5515-133">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="c5515-134">**[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5515-134">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="c5515-135">**[内部コンパイル エラー報告]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="c5515-135">Modify the **Internal Compiler Error Reporting** property.</span></span>  
  
 <span data-ttu-id="c5515-136">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5515-136">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5515-137">参照</span><span class="sxs-lookup"><span data-stu-id="c5515-137">See Also</span></span>  
 [<span data-ttu-id="c5515-138">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="c5515-138">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
