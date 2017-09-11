---
title: "方法 : Visual Studio のコマンドラインのための環境変数を設定する"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.commandline
dev_langs:
- CSharp
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
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 569683169c6d7ae50c33ed06d3b365a663f16715
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="d5dfb-102">方法 : Visual Studio のコマンドラインのための環境変数を設定する</span><span class="sxs-lookup"><span data-stu-id="d5dfb-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>
<span data-ttu-id="d5dfb-103">vcvars32.bat ファイルは、適切な環境変数を設定してコマンド ライン ビルドを有効にします。</span><span class="sxs-lookup"><span data-stu-id="d5dfb-103">The vsvars32.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="d5dfb-104">vsvars32.bat の詳細については、[サポート技術情報 Q248802](http://go.microsoft.com/fwlink/?LinkId=225042) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5dfb-104">For more information about vsvars32.bat, see [Knowledge Base article Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).</span></span>  
  
 <span data-ttu-id="d5dfb-105">以前のバージョンの Visual Studio と最新バージョンの Visual Studio の両方がコンピューターにインストールされている場合は、同じコマンド プロンプト ウィンドウから異なるバージョンの vsvars32.bat または vcvars32.bat を実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="d5dfb-105">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run vsvars32.bat or vcvars32.bat from different versions in the same Command Prompt window.</span></span>  
  
### <a name="to-run-vsvars32bat"></a><span data-ttu-id="d5dfb-106">VSVARS32.BAT を実行するには</span><span class="sxs-lookup"><span data-stu-id="d5dfb-106">To run VSVARS32.BAT</span></span>  
  
1.  <span data-ttu-id="d5dfb-107">**[スタート]** メニューから、**VS2012 の開発者コマンド プロンプト**を開きます。</span><span class="sxs-lookup"><span data-stu-id="d5dfb-107">From the **Start** menu, open the **Developer Command Prompt for VS2012**.</span></span>  
  
2.  <span data-ttu-id="d5dfb-108">インストールの Program Files\Microsoft Visual Studio *Version*\Common7\Tools または Program Files (x86)\Microsoft Visual Studio *Version*\Common7\Tools サブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="d5dfb-108">Change to the Program Files\Microsoft Visual Studio *Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio *Version*\Common7\Tools subdirectory of your installation.</span></span>  
  
3.  <span data-ttu-id="d5dfb-109">「**VSVARS32**」と入力して VSVARS32.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="d5dfb-109">Run VSVARS32.bat by typing **VSVARS32**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="d5dfb-110">VSVARS32.bat の場所は、コンピューターによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5dfb-110">VSVARS32.bat can vary from computer to computer.</span></span> <span data-ttu-id="d5dfb-111">VSVARS32.bat ファイルが見つからない場合や破損している場合でも、別のコンピューターの VSVARS32.bat と置き換えないでください。</span><span class="sxs-lookup"><span data-stu-id="d5dfb-111">Do not replace a missing or damaged VSVARS32.bat file with a VSVARS32.bat from another computer.</span></span> <span data-ttu-id="d5dfb-112">その場合は、セットアップ プログラムを再実行してファイルを置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="d5dfb-112">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5dfb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5dfb-113">See Also</span></span>  
 [<span data-ttu-id="d5dfb-114">csc.exe を使用したコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="d5dfb-114">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)

