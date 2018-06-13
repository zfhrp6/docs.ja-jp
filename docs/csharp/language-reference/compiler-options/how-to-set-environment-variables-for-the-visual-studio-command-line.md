---
title: '方法 : Visual Studio のコマンドラインのための環境変数を設定する'
ms.date: 09/29/2017
f1_keywords:
- cs.build.commandline
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
ms.openlocfilehash: 0935cb62244691af7fa450fef9c1ab8f6c616579
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214992"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="5e42f-102">方法 : Visual Studio のコマンドラインのための環境変数を設定する</span><span class="sxs-lookup"><span data-stu-id="5e42f-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="5e42f-103">VsDevCmd.bat ファイルは、適切な環境変数を設定してコマンド ライン ビルドを有効にします。</span><span class="sxs-lookup"><span data-stu-id="5e42f-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="5e42f-104">VsDevCmd.bat の詳細については、[サポート技術情報 Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e42f-104">For more information about VsDevCmd.bat, see [Knowledge Base article Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).</span></span>  

> [!NOTE]
> <span data-ttu-id="5e42f-105">VsDevCmd.bat ファイルは、Visual Studio 2017 で提供される新しいファイルです。</span><span class="sxs-lookup"><span data-stu-id="5e42f-105">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="5e42f-106">Visual Studio 2015 とそれ以前のバージョンでは、同じ目的で VSVARS32.bat を使用しました。</span><span class="sxs-lookup"><span data-stu-id="5e42f-106">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="5e42f-107">このファイルは \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools または Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools に格納されていました。</span><span class="sxs-lookup"><span data-stu-id="5e42f-107">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="5e42f-108">以前のバージョンの Visual Studio と最新バージョンの Visual Studio の両方がコンピューターにインストールされている場合は、同じコマンド プロンプト ウィンドウから異なるバージョンの VsDevCmd.bat または VSVARS32.BAT を実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="5e42f-108">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="5e42f-109">代わりに、独自のウィンドウで、各バージョンのコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e42f-109">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="5e42f-110">VsDevCmd.BAT を実行するには</span><span class="sxs-lookup"><span data-stu-id="5e42f-110">To run VsDevCmd.BAT</span></span>  
  
1.  <span data-ttu-id="5e42f-111">**[スタート]** メニューから、**VS2017 の開発者コマンド プロンプト**を開きます。</span><span class="sxs-lookup"><span data-stu-id="5e42f-111">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="5e42f-112">これは、**[Visual Studio 2017]** フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="5e42f-112">It's in the **Visual Studio 2017** folder.</span></span>
  
2.  <span data-ttu-id="5e42f-113">インストールの \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools または \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools サブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="5e42f-113">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="5e42f-114">(*Version* は最新バージョンの *2017* です。</span><span class="sxs-lookup"><span data-stu-id="5e42f-114">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="5e42f-115">*Offering* は *Enterprise*、*Professional* または *Community* のいずれかです。)</span><span class="sxs-lookup"><span data-stu-id="5e42f-115">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3.  <span data-ttu-id="5e42f-116">「**VsDevCmd**」と入力して、VsDevCmd.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="5e42f-116">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="5e42f-117">VsDevCmd.bat の場所は、コンピューターによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5e42f-117">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="5e42f-118">VsDevCmd.bat ファイルが見つからない場合や破損している場合でも、別のコンピューターの VsDevCmd.bat と置き換えないでください。</span><span class="sxs-lookup"><span data-stu-id="5e42f-118">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="5e42f-119">その場合は、セットアップ プログラムを再実行してファイルを置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="5e42f-119">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e42f-120">参照</span><span class="sxs-lookup"><span data-stu-id="5e42f-120">See Also</span></span>  
 [<span data-ttu-id="5e42f-121">csc.exe を使用したコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="5e42f-121">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
