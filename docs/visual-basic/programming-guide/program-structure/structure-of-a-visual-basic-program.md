---
title: Visual Basic プログラムの構造
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 5c45cc8982a03d5bdd974434164187b03529ae05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654831"
---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="ad0fe-102">Visual Basic プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="ad0fe-102">Structure of a Visual Basic Program</span></span>
<span data-ttu-id="ad0fe-103">Visual Basic プログラムは、標準の構成ブロックから構築します。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-103">A Visual Basic program is built up from standard building blocks.</span></span> <span data-ttu-id="ad0fe-104">A*ソリューション*1 つまたは複数のプロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-104">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="ad0fe-105">A*プロジェクト*さらに、1 つまたは複数のアセンブリを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-105">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="ad0fe-106">各*アセンブリ*が 1 つまたは複数のソース ファイルからコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-106">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="ad0fe-107">A*ソースファイル*定義とクラス、構造体、モジュール、および最終的にすべてのコードが含まれているインターフェイスの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-107">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="ad0fe-108">Visual Basic プログラムの詳細については、これらの構成要素は、次を参照してください。[ソリューションとプロジェクト](/visualstudio/ide/solutions-and-projects-in-visual-studio)と[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-108">For more information about these building blocks of a Visual Basic program, see [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="ad0fe-109">ファイル レベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="ad0fe-109">File-Level Programming Elements</span></span>  
 <span data-ttu-id="ad0fe-110">プロジェクトまたはファイルを開始する、コード エディターを開くと、既に実行されていると、正しい順序でいくつかのコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-110">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="ad0fe-111">すべてのコードを記述するは、次の順序に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-111">Any code that you write should follow the following sequence:</span></span>  
  
1.  <span data-ttu-id="ad0fe-112">`Option` ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-112">`Option` statements</span></span>  
  
2.  <span data-ttu-id="ad0fe-113">`Imports` ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-113">`Imports` statements</span></span>  
  
3.  <span data-ttu-id="ad0fe-114">`Namespace` ステートメントと名前空間レベル要素</span><span class="sxs-lookup"><span data-stu-id="ad0fe-114">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="ad0fe-115">異なる順序でステートメントを入力すると、コンパイル エラーが発生することができます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-115">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="ad0fe-116">プログラムは、条件付きコンパイル ステートメントを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-116">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="ad0fe-117">上記の一連のステートメントの間でソース ファイルでこれらを挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-117">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="ad0fe-118">ステートメントのオプション</span><span class="sxs-lookup"><span data-stu-id="ad0fe-118">Option Statements</span></span>  
 <span data-ttu-id="ad0fe-119">`Option` ステートメントは、構文とロジック エラーを回避することができ、後続のコードの基本的な規則を確立します。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-119">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="ad0fe-120">[Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)いるすべての変数の宣言し、の綴り、デバッグ時間を短縮することを確認します。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-120">The [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="ad0fe-121">[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)を異なるデータ型の変数間で作業するときに発生する可能性がロジックのエラーやデータの損失を最小限に抑えるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-121">The [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="ad0fe-122">[Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)方法文字列は、互いにいずれかに基づく比較を指定します、`Binary`または`Text`値。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-122">The [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="ad0fe-123">Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-123">Imports Statements</span></span>  
 <span data-ttu-id="ad0fe-124">含めることができます、 [Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)名、プロジェクトの外側で定義をインポートします。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-124">You can include an [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="ad0fe-125">`Imports`ステートメントにより、コードをクラスとそれらを修飾することがなく、インポートされた名前空間内で定義されているその他の型を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-125">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="ad0fe-126">できるだけ使用することができます`Imports`に応じてステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-126">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="ad0fe-127">詳細については、次を参照してください。[参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-127">For more information, see [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="ad0fe-128">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-128">Namespace Statements</span></span>  
 <span data-ttu-id="ad0fe-129">名前空間のヘルプ整理して、グループ化とへのアクセスの容易にするためのプログラミング要素を分類します。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-129">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="ad0fe-130">使用する、 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)を特定の名前空間内で次のステートメントを分類します。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-130">You use the [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="ad0fe-131">詳細については、「[Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-131">For more information, see [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="ad0fe-132">条件付きコンパイル ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-132">Conditional Compilation Statements</span></span>  
 <span data-ttu-id="ad0fe-133">条件付きコンパイル ステートメントは、ソース ファイルでほぼどこでも表示できます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-133">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="ad0fe-134">含まれているまたは特定の条件によってコンパイル時に除外するコードの部分と、されます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-134">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="ad0fe-135">使用することも、アプリケーションのデバッグの条件付きコードがデバッグ モードのみで実行されるためです。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-135">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="ad0fe-136">詳細については、次を参照してください。[条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-136">For more information, see [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="ad0fe-137">Namespace レベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="ad0fe-137">Namespace-Level Programming Elements</span></span>  
 <span data-ttu-id="ad0fe-138">クラス、構造体、およびモジュールには、ソース ファイル内のすべてのコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-138">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="ad0fe-139">*名前空間レベル*要素、またはファイル レベルのソースを名前空間内に表示されることができます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-139">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="ad0fe-140">その他のすべてのプログラミング要素の宣言が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-140">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="ad0fe-141">要素のシグネチャを定義しますが、実装を提供しない、インターフェイスは、モジュール レベルも表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-141">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="ad0fe-142">モジュール レベルの要素の詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-142">For more information on the module-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="ad0fe-143">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-143">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [<span data-ttu-id="ad0fe-144">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-144">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [<span data-ttu-id="ad0fe-145">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-145">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [<span data-ttu-id="ad0fe-146">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-146">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="ad0fe-147">名前空間レベルでのデータ要素は、列挙およびデリゲートです。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-147">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="ad0fe-148">モジュール レベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="ad0fe-148">Module-Level Programming Elements</span></span>  
 <span data-ttu-id="ad0fe-149">プロシージャ、演算子、プロパティ、およびイベントは、実行可能コード (実行時にアクションを実行するステートメント) が保持できる唯一のプログラミング要素です。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-149">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="ad0fe-150">*モジュール レベル*プログラムの要素。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-150">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="ad0fe-151">プロシージャ レベルの要素の詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-151">For more information on the procedure-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="ad0fe-152">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-152">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="ad0fe-153">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-153">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [<span data-ttu-id="ad0fe-154">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-154">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="ad0fe-155">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-155">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [<span data-ttu-id="ad0fe-156">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-156">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="ad0fe-157">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="ad0fe-157">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="ad0fe-158">モジュール レベルのデータ要素は、変数、定数、列挙型、およびデリゲートされます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-158">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="ad0fe-159">プロシージャ レベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="ad0fe-159">Procedure-Level Programming Elements</span></span>  
 <span data-ttu-id="ad0fe-160">ほとんどの内容の*プロシージャ レベル*要素は、実行可能なステートメントは、プログラムの実行時のコードを構成します。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-160">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="ad0fe-161">すべての実行可能コードは、いくつかの手順である必要があります (`Function`、 `Sub`、 `Operator`、 `Get`、 `Set`、 `AddHandler`、 `RemoveHandler`、 `RaiseEvent`)。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-161">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="ad0fe-162">詳細については、「[ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-162">For more information, see [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
 <span data-ttu-id="ad0fe-163">プロシージャ レベルのデータ要素は、ローカル変数および定数に限定されます。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-163">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="ad0fe-164">Main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ad0fe-164">The Main Procedure</span></span>  
 <span data-ttu-id="ad0fe-165">`Main`プロシージャは、アプリケーションが読み込まれているときに実行する最初のコード。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-165">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="ad0fe-166">`Main` 開始ポイントとアプリケーションの全体的なコントロールとして機能します。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-166">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="ad0fe-167">次の 4 種類がある`Main`:</span><span class="sxs-lookup"><span data-stu-id="ad0fe-167">There are four varieties of `Main`:</span></span>  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="ad0fe-168">この手順の最も一般的なさまざまな`Sub Main()`します。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-168">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="ad0fe-169">詳細については、次を参照してください。 [Visual Basic の Main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad0fe-169">For more information, see [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0fe-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad0fe-170">See Also</span></span>  
 [<span data-ttu-id="ad0fe-171">Visual Basic の main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ad0fe-171">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 [<span data-ttu-id="ad0fe-172">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="ad0fe-172">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="ad0fe-173">Visual Basic の制限事項</span><span class="sxs-lookup"><span data-stu-id="ad0fe-173">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)
