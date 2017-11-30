---
title: /libpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2be2c460fddf2e8ea4fe1239ec073f208c072d34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="libpath"></a><span data-ttu-id="ae854-102">/libpath</span><span class="sxs-lookup"><span data-stu-id="ae854-102">/libpath</span></span>
<span data-ttu-id="ae854-103">参照先アセンブリの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="ae854-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae854-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae854-104">Syntax</span></span>  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae854-105">引数</span><span class="sxs-lookup"><span data-stu-id="ae854-105">Arguments</span></span>  
  
|<span data-ttu-id="ae854-106">用語</span><span class="sxs-lookup"><span data-stu-id="ae854-106">Term</span></span>|<span data-ttu-id="ae854-107">定義</span><span class="sxs-lookup"><span data-stu-id="ae854-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="ae854-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="ae854-108">Required.</span></span> <span data-ttu-id="ae854-109">コンパイラが参照先アセンブリを探す場合にディレクトリのセミコロン区切りのリストに載っていないいずれかの現在の作業ディレクトリ (コンパイラの起動元のディレクトリ)、または共通言語ランタイムのシステム ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="ae854-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="ae854-110">ディレクトリ名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="ae854-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae854-111">コメント</span><span class="sxs-lookup"><span data-stu-id="ae854-111">Remarks</span></span>  
 <span data-ttu-id="ae854-112">`/libpath`オプションによって参照されるアセンブリの場所を指定する、 [/reference](../../../visual-basic/reference/command-line-compiler/reference.md)オプション。</span><span class="sxs-lookup"><span data-stu-id="ae854-112">The `/libpath` option specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="ae854-113">コンパイラは、完全に修飾されていないアセンブリ参照を次の順序で検索します。</span><span class="sxs-lookup"><span data-stu-id="ae854-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="ae854-114">現在の作業ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="ae854-114">Current working directory.</span></span> <span data-ttu-id="ae854-115">これは、コンパイラを起動したディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="ae854-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="ae854-116">共通言語ランタイムのシステム ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="ae854-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="ae854-117">指定したディレクトリ`/libpath`です。</span><span class="sxs-lookup"><span data-stu-id="ae854-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="ae854-118">LIB 環境変数によって指定されているディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="ae854-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="ae854-119">`/libpath`オプションが加法; 指定するには、複数の前の値に 1 回追加します。</span><span class="sxs-lookup"><span data-stu-id="ae854-119">The `/libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="ae854-120">使用して`/reference`アセンブリ参照を指定します。</span><span class="sxs-lookup"><span data-stu-id="ae854-120">Use `/reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="ae854-121">Visual Studio で/libpath を設定するには、統合開発環境</span><span class="sxs-lookup"><span data-stu-id="ae854-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ae854-122">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="ae854-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ae854-123">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae854-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="ae854-124">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae854-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="ae854-125">2.**[参照]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae854-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="ae854-126">3.クリックして、**パスを参照しています.**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae854-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="ae854-127">4.**参照パス** ダイアログ ボックスで、ディレクトリ名を入力、**フォルダー:**ボックス。</span><span class="sxs-lookup"><span data-stu-id="ae854-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="ae854-128">5.をクリックして**フォルダーの追加**です。</span><span class="sxs-lookup"><span data-stu-id="ae854-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae854-129">例</span><span class="sxs-lookup"><span data-stu-id="ae854-129">Example</span></span>  
 <span data-ttu-id="ae854-130">次のコードのコンパイル`T2.vb`.exe ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ae854-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="ae854-131">コンパイラは、アセンブリ参照の作業ディレクトリに、c: ドライブのルート ディレクトリ、および c: ドライブのアセンブリを新しいディレクトリに検索します。</span><span class="sxs-lookup"><span data-stu-id="ae854-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae854-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae854-132">See Also</span></span>  
 [<span data-ttu-id="ae854-133">アセンブリとグローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="ae854-133">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="ae854-134">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="ae854-134">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ae854-135">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="ae854-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
