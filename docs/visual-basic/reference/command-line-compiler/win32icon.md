---
title: "/win32icon |Microsoft ドキュメント"
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
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
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
ms.openlocfilehash: f7d451026438be722d6cb7eecfffe397ccff82ae
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="win32icon"></a><span data-ttu-id="70955-102">/win32icon</span><span class="sxs-lookup"><span data-stu-id="70955-102">/win32icon</span></span>
<span data-ttu-id="70955-103">.Ico ファイルは、出力ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="70955-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="70955-104">この .ico ファイルに出力ファイルを表す**ファイル エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="70955-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70955-105">構文</span><span class="sxs-lookup"><span data-stu-id="70955-105">Syntax</span></span>  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="70955-106">引数</span><span class="sxs-lookup"><span data-stu-id="70955-106">Arguments</span></span>  
  
|<span data-ttu-id="70955-107">用語</span><span class="sxs-lookup"><span data-stu-id="70955-107">Term</span></span>|<span data-ttu-id="70955-108">定義</span><span class="sxs-lookup"><span data-stu-id="70955-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="70955-109">出力ファイルに追加する .ico ファイルです。</span><span class="sxs-lookup"><span data-stu-id="70955-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="70955-110">ファイル名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="70955-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70955-111">コメント</span><span class="sxs-lookup"><span data-stu-id="70955-111">Remarks</span></span>  
 <span data-ttu-id="70955-112">.Ico ファイルは、Microsoft Windows リソース コンパイラ (RC) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="70955-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="70955-113">Visual C プログラムをコンパイルするときに、リソース コンパイラが呼び出されます.ico ファイルは .rc ファイルから作成されます。</span><span class="sxs-lookup"><span data-stu-id="70955-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="70955-114">`/win32icon`と`/win32resource`オプションは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="70955-114">The `/win32icon` and `/win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="70955-115">参照してください[/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)参照に、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイルまたは[/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)をアタッチする、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="70955-115">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file.</span></span> <span data-ttu-id="70955-116">参照してください[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res ファイルをインポートします。</span><span class="sxs-lookup"><span data-stu-id="70955-116">See [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="70955-117">Visual Studio IDE で/win32icon を設定するには</span><span class="sxs-lookup"><span data-stu-id="70955-117">To set /win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="70955-118">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="70955-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="70955-119">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="70955-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="70955-120">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70955-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="70955-121">2.**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="70955-121">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="70955-122">3.値を変更、**アイコン**ボックス。</span><span class="sxs-lookup"><span data-stu-id="70955-122">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="70955-123">例</span><span class="sxs-lookup"><span data-stu-id="70955-123">Example</span></span>  
 <span data-ttu-id="70955-124">次のコードのコンパイル`In.vb`.ico ファイルをアタッチおよび`Rf.ico`です。</span><span class="sxs-lookup"><span data-stu-id="70955-124">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="70955-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="70955-125">See Also</span></span>  
 <span data-ttu-id="70955-126">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="70955-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="70955-127"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="70955-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
