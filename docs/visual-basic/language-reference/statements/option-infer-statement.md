---
title: "Option Infer ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4634c198b5fc41a4834cbd3cd96f9d3f1863d09b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="option-infer-statement"></a><span data-ttu-id="9ea7b-102">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="9ea7b-102">Option Infer Statement</span></span>
<span data-ttu-id="9ea7b-103">変数の宣言でローカル型推論を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ea7b-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ea7b-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="9ea7b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9ea7b-105">Parts</span></span>  
  
|<span data-ttu-id="9ea7b-106">用語</span><span class="sxs-lookup"><span data-stu-id="9ea7b-106">Term</span></span>|<span data-ttu-id="9ea7b-107">定義</span><span class="sxs-lookup"><span data-stu-id="9ea7b-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="9ea7b-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-108">Optional.</span></span> <span data-ttu-id="9ea7b-109">ローカル型推論を有効にします。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="9ea7b-110">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-110">Optional.</span></span> <span data-ttu-id="9ea7b-111">ローカル型推論を無効にします。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ea7b-112">コメント</span><span class="sxs-lookup"><span data-stu-id="9ea7b-112">Remarks</span></span>  
 <span data-ttu-id="9ea7b-113">ファイルに `Option Infer` を設定するには、ファイルの先頭に他のソース コードよりも前に `Option Infer On` または `Option Infer Off` を入力します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="9ea7b-114">ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="9ea7b-115">`Option Infer` を `On` に設定すると、データ型を明示的に指定せずにローカル変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="9ea7b-116">コンパイラは、初期化式の型から変数のデータ型を推測します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="9ea7b-117">次の図では、`Option Infer` がオンになっています。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="9ea7b-118">宣言 `Dim someVar = 2` 内の変数は、型の推定によって整数として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="9ea7b-119">![宣言の IntelliSense ビュー。] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="9ea7b-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="9ea7b-120">Option Infer がオンのときの IntelliSense</span><span class="sxs-lookup"><span data-stu-id="9ea7b-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="9ea7b-121">次の図では、`Option Infer` がオフになっています。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="9ea7b-122">宣言 `Dim someVar = 2` 内の変数は、型の推定によって `Object` として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="9ea7b-123">この例では、 **Option Strict**に設定した**オフ**上、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="9ea7b-124">![宣言の IntelliSense ビュー。] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="9ea7b-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="9ea7b-125">Option Infer がオフのときの IntelliSense</span><span class="sxs-lookup"><span data-stu-id="9ea7b-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ea7b-126">変数を `Object` として宣言すると、プログラムの実行中にランタイム型が変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="9ea7b-127">という操作を実行*ボックス化*と*アンボックス*間で変換する、`Object`と値の種類、これにより実行速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="9ea7b-128">ボックス化とボックス化解除については、次を参照してください。、 [Visual Basic 言語仕様](../../../visual-basic/reference/language-specification/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="9ea7b-129">型の推定は、プロシージャ レベルで適用され、クラス、構造体、モジュール、またはインターフェイスのプロシージャの外側には適用されません。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="9ea7b-130">詳細については、次を参照してください。[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="9ea7b-131">Option Infer ステートメントが指定されていない場合</span><span class="sxs-lookup"><span data-stu-id="9ea7b-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="9ea7b-132">ソース コードが含まれていない場合、`Option Infer`ステートメントでは、 **Option Infer**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="9ea7b-133">コマンド ライン コンパイラを使用する場合、 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="9ea7b-134">IDE の Option Infer を設定するには</span><span class="sxs-lookup"><span data-stu-id="9ea7b-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="9ea7b-135">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="9ea7b-136">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-136">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="9ea7b-137">詳細については、次を参照してください。 [NIB: プロジェクト デザイナーでプロジェクトのプロパティを管理する](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-137">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="9ea7b-138">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-138">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="9ea7b-139">値を設定、 **Option infer**ボックス。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-139">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="9ea7b-140">新しいプロジェクトを作成するときに、 **Option Infer**の設定、**コンパイル** タブに設定されている、 **Option Infer**で設定、**既定値は VB**ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="9ea7b-141">アクセスする、**既定値は VB**  ダイアログ ボックスで、**ツール** メニューのをクリックして**オプション**です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="9ea7b-142">**オプション** ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、クリックして**既定値は VB**です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="9ea7b-143">初期の既定の設定**VB 既定**は`On`します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-143">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="9ea7b-144">コマンド ラインで Option Infer を設定するには</span><span class="sxs-lookup"><span data-stu-id="9ea7b-144">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="9ea7b-145">含める、 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)コンパイラ オプション、 **vbc**コマンド。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-145">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="9ea7b-146">既定のデータ型と値</span><span class="sxs-lookup"><span data-stu-id="9ea7b-146">Default Data Types and Values</span></span>  
 <span data-ttu-id="9ea7b-147">次の表では、`Dim` ステートメントのデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="9ea7b-148">データ型が指定されているか</span><span class="sxs-lookup"><span data-stu-id="9ea7b-148">Data type specified?</span></span>|<span data-ttu-id="9ea7b-149">初期化子が指定されているか</span><span class="sxs-lookup"><span data-stu-id="9ea7b-149">Initializer specified?</span></span>|<span data-ttu-id="9ea7b-150">例</span><span class="sxs-lookup"><span data-stu-id="9ea7b-150">Example</span></span>|<span data-ttu-id="9ea7b-151">結果</span><span class="sxs-lookup"><span data-stu-id="9ea7b-151">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="9ea7b-152">Ｘ</span><span class="sxs-lookup"><span data-stu-id="9ea7b-152">No</span></span>|<span data-ttu-id="9ea7b-153">Ｘ</span><span class="sxs-lookup"><span data-stu-id="9ea7b-153">No</span></span>|`Dim qty`|<span data-ttu-id="9ea7b-154">`Option Strict` がオフ (既定値) の場合、変数は `Nothing` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="9ea7b-155">`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="9ea7b-156">Ｘ</span><span class="sxs-lookup"><span data-stu-id="9ea7b-156">No</span></span>|<span data-ttu-id="9ea7b-157">○</span><span class="sxs-lookup"><span data-stu-id="9ea7b-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="9ea7b-158">`Option Infer` がオン (既定値) の場合、変数は初期化子のデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="9ea7b-159">参照してください[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-159">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="9ea7b-160">`Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="9ea7b-161">`Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="9ea7b-162">○</span><span class="sxs-lookup"><span data-stu-id="9ea7b-162">Yes</span></span>|<span data-ttu-id="9ea7b-163">Ｘ</span><span class="sxs-lookup"><span data-stu-id="9ea7b-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="9ea7b-164">変数は、データ型の既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="9ea7b-165">詳細については、次を参照してください。 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-165">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="9ea7b-166">はい</span><span class="sxs-lookup"><span data-stu-id="9ea7b-166">Yes</span></span>|<span data-ttu-id="9ea7b-167">○</span><span class="sxs-lookup"><span data-stu-id="9ea7b-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="9ea7b-168">初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9ea7b-169">例</span><span class="sxs-lookup"><span data-stu-id="9ea7b-169">Example</span></span>  
 <span data-ttu-id="9ea7b-170">次の例では、`Option Infer` ステートメントがローカル型推論をどのように有効にするかを示します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="9ea7b-171">例</span><span class="sxs-lookup"><span data-stu-id="9ea7b-171">Example</span></span>  
 <span data-ttu-id="9ea7b-172">次の例では、変数が `Object` として識別されたときに、ランタイム型が異なる場合があることを示します。</span><span class="sxs-lookup"><span data-stu-id="9ea7b-172">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9ea7b-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ea7b-173">See Also</span></span>  
 [<span data-ttu-id="9ea7b-174">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="9ea7b-174">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="9ea7b-175">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="9ea7b-175">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="9ea7b-176">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="9ea7b-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="9ea7b-177">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="9ea7b-177">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="9ea7b-178">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="9ea7b-178">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 <span data-ttu-id="9ea7b-179">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="9ea7b-179">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>  
 [<span data-ttu-id="9ea7b-180">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="9ea7b-180">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="9ea7b-181">ボックス化とボックス化解除</span><span class="sxs-lookup"><span data-stu-id="9ea7b-181">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
