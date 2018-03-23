---
title: -除外 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cc3779f9efda8cf48107a7c16e31f8ff05a456d
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-out-visual-basic"></a><span data-ttu-id="63f83-102">-除外 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63f83-102">-out (Visual Basic)</span></span>
<span data-ttu-id="63f83-103">出力ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="63f83-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f83-104">構文</span><span class="sxs-lookup"><span data-stu-id="63f83-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="63f83-105">引数</span><span class="sxs-lookup"><span data-stu-id="63f83-105">Arguments</span></span>  
  
|<span data-ttu-id="63f83-106">用語</span><span class="sxs-lookup"><span data-stu-id="63f83-106">Term</span></span>|<span data-ttu-id="63f83-107">定義</span><span class="sxs-lookup"><span data-stu-id="63f83-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="63f83-108">必須。</span><span class="sxs-lookup"><span data-stu-id="63f83-108">Required.</span></span> <span data-ttu-id="63f83-109">コンパイラの出力ファイルの名前を作成します。</span><span class="sxs-lookup"><span data-stu-id="63f83-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="63f83-110">ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="63f83-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63f83-111">コメント</span><span class="sxs-lookup"><span data-stu-id="63f83-111">Remarks</span></span>  
 <span data-ttu-id="63f83-112">完全な名前とを作成するファイルの拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="63f83-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="63f83-113">.Exe ファイルが、ソース コードを含むファイルから名前を取得しない場合、`Sub Main`プロシージャと .dll ファイルは、最初のソース コード ファイルの名前がします。</span><span class="sxs-lookup"><span data-stu-id="63f83-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="63f83-114">.Exe または .dll 拡張子を持たないファイル名を指定する場合、コンパイラ自動的に追加、拡張機能に指定された値によって、`-target`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="63f83-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="63f83-115">設定するを Visual Studio 統合開発環境</span><span class="sxs-lookup"><span data-stu-id="63f83-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="63f83-116">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="63f83-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="63f83-117">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63f83-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="63f83-118">2.**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="63f83-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="63f83-119">3.値を変更、**アセンブリ名**ボックス。</span><span class="sxs-lookup"><span data-stu-id="63f83-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="63f83-120">例</span><span class="sxs-lookup"><span data-stu-id="63f83-120">Example</span></span>  
 <span data-ttu-id="63f83-121">次のコードのコンパイル`T2.vb`出力ファイルが作成および`T2.exe`です。</span><span class="sxs-lookup"><span data-stu-id="63f83-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="63f83-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="63f83-122">See Also</span></span>  
 [<span data-ttu-id="63f83-123">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="63f83-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="63f83-124">-ターゲット (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63f83-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="63f83-125">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="63f83-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
