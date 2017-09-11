---
title: "Option Explicit ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
dev_langs:
- VB
helpviewer_keywords:
- declaring variables, explicit
- forced variable declaration in Option Explicit statement
- Explicit keyword
- explicit variable declaration
- Option Explicit statement
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
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
ms.openlocfilehash: 4283599d9ed2ad9075ab0b2f404f1a12a31437ec
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="3b96c-102">Option Explicit ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b96c-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="3b96c-103">強制的に、ファイルのすべての変数を明示的に宣言または変数の暗黙の宣言を許可します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b96c-104">構文</span><span class="sxs-lookup"><span data-stu-id="3b96c-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="3b96c-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="3b96c-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="3b96c-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3b96c-106">Optional.</span></span> <span data-ttu-id="3b96c-107">により、`Option Explicit`をチェックします。</span><span class="sxs-lookup"><span data-stu-id="3b96c-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="3b96c-108">場合`On`または`Off`が指定されていない、既定値は`On`です。</span><span class="sxs-lookup"><span data-stu-id="3b96c-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="3b96c-109">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3b96c-109">Optional.</span></span> <span data-ttu-id="3b96c-110">無効に`Option Explicit`をチェックします。</span><span class="sxs-lookup"><span data-stu-id="3b96c-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b96c-111">コメント</span><span class="sxs-lookup"><span data-stu-id="3b96c-111">Remarks</span></span>  
 <span data-ttu-id="3b96c-112">`Option Explicit On`または`Option Explicit`を使用してすべての変数を明示的に宣言する必要がありますが、ファイルに表示されます、`Dim`または`ReDim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="3b96c-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="3b96c-113">宣言されていない変数名を使用しようとする場合は、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="3b96c-114">`Option Explicit Off`ステートメントでは、変数の暗黙の宣言を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b96c-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="3b96c-115">使用した場合、`Option Explicit` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b96c-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b96c-116">設定`Option Explicit`に`Off`は一般にないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3b96c-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="3b96c-117">プログラムの実行時に予期しない結果になる&1; つまたは複数の場所で、変数名のスペルを間違えた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3b96c-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="3b96c-118">Option Explicit ステートメントが存在しない場合</span><span class="sxs-lookup"><span data-stu-id="3b96c-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="3b96c-119">ソース コードが含まれていない場合、`Option Explicit`ステートメント、 **Option Explicit**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="3b96c-120">コマンド ライン コンパイラを使用する場合、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="3b96c-121">IDE で Option explicit ステートメントを設定するには</span><span class="sxs-lookup"><span data-stu-id="3b96c-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="3b96c-122">**ソリューション エクスプ ローラー**プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="3b96c-123">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="3b96c-124">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b96c-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="3b96c-125">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b96c-125">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="3b96c-126">値を設定、 **Option Explicit**ボックス。</span><span class="sxs-lookup"><span data-stu-id="3b96c-126">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="3b96c-127">新しいプロジェクトを作成するときに、 **Option Explicit**の設定、**コンパイル**に設定されているタブ、 **Option Explicit**で設定、 **VB の既定値** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="3b96c-127">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="3b96c-128">アクセスする、**既定値は VB**  ダイアログ ボックスの 、**ツール** メニューのをクリックして**オプション**します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-128">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="3b96c-129">**オプション** ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、 をクリックし、 **VB が既定で**します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-129">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="3b96c-130">初期の既定の設定**VB 既定**は`On`です。</span><span class="sxs-lookup"><span data-stu-id="3b96c-130">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="3b96c-131">コマンドラインで Option explicit ステートメントを設定するには</span><span class="sxs-lookup"><span data-stu-id="3b96c-131">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="3b96c-132">含める、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラ オプションで、 **vbc**コマンドです。</span><span class="sxs-lookup"><span data-stu-id="3b96c-132">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b96c-133">例</span><span class="sxs-lookup"><span data-stu-id="3b96c-133">Example</span></span>  
 <span data-ttu-id="3b96c-134">次の例では、`Option Explicit`ステートメントを強制的にすべての変数を明示的に宣言します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-134">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="3b96c-135">宣言されていない変数を使用するとすると、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3b96c-135">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 <span data-ttu-id="3b96c-136">[!code-vb[VbVbalrStatements #&47;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3b96c-136">[!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="3b96c-137">[!code-vb[VbVbalrStatements #&48;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="3b96c-137">[!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b96c-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b96c-138">See Also</span></span>  
 <span data-ttu-id="3b96c-139">[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3b96c-139">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="3b96c-140"> [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3b96c-140"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="3b96c-141"> [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3b96c-141"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="3b96c-142"> [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3b96c-142"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="3b96c-143"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="3b96c-143"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="3b96c-144"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="3b96c-144"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="3b96c-145"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="3b96c-145"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="3b96c-146"> [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="3b96c-146"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
