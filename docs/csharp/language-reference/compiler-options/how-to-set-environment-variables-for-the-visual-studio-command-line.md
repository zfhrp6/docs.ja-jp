---
title: "方法 : Visual Studio のコマンドラインのための環境変数を設定する"
ms.date: 09-29-2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8012e310bb04ec3acef0790f9cd50ed42dd9286a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="a2601-102">方法 : Visual Studio のコマンドラインのための環境変数を設定する</span><span class="sxs-lookup"><span data-stu-id="a2601-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="a2601-103">VsDevCmd.bat ファイルでは、コマンド ライン ビルドを有効にする適切な環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="a2601-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="a2601-104">VsDevCmd.bat の詳細については、次を参照してください。[サポート技術情報の記事 Q248802](http://go.microsoft.com/fwlink/?LinkId=225042)です。</span><span class="sxs-lookup"><span data-stu-id="a2601-104">For more information about VsDevCmd.bat, see [Knowledge Base article Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).</span></span>  

> [!NOTE]
> <span data-ttu-id="a2601-105">VsDevCmd.bat ファイルは、Visual Studio 2017 で提供される新しいファイルです。</span><span class="sxs-lookup"><span data-stu-id="a2601-105">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="a2601-106">Visual Studio 2015 と以前のバージョンは、VSVARS32.bat を同じ目的で使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2601-106">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="a2601-107">\Program Files\Microsoft Visual Studio でこのファイルが格納されている\\*バージョン*\Common7\Tools または Program Files (x86) \Microsoft Visual Studio\\*バージョン*\Common7\Tools です。</span><span class="sxs-lookup"><span data-stu-id="a2601-107">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="a2601-108">Visual Studio の現在のバージョンが Visual Studio の以前のバージョンは、コンピューターにインストールされている場合は、VsDevCmd.bat と VSVARS32 を実行する必要がありますされません。同じコマンド プロンプト ウィンドウで異なるバージョンの BAT です。</span><span class="sxs-lookup"><span data-stu-id="a2601-108">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="a2601-109">代わりに、独自のウィンドウで、各バージョンのコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2601-109">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="a2601-110">VsDevCmd.BAT を実行するには</span><span class="sxs-lookup"><span data-stu-id="a2601-110">To run VsDevCmd.BAT</span></span>  
  
1.  <span data-ttu-id="a2601-111">**開始**メニューを開き、 **VS 2017 用開発者コマンド プロンプト**です。</span><span class="sxs-lookup"><span data-stu-id="a2601-111">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="a2601-112">内にある、 **Visual Studio 2017**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="a2601-112">It's in the **Visual Studio 2017** folder.</span></span>
  
2.  <span data-ttu-id="a2601-113">\Program Files\Microsoft Visual Studio に変更\\*バージョン*\\*内容*\Common7\Tools または \Program Files (x86) \Microsoft Visual Studio\\*バージョン*\\*内容*インストールの \Common7\Tools サブディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="a2601-113">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="a2601-114">(*バージョン*は*2017*現在のバージョン。</span><span class="sxs-lookup"><span data-stu-id="a2601-114">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="a2601-115">*提供*の 1 つ*エンタープライズ*、 *Professional*または*コミュニティ*)。</span><span class="sxs-lookup"><span data-stu-id="a2601-115">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3.  <span data-ttu-id="a2601-116">VsDevCmd.bat を入力して実行**VsDevCmd**です。</span><span class="sxs-lookup"><span data-stu-id="a2601-116">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="a2601-117">VsDevCmd.bat には、コンピューターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="a2601-117">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="a2601-118">欠落または破損して VsDevCmd.bat ファイルを別のコンピューターから VsDevCmd.bat と置き換えないでください。</span><span class="sxs-lookup"><span data-stu-id="a2601-118">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="a2601-119">その場合は、セットアップ プログラムを再実行してファイルを置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="a2601-119">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2601-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2601-120">See Also</span></span>  
 [<span data-ttu-id="a2601-121">csc.exe を使用したコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="a2601-121">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
