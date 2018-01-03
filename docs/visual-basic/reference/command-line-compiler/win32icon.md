---
title: /win32icon
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4fc5210d2dcf30d9c4603b67b890c78510af1338
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="win32icon"></a><span data-ttu-id="39c6f-102">/win32icon</span><span class="sxs-lookup"><span data-stu-id="39c6f-102">/win32icon</span></span>
<span data-ttu-id="39c6f-103">.Ico ファイルを出力ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="39c6f-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="39c6f-104">この .ico ファイルは出力ファイルを表す**ファイル エクスプ ローラー**です。</span><span class="sxs-lookup"><span data-stu-id="39c6f-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c6f-105">構文</span><span class="sxs-lookup"><span data-stu-id="39c6f-105">Syntax</span></span>  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="39c6f-106">引数</span><span class="sxs-lookup"><span data-stu-id="39c6f-106">Arguments</span></span>  
  
|<span data-ttu-id="39c6f-107">用語</span><span class="sxs-lookup"><span data-stu-id="39c6f-107">Term</span></span>|<span data-ttu-id="39c6f-108">定義</span><span class="sxs-lookup"><span data-stu-id="39c6f-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="39c6f-109">出力ファイルに追加する .ico ファイル。</span><span class="sxs-lookup"><span data-stu-id="39c6f-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="39c6f-110">ファイル名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="39c6f-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39c6f-111">コメント</span><span class="sxs-lookup"><span data-stu-id="39c6f-111">Remarks</span></span>  
 <span data-ttu-id="39c6f-112">.Ico ファイルは、Microsoft Windows リソース コンパイラ (RC) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="39c6f-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="39c6f-113">リソース コンパイラが、Visual C プログラムをコンパイルするときに呼び出されます.ico ファイルは .rc ファイルから作成されます。</span><span class="sxs-lookup"><span data-stu-id="39c6f-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="39c6f-114">`/win32icon`と`/win32resource`オプションは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="39c6f-114">The `/win32icon` and `/win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="39c6f-115">参照してください[/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)参照に、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リソース ファイル、または[/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)をアタッチする、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="39c6f-115">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="39c6f-116">参照してください[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res ファイルをインポートします。</span><span class="sxs-lookup"><span data-stu-id="39c6f-116">See [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="39c6f-117">Visual Studio IDE で/win32icon を設定するには</span><span class="sxs-lookup"><span data-stu-id="39c6f-117">To set /win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="39c6f-118">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="39c6f-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="39c6f-119">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39c6f-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="39c6f-120">2.**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="39c6f-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="39c6f-121">3.値を変更、**アイコン**ボックス。</span><span class="sxs-lookup"><span data-stu-id="39c6f-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39c6f-122">例</span><span class="sxs-lookup"><span data-stu-id="39c6f-122">Example</span></span>  
 <span data-ttu-id="39c6f-123">次のコードのコンパイル`In.vb`.ico ファイルをアタッチおよび`Rf.ico`です。</span><span class="sxs-lookup"><span data-stu-id="39c6f-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="39c6f-124">参照</span><span class="sxs-lookup"><span data-stu-id="39c6f-124">See Also</span></span>  
 [<span data-ttu-id="39c6f-125">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="39c6f-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="39c6f-126">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="39c6f-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
