---
title: "/libpath |Microsoft ドキュメント"
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
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
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
ms.openlocfilehash: 7f24dd7707645f45677dcf7009e1adc64afaaa7c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="libpath"></a><span data-ttu-id="b2462-102">/libpath</span><span class="sxs-lookup"><span data-stu-id="b2462-102">/libpath</span></span>
<span data-ttu-id="b2462-103">参照先アセンブリの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2462-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2462-104">構文</span><span class="sxs-lookup"><span data-stu-id="b2462-104">Syntax</span></span>  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="b2462-105">引数</span><span class="sxs-lookup"><span data-stu-id="b2462-105">Arguments</span></span>  
  
|<span data-ttu-id="b2462-106">用語</span><span class="sxs-lookup"><span data-stu-id="b2462-106">Term</span></span>|<span data-ttu-id="b2462-107">定義</span><span class="sxs-lookup"><span data-stu-id="b2462-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="b2462-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="b2462-108">Required.</span></span> <span data-ttu-id="b2462-109">コンパイラが参照先アセンブリを探す場合にディレクトリのセミコロン区切りのリストが見つからないいずれかで現在の作業ディレクトリ (コンパイラの起動元ディレクトリ) または共通言語ランタイムのシステム ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="b2462-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="b2462-110">ディレクトリ名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="b2462-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2462-111">コメント</span><span class="sxs-lookup"><span data-stu-id="b2462-111">Remarks</span></span>  
 <span data-ttu-id="b2462-112">`/libpath`オプションによって参照されるアセンブリの場所を指定する、 [/reference](../../../visual-basic/reference/command-line-compiler/reference.md)オプション。</span><span class="sxs-lookup"><span data-stu-id="b2462-112">The `/libpath` option specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="b2462-113">コンパイラは、次の順序で完全に修飾されていないアセンブリ参照を検索します。</span><span class="sxs-lookup"><span data-stu-id="b2462-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="b2462-114">現在の作業ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="b2462-114">Current working directory.</span></span> <span data-ttu-id="b2462-115">これは、コンパイラが呼び出されているディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="b2462-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="b2462-116">共通言語ランタイムのシステム ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="b2462-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="b2462-117">指定したディレクトリ`/libpath`します。</span><span class="sxs-lookup"><span data-stu-id="b2462-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="b2462-118">LIB 環境変数で指定したディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="b2462-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="b2462-119">`/libpath`オプションが加法; を指定するには、前の値に&1; 回追加よりも詳細です。</span><span class="sxs-lookup"><span data-stu-id="b2462-119">The `/libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="b2462-120">使用`/reference`アセンブリ参照を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2462-120">Use `/reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="b2462-121">統合開発環境 Visual Studio で/libpath を設定するには</span><span class="sxs-lookup"><span data-stu-id="b2462-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="b2462-122">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="b2462-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b2462-123">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="b2462-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="b2462-124">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2462-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="b2462-125">2.クリックして、**参照** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2462-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="b2462-126">3.クリックして、**パスを参照しています.**  ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2462-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="b2462-127">4.**参照パス** ダイアログ ボックスで、ディレクトリ名を入力、**フォルダー:**ボックス。</span><span class="sxs-lookup"><span data-stu-id="b2462-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="b2462-128">5.クリックして**フォルダーを追加する**です。</span><span class="sxs-lookup"><span data-stu-id="b2462-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b2462-129">例</span><span class="sxs-lookup"><span data-stu-id="b2462-129">Example</span></span>  
 <span data-ttu-id="b2462-130">次のコードのコンパイル`T2.vb`.exe ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2462-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="b2462-131">コンパイラは、アセンブリ参照の作業ディレクトリで、c: ドライブのルート ディレクトリ、および c: ドライブのアセンブリの新しいディレクトリを検索します。</span><span class="sxs-lookup"><span data-stu-id="b2462-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2462-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2462-132">See Also</span></span>  
 <span data-ttu-id="b2462-133">[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2462-133">[Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="b2462-134"> [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2462-134"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="b2462-135"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="b2462-135"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
