---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e701addb31b361e55f2761f441c23deaef7c10d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="optionexplicit"></a><span data-ttu-id="20fb7-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="20fb7-102">/optionexplicit</span></span>
<span data-ttu-id="20fb7-103">変数が使用されるように宣言されていない場合は、コンパイラがエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="20fb7-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20fb7-104">構文</span><span class="sxs-lookup"><span data-stu-id="20fb7-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="20fb7-105">引数</span><span class="sxs-lookup"><span data-stu-id="20fb7-105">Arguments</span></span>  
 <span data-ttu-id="20fb7-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="20fb7-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="20fb7-107">任意。</span><span class="sxs-lookup"><span data-stu-id="20fb7-107">Optional.</span></span> <span data-ttu-id="20fb7-108">指定`/optionexplicit+`変数の明示的な宣言を要求するようにします。</span><span class="sxs-lookup"><span data-stu-id="20fb7-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="20fb7-109">`/optionexplicit+`オプションは、既定値と同じとして`/optionexplicit`です。</span><span class="sxs-lookup"><span data-stu-id="20fb7-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="20fb7-110">`/optionexplicit-`変数の暗黙の宣言を有効にします。</span><span class="sxs-lookup"><span data-stu-id="20fb7-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20fb7-111">コメント</span><span class="sxs-lookup"><span data-stu-id="20fb7-111">Remarks</span></span>  
 <span data-ttu-id="20fb7-112">ソース コード ファイルが含まれている場合、 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)、ステートメントよりも優先、`/optionexplicit`コマンド ライン コンパイラ設定します。</span><span class="sxs-lookup"><span data-stu-id="20fb7-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="20fb7-113">Visual Studio IDE で/optionexplicit を設定するには</span><span class="sxs-lookup"><span data-stu-id="20fb7-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="20fb7-114">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="20fb7-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="20fb7-115">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="20fb7-115">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="20fb7-116">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="20fb7-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="20fb7-117">値を変更、 **Option Explicit**ボックス。</span><span class="sxs-lookup"><span data-stu-id="20fb7-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20fb7-118">例</span><span class="sxs-lookup"><span data-stu-id="20fb7-118">Example</span></span>  
 <span data-ttu-id="20fb7-119">次のコードをコンパイル時に`/optionexplicit-`を使用します。</span><span class="sxs-lookup"><span data-stu-id="20fb7-119">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="20fb7-120">参照</span><span class="sxs-lookup"><span data-stu-id="20fb7-120">See Also</span></span>  
 [<span data-ttu-id="20fb7-121">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="20fb7-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="20fb7-122">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="20fb7-122">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="20fb7-123">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="20fb7-123">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="20fb7-124">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="20fb7-124">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="20fb7-125">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="20fb7-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="20fb7-126">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="20fb7-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 <span data-ttu-id="20fb7-127">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="20fb7-127">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
