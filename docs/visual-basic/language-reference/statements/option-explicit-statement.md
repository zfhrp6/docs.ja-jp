---
title: Option Explicit ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: 3a2d81b1441052c132e4739dfe6045f8c3a026d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604602"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="4085d-102">Option Explicit ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4085d-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="4085d-103">強制的に、ファイル内のすべての変数を明示的に宣言または変数の暗黙的な宣言を許可します。</span><span class="sxs-lookup"><span data-stu-id="4085d-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4085d-104">構文</span><span class="sxs-lookup"><span data-stu-id="4085d-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="4085d-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="4085d-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="4085d-106">任意。</span><span class="sxs-lookup"><span data-stu-id="4085d-106">Optional.</span></span> <span data-ttu-id="4085d-107">により、`Option Explicit`をチェックします。</span><span class="sxs-lookup"><span data-stu-id="4085d-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="4085d-108">場合`On`または`Off`が指定されていない、既定値は`On`します。</span><span class="sxs-lookup"><span data-stu-id="4085d-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="4085d-109">任意。</span><span class="sxs-lookup"><span data-stu-id="4085d-109">Optional.</span></span> <span data-ttu-id="4085d-110">無効に`Option Explicit`をチェックします。</span><span class="sxs-lookup"><span data-stu-id="4085d-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4085d-111">コメント</span><span class="sxs-lookup"><span data-stu-id="4085d-111">Remarks</span></span>  
 <span data-ttu-id="4085d-112">ときに`Option Explicit On`または`Option Explicit`を使用してすべての変数を明示的に宣言する必要がありますが、ファイルに表示されます、`Dim`または`ReDim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4085d-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="4085d-113">宣言されていない変数名を使用しようとする場合は、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4085d-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="4085d-114">`Option Explicit Off`ステートメントにより、変数を暗黙的に宣言します。</span><span class="sxs-lookup"><span data-stu-id="4085d-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="4085d-115">使用した場合、`Option Explicit` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4085d-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4085d-116">設定`Option Explicit`に`Off`は一般にないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4085d-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="4085d-117">変数名のスペルを 1 か所以上間違えると、プログラムの実行時に予期しない結果を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4085d-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="4085d-118">Option Explicit ステートメントが存在する場合されません。</span><span class="sxs-lookup"><span data-stu-id="4085d-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="4085d-119">ソース コードが含まれていない場合、`Option Explicit`ステートメントでは、 **Option Explicit**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。</span><span class="sxs-lookup"><span data-stu-id="4085d-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="4085d-120">コマンド ライン コンパイラを使用する場合、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="4085d-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="4085d-121">IDE で Option Explicit を設定するには</span><span class="sxs-lookup"><span data-stu-id="4085d-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="4085d-122">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="4085d-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="4085d-123">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4085d-123">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="4085d-124">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4085d-124">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="4085d-125">値を設定、 **Option Explicit**ボックス。</span><span class="sxs-lookup"><span data-stu-id="4085d-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="4085d-126">新しいプロジェクトを作成するときに、 **Option Explicit**の設定、**コンパイル** タブに設定されている、 **Option Explicit**での設定、 **VBの既定値** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="4085d-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="4085d-127">アクセスする、**既定値は VB**  ダイアログ ボックスで、**ツール** メニューのをクリックして**オプション**です。</span><span class="sxs-lookup"><span data-stu-id="4085d-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="4085d-128">**[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、**[VISUAL BASIC の既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4085d-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="4085d-129">初期の既定の設定**VB 既定**は`On`します。</span><span class="sxs-lookup"><span data-stu-id="4085d-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="4085d-130">コマンドラインで Option Explicit を設定するには</span><span class="sxs-lookup"><span data-stu-id="4085d-130">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="4085d-131">含める、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラ オプション、 **vbc**コマンド。</span><span class="sxs-lookup"><span data-stu-id="4085d-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4085d-132">例</span><span class="sxs-lookup"><span data-stu-id="4085d-132">Example</span></span>  
 <span data-ttu-id="4085d-133">次の例では、`Option Explicit`すべての変数の明示的な宣言を強制するステートメント。</span><span class="sxs-lookup"><span data-stu-id="4085d-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="4085d-134">宣言されていない変数を使用すると場合、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4085d-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4085d-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="4085d-135">See Also</span></span>  
 [<span data-ttu-id="4085d-136">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="4085d-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="4085d-137">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="4085d-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="4085d-138">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="4085d-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="4085d-139">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="4085d-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="4085d-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="4085d-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="4085d-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="4085d-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="4085d-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="4085d-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 <span data-ttu-id="4085d-143">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="4085d-143">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
