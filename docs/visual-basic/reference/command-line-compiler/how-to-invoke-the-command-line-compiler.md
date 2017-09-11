---
title: "方法: コマンド ライン コンパイラ (Visual Basic) を起動 |Microsoft ドキュメント"
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
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line, arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
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
ms.openlocfilehash: e19bb506b016b774d2c497f8b17d91b35afb3eef
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="a3765-102">方法: コマンド ライン コンパイラを起動する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3765-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="a3765-103">コマンド ラインで、MS-DOS プロンプトとも呼ばれますにその実行可能ファイルの名前を入力して、コマンド ライン コンパイラを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a3765-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="a3765-104">既定の Windows コマンド プロンプトからコンパイルする場合は、実行可能ファイルへの完全修飾パスを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3765-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="a3765-105">この既定の動作をオーバーライドする使用するか、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]コマンド プロンプト、または PATH 環境変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="a3765-105">To override this default behavior, you can either use the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] Command Prompt, or modify the PATH environment variable.</span></span> <span data-ttu-id="a3765-106">コンパイラの名前を入力するだけで任意のディレクトリからコンパイルをどちらもができます。</span><span class="sxs-lookup"><span data-stu-id="a3765-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a><span data-ttu-id="a3765-107">Visual Studio コマンド プロンプトを使用するコンパイラを起動するには</span><span class="sxs-lookup"><span data-stu-id="a3765-107">To invoke the compiler using the Visual Studio Command Prompt</span></span>  
  
1.  <span data-ttu-id="a3765-108">Microsoft Visual Studio のプログラム グループ内の Visual Studio Tools プログラム フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="a3765-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="a3765-109">使用することができます、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]コマンド プロンプトは、Visual Studio がインストールされている場合、コンピューター上の任意のディレクトリから、コンパイラにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="a3765-109">You can use the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] Command Prompt to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="a3765-110">呼び出す、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]コマンド プロンプト。</span><span class="sxs-lookup"><span data-stu-id="a3765-110">Invoke the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] Command Prompt.</span></span>  
  
4.  <span data-ttu-id="a3765-111">コマンドラインで「 `vbc.exe` *sourceFileName* ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a3765-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="a3765-112">という名前のディレクトリにソース コードを格納する場合など`SourceFiles`、コマンド プロンプトと型が開きます`cd SourceFiles`そのディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="a3765-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="a3765-113">ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルすることが`vbc.exe Source.vb`です。</span><span class="sxs-lookup"><span data-stu-id="a3765-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="a3765-114">Windows コマンド プロンプトをコンパイラに PATH 環境変数を設定するには</span><span class="sxs-lookup"><span data-stu-id="a3765-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="a3765-115">Windows Search の機能を使用して、ローカル ハード_ディスク上の Vbc.exe を検索します。</span><span class="sxs-lookup"><span data-stu-id="a3765-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="a3765-116">コンパイラがあるディレクトリの正確な名前の Windows ディレクトリの場所とのバージョンによって異なる、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a3765-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] installed.</span></span> <span data-ttu-id="a3765-117">複数のバージョンがインストールされている場合、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]インストールされている、(通常は最新のバージョン) を使用するバージョンを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3765-117">If you have more than one version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="a3765-118">**開始** メニューの を右クリックして**マイ コンピューター**、 をクリックし、**プロパティ**のショートカット メニュー。</span><span class="sxs-lookup"><span data-stu-id="a3765-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="a3765-119">クリックして、**詳細**タブをクリックし、をクリックして**環境変数**します。</span><span class="sxs-lookup"><span data-stu-id="a3765-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="a3765-120">**システム**変数ウィンドウで、**パス**、リストをクリックしてから**編集**します。</span><span class="sxs-lookup"><span data-stu-id="a3765-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="a3765-121">**編集システム**変数 ダイアログ ボックス内の文字列の末尾にカーソルを移動、**変数値**フィールドで、セミコロン (;) を入力し、続けて手順 1. で検出された完全なディレクトリ名です。</span><span class="sxs-lookup"><span data-stu-id="a3765-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="a3765-122">クリックして**OK**を編集内容を確認し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a3765-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="a3765-123">実行することができます、PATH 環境変数を変更した後、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラ、Windows コマンド プロンプトで、コンピューター上の任意のディレクトリからです。</span><span class="sxs-lookup"><span data-stu-id="a3765-123">After you change the PATH environment variable, you can run the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="a3765-124">Windows コマンド プロンプトを使用してコンパイラを起動するには</span><span class="sxs-lookup"><span data-stu-id="a3765-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="a3765-125">**開始**メニューをクリックして、**アクセサリ**フォルダー、およびを開きます、 **Windows コマンド プロンプト**します。</span><span class="sxs-lookup"><span data-stu-id="a3765-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="a3765-126">コマンドラインで「 `vbc.exe` *sourceFileName* ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a3765-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="a3765-127">という名前のディレクトリにソース コードを格納する場合など`SourceFiles`、コマンド プロンプトと型が開きます`cd SourceFiles`そのディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="a3765-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="a3765-128">ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルすることが`vbc.exe Source.vb`です。</span><span class="sxs-lookup"><span data-stu-id="a3765-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3765-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3765-129">See Also</span></span>  
 <span data-ttu-id="a3765-130">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="a3765-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="a3765-131"> [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span><span class="sxs-lookup"><span data-stu-id="a3765-131"> [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span></span>
