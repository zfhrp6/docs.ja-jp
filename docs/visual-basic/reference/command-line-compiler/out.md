---
title: /out (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d98a9f3cadc42021c302915cfc5b058b41e11ec6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="out-visual-basic"></a><span data-ttu-id="1b314-102">/out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b314-102">/out (Visual Basic)</span></span>
<span data-ttu-id="1b314-103">出力ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1b314-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b314-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b314-104">Syntax</span></span>  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="1b314-105">引数</span><span class="sxs-lookup"><span data-stu-id="1b314-105">Arguments</span></span>  
  
|<span data-ttu-id="1b314-106">用語</span><span class="sxs-lookup"><span data-stu-id="1b314-106">Term</span></span>|<span data-ttu-id="1b314-107">定義</span><span class="sxs-lookup"><span data-stu-id="1b314-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="1b314-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="1b314-108">Required.</span></span> <span data-ttu-id="1b314-109">コンパイラの出力ファイルの名前を作成します。</span><span class="sxs-lookup"><span data-stu-id="1b314-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="1b314-110">ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="1b314-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b314-111">コメント</span><span class="sxs-lookup"><span data-stu-id="1b314-111">Remarks</span></span>  
 <span data-ttu-id="1b314-112">完全な名前とを作成するファイルの拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="1b314-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="1b314-113">.Exe ファイルが、ソース コードを含むファイルから名前を取得しない場合、`Sub Main`プロシージャと .dll ファイルは、最初のソース コード ファイルの名前がします。</span><span class="sxs-lookup"><span data-stu-id="1b314-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="1b314-114">.Exe または .dll 拡張子を持たないファイル名を指定する場合、コンパイラ自動的に追加、拡張機能に指定された値によって、`/target`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="1b314-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `/target` compiler option.</span></span>  
  
|<span data-ttu-id="1b314-115">Visual Studio 統合開発環境で/out を設定するには</span><span class="sxs-lookup"><span data-stu-id="1b314-115">To set /out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1b314-116">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1b314-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1b314-117">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b314-117">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="1b314-118">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b314-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="1b314-119">2.**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b314-119">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="1b314-120">3.値を変更、**アセンブリ名**ボックス。</span><span class="sxs-lookup"><span data-stu-id="1b314-120">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1b314-121">例</span><span class="sxs-lookup"><span data-stu-id="1b314-121">Example</span></span>  
 <span data-ttu-id="1b314-122">次のコードのコンパイル`T2.vb`出力ファイルが作成および`T2.exe`です。</span><span class="sxs-lookup"><span data-stu-id="1b314-122">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b314-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b314-123">See Also</span></span>  
 [<span data-ttu-id="1b314-124">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1b314-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1b314-125">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b314-125">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="1b314-126">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="1b314-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
