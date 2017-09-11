---
title: "/optionexplicit |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
dev_langs:
- VB
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
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
ms.openlocfilehash: 3d2622c08b863233c8e1088bad252b37b3b38b04
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="optionexplicit"></a><span data-ttu-id="1d237-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="1d237-102">/optionexplicit</span></span>
<span data-ttu-id="1d237-103">使用されるように、変数が宣言されていない場合は、コンパイラがエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="1d237-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d237-104">構文</span><span class="sxs-lookup"><span data-stu-id="1d237-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d237-105">引数</span><span class="sxs-lookup"><span data-stu-id="1d237-105">Arguments</span></span>  
 <span data-ttu-id="1d237-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1d237-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="1d237-107">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1d237-107">Optional.</span></span> <span data-ttu-id="1d237-108">指定`/optionexplicit+`変数の明示的宣言を要求するようにします。</span><span class="sxs-lookup"><span data-stu-id="1d237-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="1d237-109">`/optionexplicit+`  オプションを選択し、既定値と同じ`/optionexplicit`します。</span><span class="sxs-lookup"><span data-stu-id="1d237-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="1d237-110">`/optionexplicit-`変数の暗黙の宣言を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1d237-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d237-111">コメント</span><span class="sxs-lookup"><span data-stu-id="1d237-111">Remarks</span></span>  
 <span data-ttu-id="1d237-112">ソース コード ファイルが含まれている場合、 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)、ステートメントのオーバーライド、`/optionexplicit`コマンド ライン コンパイラ設定します。</span><span class="sxs-lookup"><span data-stu-id="1d237-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="1d237-113">Visual Studio IDE で/optionexplicit を設定するには</span><span class="sxs-lookup"><span data-stu-id="1d237-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="1d237-114">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1d237-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1d237-115">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="1d237-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="1d237-116">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d237-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="1d237-117">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d237-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="1d237-118">値を変更、 **Option Explicit**ボックス。</span><span class="sxs-lookup"><span data-stu-id="1d237-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d237-119">例</span><span class="sxs-lookup"><span data-stu-id="1d237-119">Example</span></span>  
 <span data-ttu-id="1d237-120">次のコードをコンパイルとき`/optionexplicit-`を使用します。</span><span class="sxs-lookup"><span data-stu-id="1d237-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 <span data-ttu-id="1d237-121">[!code-vb[VbVbalrCompiler&#5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d237-121">[!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d237-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d237-122">See Also</span></span>  
 <span data-ttu-id="1d237-123">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="1d237-123">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="1d237-124"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="1d237-124"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="1d237-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="1d237-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="1d237-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="1d237-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="1d237-127"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="1d237-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="1d237-128"> [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1d237-128"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="1d237-129"> [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="1d237-129"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
