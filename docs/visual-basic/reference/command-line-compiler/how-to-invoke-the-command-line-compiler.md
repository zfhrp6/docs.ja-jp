---
title: '方法: コマンド ライン コンパイラを起動する (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1ccf08ba58fa6af60bd8ffd7cba79b205dc0f3d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="d91d2-102">方法: コマンド ライン コンパイラを起動する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d91d2-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="d91d2-103">コマンド ラインで、MS-DOS のプロンプトとも呼ばれるにその実行可能ファイルの名前を入力して、コマンド ライン コンパイラを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d91d2-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="d91d2-104">既定の Windows コマンド プロンプトからコンパイルする場合は、実行可能ファイルへの完全修飾パスを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d91d2-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="d91d2-105">この既定の動作をオーバーライドするを使用するか、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]コマンド プロンプト、または、PATH 環境変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="d91d2-105">To override this default behavior, you can either use the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt, or modify the PATH environment variable.</span></span> <span data-ttu-id="d91d2-106">コンパイラの名前を入力するだけで任意のディレクトリからコンパイルを両方ができます。</span><span class="sxs-lookup"><span data-stu-id="d91d2-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a><span data-ttu-id="d91d2-107">Visual Studio コマンド プロンプトを使用してコンパイラを起動するには</span><span class="sxs-lookup"><span data-stu-id="d91d2-107">To invoke the compiler using the Visual Studio Command Prompt</span></span>  
  
1.  <span data-ttu-id="d91d2-108">Microsoft Visual Studio プログラム グループ内の Visual Studio Tools プログラム フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="d91d2-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="d91d2-109">使用することができます、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]コマンド プロンプトを Visual Studio がインストールされている場合、コンピューター上の任意のディレクトリから、コンパイラにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d91d2-109">You can use the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="d91d2-110">呼び出す、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]コマンド プロンプトです。</span><span class="sxs-lookup"><span data-stu-id="d91d2-110">Invoke the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt.</span></span>  
  
4.  <span data-ttu-id="d91d2-111">コマンドラインで「 `vbc.exe` *sourceFileName*し、ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d91d2-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="d91d2-112">というディレクトリに、ソース コードを格納する場合など、 `SourceFiles`、するはプロンプトを開き、コマンド`cd SourceFiles`そのディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="d91d2-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="d91d2-113">ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルする`vbc.exe Source.vb`です。</span><span class="sxs-lookup"><span data-stu-id="d91d2-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="d91d2-114">Windows コマンド プロンプトをコンパイラに PATH 環境変数を設定するには</span><span class="sxs-lookup"><span data-stu-id="d91d2-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="d91d2-115">ローカル ディスクに Vbc.exe を検索するのにには、Windows 検索機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="d91d2-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="d91d2-116">コンパイラが配置されているディレクトリの正確な名前は、Windows ディレクトリの場所と、".NET Framework の"インストールされているバージョンに依存します。</span><span class="sxs-lookup"><span data-stu-id="d91d2-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="d91d2-117">1 つ以上の".NET Framework のバージョン"をインストールした場合 (通常は最新のバージョン) を使用するバージョンが判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d91d2-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="d91d2-118">**開始**メニューを右クリックして**マイ コンピューター**、順にクリック**プロパティ**ショートカット メニューからです。</span><span class="sxs-lookup"><span data-stu-id="d91d2-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="d91d2-119">クリックして、**詳細** タブをクリックして**環境変数**です。</span><span class="sxs-lookup"><span data-stu-id="d91d2-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="d91d2-120">**システム**変数ウィンドウで、**パス**クリックしてリストから**編集**です。</span><span class="sxs-lookup"><span data-stu-id="d91d2-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="d91d2-121">**編集システム**変数 ダイアログ ボックス、内の文字列の末尾にカーソルを移動、**変数値**フィールドで、セミコロン (;) を入力し、続けて手順 1. で検出された完全なディレクトリ名。</span><span class="sxs-lookup"><span data-stu-id="d91d2-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="d91d2-122">をクリックして**OK**を編集内容を確認し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d91d2-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="d91d2-123">PATH 環境変数を変更すると、後に実行できます Visual Basic コンパイラ、Windows コマンド プロンプトで任意のディレクトリから、コンピューター上。</span><span class="sxs-lookup"><span data-stu-id="d91d2-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="d91d2-124">Windows コマンド プロンプトを使用するコンパイラを起動するには</span><span class="sxs-lookup"><span data-stu-id="d91d2-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="d91d2-125">**開始** メニューをクリックして、**アクセサリ**フォルダーを開き、 **Windows コマンド プロンプト**です。</span><span class="sxs-lookup"><span data-stu-id="d91d2-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="d91d2-126">コマンドラインで「 `vbc.exe` *sourceFileName*し、ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d91d2-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="d91d2-127">というディレクトリに、ソース コードを格納する場合など、 `SourceFiles`、するはプロンプトを開き、コマンド`cd SourceFiles`そのディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="d91d2-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="d91d2-128">ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルする`vbc.exe Source.vb`です。</span><span class="sxs-lookup"><span data-stu-id="d91d2-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d91d2-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="d91d2-129">See Also</span></span>  
 [<span data-ttu-id="d91d2-130">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="d91d2-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d91d2-131">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="d91d2-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
