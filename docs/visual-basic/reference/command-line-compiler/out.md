---
title: "/out (Visual Basic) |Microsoft ドキュメント"
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
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: 17
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
ms.openlocfilehash: 489a9015718a581c793cd1217ba073625929daf3
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="out-visual-basic"></a><span data-ttu-id="0b54e-102">/out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b54e-102">/out (Visual Basic)</span></span>
<span data-ttu-id="0b54e-103">出力ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0b54e-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b54e-104">構文</span><span class="sxs-lookup"><span data-stu-id="0b54e-104">Syntax</span></span>  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b54e-105">引数</span><span class="sxs-lookup"><span data-stu-id="0b54e-105">Arguments</span></span>  
  
|<span data-ttu-id="0b54e-106">用語</span><span class="sxs-lookup"><span data-stu-id="0b54e-106">Term</span></span>|<span data-ttu-id="0b54e-107">定義</span><span class="sxs-lookup"><span data-stu-id="0b54e-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="0b54e-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="0b54e-108">Required.</span></span> <span data-ttu-id="0b54e-109">コンパイラ出力ファイルの名前を作成します。</span><span class="sxs-lookup"><span data-stu-id="0b54e-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="0b54e-110">ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="0b54e-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b54e-111">コメント</span><span class="sxs-lookup"><span data-stu-id="0b54e-111">Remarks</span></span>  
 <span data-ttu-id="0b54e-112">完全な名前と作成するファイルの拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="0b54e-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="0b54e-113">.Exe ファイルを含むソース コード ファイルから名前を取得しないと場合、`Sub Main`手順、または .dll ファイルは、最初のソース コード ファイルからその名を取得します。</span><span class="sxs-lookup"><span data-stu-id="0b54e-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="0b54e-114">.Exe または .dll 拡張子を持たないファイル名を指定すると、コンパイラが自動的に追加、拡張機能に指定された値に応じて、`/target`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="0b54e-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `/target` compiler option.</span></span>  
  
|<span data-ttu-id="0b54e-115">統合開発環境を設定または Visual Studio で出力するには</span><span class="sxs-lookup"><span data-stu-id="0b54e-115">To set /out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0b54e-116">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="0b54e-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0b54e-117">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="0b54e-117">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="0b54e-118">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b54e-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="0b54e-119">2.**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0b54e-119">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="0b54e-120">3.値を変更、**アセンブリ名**ボックス。</span><span class="sxs-lookup"><span data-stu-id="0b54e-120">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b54e-121">例</span><span class="sxs-lookup"><span data-stu-id="0b54e-121">Example</span></span>  
 <span data-ttu-id="0b54e-122">次のコードのコンパイル`T2.vb`出力ファイルが作成および`T2.exe`です。</span><span class="sxs-lookup"><span data-stu-id="0b54e-122">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b54e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b54e-123">See Also</span></span>  
 <span data-ttu-id="0b54e-124">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0b54e-124">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0b54e-125"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="0b54e-125"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="0b54e-126"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="0b54e-126"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
