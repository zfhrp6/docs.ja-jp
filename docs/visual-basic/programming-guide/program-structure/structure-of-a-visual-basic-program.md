---
title: "Visual Basic プログラムの構造 |Microsoft ドキュメント"
ms.custom: 
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
- conditional compilation, Visual Basic
- program structure, Visual Basic
- procedures, structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
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
ms.openlocfilehash: 3e16ea51d0f766fcb5866cde89e5384a153ac050
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="e71e0-102">Visual Basic プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="e71e0-102">Structure of a Visual Basic Program</span></span>
<span data-ttu-id="e71e0-103">A[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムは、標準の構成ブロックから構築します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-103">A [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program is built up from standard building blocks.</span></span> <span data-ttu-id="e71e0-104">A*ソリューション*1 つまたは複数のプロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-104">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="e71e0-105">A*プロジェクト*さらに、1 つまたは複数のアセンブリを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-105">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="e71e0-106">各*アセンブリ*が&1; つまたは複数のソース ファイルからコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e71e0-106">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="e71e0-107">A*ソースファイル*定義とクラス、構造体、モジュール、および最終的には、すべてのコードが含まれているインターフェイスの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-107">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="e71e0-108">これらの構成要素の詳細については、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムを参照してください[ソリューションとプロジェクト](https://docs.microsoft.com/visualstudio/ide/solutions-and-projects-in-visual-studio)と[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-108">For more information about these building blocks of a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program, see [Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="e71e0-109">ファイル レベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="e71e0-109">File-Level Programming Elements</span></span>  
 <span data-ttu-id="e71e0-110">プロジェクトまたはファイルを起動して、コード エディターを開いた場所に既に存在し、正しい順序でいくつかのコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-110">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="e71e0-111">作成するすべてのコードは、次の順序に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e71e0-111">Any code that you write should follow the following sequence:</span></span>  
  
1.  <span data-ttu-id="e71e0-112">`Option`ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-112">`Option` statements</span></span>  
  
2.  <span data-ttu-id="e71e0-113">`Imports`ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-113">`Imports` statements</span></span>  
  
3.  <span data-ttu-id="e71e0-114">`Namespace`ステートメントと名前空間レベル要素</span><span class="sxs-lookup"><span data-stu-id="e71e0-114">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="e71e0-115">別の順序でステートメントを入力すると、コンパイル エラーが発生することができます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-115">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="e71e0-116">プログラムでは、条件付きコンパイル ステートメントを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-116">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="e71e0-117">上記の一連のステートメントの間でソース ファイルを挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-117">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="e71e0-118">オプション ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-118">Option Statements</span></span>  
 <span data-ttu-id="e71e0-119">`Option`ステートメントは、後続のコードでは、構文とロジックのエラーを防ぐの基盤となる規則を確立します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-119">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="e71e0-120">[Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)により、すべての変数が宣言されのスペルが正しいデバッグ時間が削減されます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-120">The [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="e71e0-121">[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)を異なるデータ型の変数を使用するときに発生するロジック エラーやデータ損失を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-121">The [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="e71e0-122">[Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)方法文字列は、互いにいずれかに基づく比較を示す、`Binary`または`Text`値。</span><span class="sxs-lookup"><span data-stu-id="e71e0-122">The [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="e71e0-123">Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-123">Imports Statements</span></span>  
 <span data-ttu-id="e71e0-124">含めることができます、 [Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)プロジェクトの外部で定義されている名前をインポートします。</span><span class="sxs-lookup"><span data-stu-id="e71e0-124">You can include an [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="e71e0-125">`Imports`ステートメントでは、クラスとその他の型を修飾しなくても、インポートされた名前空間内で定義を参照するようにコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-125">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="e71e0-126">できるだけ使用することができます`Imports`ステートメントに該当します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-126">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="e71e0-127">詳細については、次を参照してください。[参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-127">For more information, see [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="e71e0-128">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-128">Namespace Statements</span></span>  
 <span data-ttu-id="e71e0-129">名前空間のヘルプの編成し、分類、プログラミングの要素をグループ化およびへのアクセスを簡素化できます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-129">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="e71e0-130">使用する、 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)を特定の名前空間内で次のステートメントを分類します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-130">You use the [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="e71e0-131">詳細については、次を参照してください。 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-131">For more information, see [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="e71e0-132">条件付きコンパイル ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-132">Conditional Compilation Statements</span></span>  
 <span data-ttu-id="e71e0-133">条件付きコンパイル ステートメントは、ソース ファイルにどこに表示できます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-133">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="e71e0-134">含まれているまたは特定の条件によってコンパイル時に除外するコードの部分と、されます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-134">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="e71e0-135">行えますに、アプリケーションのデバッグに条件付きコードがデバッグ モードのみで実行されているためです。</span><span class="sxs-lookup"><span data-stu-id="e71e0-135">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="e71e0-136">詳細については、次を参照してください。[条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-136">For more information, see [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="e71e0-137">Namespace レベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="e71e0-137">Namespace-Level Programming Elements</span></span>  
 <span data-ttu-id="e71e0-138">クラス、構造体、およびモジュールには、ソース ファイル内のすべてのコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-138">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="e71e0-139">*名前空間レベル*要素、またはソース ファイル レベルでは、名前空間内で表示することができます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-139">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="e71e0-140">その他のすべてのプログラミング要素の宣言を保持します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-140">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="e71e0-141">要素のシグネチャを定義しますが、実装を提供しない、インターフェイスは、モジュール レベルも表示されます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-141">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="e71e0-142">モジュール レベルの要素の詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e71e0-142">For more information on the module-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="e71e0-143">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-143">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [<span data-ttu-id="e71e0-144">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-144">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [<span data-ttu-id="e71e0-145">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-145">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [<span data-ttu-id="e71e0-146">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-146">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="e71e0-147">名前空間レベルでのデータ要素は、列挙体およびデリゲートです。</span><span class="sxs-lookup"><span data-stu-id="e71e0-147">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="e71e0-148">モジュール レベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="e71e0-148">Module-Level Programming Elements</span></span>  
 <span data-ttu-id="e71e0-149">プロシージャ、演算子、プロパティ、およびイベントは、実行可能コード (実行時にアクションを実行するステートメント) が保持できる唯一のプログラミング要素です。</span><span class="sxs-lookup"><span data-stu-id="e71e0-149">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="e71e0-150">*モジュール レベル*プログラムの要素。</span><span class="sxs-lookup"><span data-stu-id="e71e0-150">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="e71e0-151">プロシージャ レベル要素の詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e71e0-151">For more information on the procedure-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="e71e0-152">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-152">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="e71e0-153">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-153">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [<span data-ttu-id="e71e0-154">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-154">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="e71e0-155">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-155">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [<span data-ttu-id="e71e0-156">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-156">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="e71e0-157">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="e71e0-157">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="e71e0-158">モジュール レベルのデータ要素は、変数、定数、列挙型、およびデリゲート。</span><span class="sxs-lookup"><span data-stu-id="e71e0-158">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="e71e0-159">プロシージャ レベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="e71e0-159">Procedure-Level Programming Elements</span></span>  
 <span data-ttu-id="e71e0-160">内容のほとんど*プロシージャ レベル*要素は、実行可能ステートメントは、プログラムの実行時のコードを構成します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-160">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="e71e0-161">すべての実行可能コードがいくつかの手順である必要があります (`Function`、 `Sub`、 `Operator`、 `Get`、 `Set`、 `AddHandler`、 `RemoveHandler`、 `RaiseEvent`)。</span><span class="sxs-lookup"><span data-stu-id="e71e0-161">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="e71e0-162">詳細については、次を参照してください。[ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-162">For more information, see [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
 <span data-ttu-id="e71e0-163">プロシージャ レベルでのデータ要素は、ローカル変数および定数に限定されます。</span><span class="sxs-lookup"><span data-stu-id="e71e0-163">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="e71e0-164">メインのプロシージャ</span><span class="sxs-lookup"><span data-stu-id="e71e0-164">The Main Procedure</span></span>  
 <span data-ttu-id="e71e0-165">`Main`プロシージャは、アプリケーションが読み込まれているときに実行する最初のコードです。</span><span class="sxs-lookup"><span data-stu-id="e71e0-165">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="e71e0-166">`Main`開始点し、アプリケーション全体を制御します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-166">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="e71e0-167">次の&4; 種類がある`Main`:</span><span class="sxs-lookup"><span data-stu-id="e71e0-167">There are four varieties of `Main`:</span></span>  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="e71e0-168">この手順の最も一般的なさまざまなの`Sub Main()`です。</span><span class="sxs-lookup"><span data-stu-id="e71e0-168">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="e71e0-169">詳細については、次を参照してください。 [Visual Basic の Main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)します。</span><span class="sxs-lookup"><span data-stu-id="e71e0-169">For more information, see [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71e0-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="e71e0-170">See Also</span></span>  
 <span data-ttu-id="e71e0-171">[Visual Basic の main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e71e0-171">[Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) </span></span>  
<span data-ttu-id="e71e0-172"> [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="e71e0-172"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="e71e0-173"> [Visual Basic の制限事項](../../../visual-basic/programming-guide/program-structure/limitations.md)</span><span class="sxs-lookup"><span data-stu-id="e71e0-173"> [Visual Basic Limitations](../../../visual-basic/programming-guide/program-structure/limitations.md)</span></span>
