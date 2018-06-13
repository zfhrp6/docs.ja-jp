---
title: Visual Basic での条件付きコンパイル
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 496df36242c6b43e7e3ec94ce675d11177e8b466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653018"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="77c2c-102">Visual Basic での条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="77c2c-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="77c2c-103">*条件付きコンパイル*、他のユーザーは無視されます、特定のプログラムではコード ブロックは選択的にコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="77c2c-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="77c2c-104">たとえば、書き込むする可能性があるか、同じプログラミング タスクを別のアプローチの速度を比較するステートメントをデバッグすることが複数言語のアプリケーションをローカライズします。</span><span class="sxs-lookup"><span data-stu-id="77c2c-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="77c2c-105">条件付きコンパイル ステートメントは実行時ではなく、コンパイル時に実行するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="77c2c-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="77c2c-106">条件付きでコンパイルされているコードのブロックを指定、`#If...Then...#Else`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="77c2c-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="77c2c-107">たとえば、フランス語、ドイツ語を作成する同じから同じアプリケーションのバージョンのソース コード、プラットフォーム固有のコードのセグメントを埋め込む`#If...Then`定義済みの定数を使用して、ステートメント`FrenchVersion`と`GermanVersion`です。</span><span class="sxs-lookup"><span data-stu-id="77c2c-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="77c2c-108">次の例でどのようにします。</span><span class="sxs-lookup"><span data-stu-id="77c2c-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 <span data-ttu-id="77c2c-109">値を設定した場合、`FrenchVersion`に条件付きコンパイル定数`True`コンパイル時に、フランス語版の条件付きのコードがコンパイルされています。</span><span class="sxs-lookup"><span data-stu-id="77c2c-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="77c2c-110">値を設定した場合、`GermanVersion`に定数`True`コンパイラがドイツ語版を使用します。</span><span class="sxs-lookup"><span data-stu-id="77c2c-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="77c2c-111">どちらに設定されている場合`True`、最後にコード`Else`ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="77c2c-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77c2c-112">オートコンプリートは、コードの編集時に機能しないと、コードが現在のブランチの一部ではない場合は、条件付きコンパイル ディレクティブを使用するには。</span><span class="sxs-lookup"><span data-stu-id="77c2c-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="77c2c-113">条件付きコンパイル定数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="77c2c-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="77c2c-114">3 つの方法のいずれかで条件付きコンパイル定数を設定できます。</span><span class="sxs-lookup"><span data-stu-id="77c2c-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="77c2c-115">**プロジェクト デザイナー**</span><span class="sxs-lookup"><span data-stu-id="77c2c-115">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="77c2c-116">コマンド ライン コンパイラを使用するときに、コマンドラインで</span><span class="sxs-lookup"><span data-stu-id="77c2c-116">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="77c2c-117">コードで</span><span class="sxs-lookup"><span data-stu-id="77c2c-117">In your code</span></span>  
  
 <span data-ttu-id="77c2c-118">条件付きコンパイル定数は、特殊なスコープを持ち、標準的なコードからアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="77c2c-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="77c2c-119">条件付きコンパイル定数のスコープは、設定されている方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="77c2c-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="77c2c-120">次の表は、上記で説明した 3 つの方法のそれぞれを使用して宣言されている定数のスコープを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="77c2c-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="77c2c-121">定数を設定する方法</span><span class="sxs-lookup"><span data-stu-id="77c2c-121">How constant is set</span></span>|<span data-ttu-id="77c2c-122">定数のスコープ</span><span class="sxs-lookup"><span data-stu-id="77c2c-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="77c2c-123">**プロジェクト デザイナー**</span><span class="sxs-lookup"><span data-stu-id="77c2c-123">**Project Designer**</span></span>|<span data-ttu-id="77c2c-124">プロジェクト内のすべてのファイルへの公開</span><span class="sxs-lookup"><span data-stu-id="77c2c-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="77c2c-125">コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="77c2c-125">Command line</span></span>|<span data-ttu-id="77c2c-126">コマンド ライン コンパイラに渡されるすべてのファイルへの公開</span><span class="sxs-lookup"><span data-stu-id="77c2c-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="77c2c-127">`#Const` コード内のステートメント</span><span class="sxs-lookup"><span data-stu-id="77c2c-127">`#Const` statement in code</span></span>|<span data-ttu-id="77c2c-128">プライベートに宣言されているファイル</span><span class="sxs-lookup"><span data-stu-id="77c2c-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="77c2c-129">プロジェクト デザイナーで定数を設定するには</span><span class="sxs-lookup"><span data-stu-id="77c2c-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="77c2c-130">実行可能ファイルを作成する前定数を設定、**プロジェクト デザイナー**で提供される手順に従って、[管理プロジェクトおよびソリューションのプロパティ](/visualstudio/ide/managing-project-and-solution-properties)です。</span><span class="sxs-lookup"><span data-stu-id="77c2c-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="77c2c-131">コマンドラインで定数を設定するには</span><span class="sxs-lookup"><span data-stu-id="77c2c-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="77c2c-132">-を使用して、 **/d**スイッチを次の例のように、条件付きコンパイル定数を入力します。</span><span class="sxs-lookup"><span data-stu-id="77c2c-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="77c2c-133">間で必要な空き領域がない、 **/d**スイッチとの最初の定数です。</span><span class="sxs-lookup"><span data-stu-id="77c2c-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="77c2c-134">詳細については、次を参照してください。 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)です。</span><span class="sxs-lookup"><span data-stu-id="77c2c-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="77c2c-135">コマンド ラインの宣言で入力した宣言のオーバーライド、**プロジェクト デザイナー**は消去されません。</span><span class="sxs-lookup"><span data-stu-id="77c2c-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="77c2c-136">引数の設定**プロジェクト デザイナー**後続のコンパイルを有効になります。</span><span class="sxs-lookup"><span data-stu-id="77c2c-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="77c2c-137">定数をそれ自体のコードを記述する場合はありません、配置に関する厳密な規則のスコープが宣言されているモジュール全体であるため。</span><span class="sxs-lookup"><span data-stu-id="77c2c-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="77c2c-138">コード内の定数を設定するには</span><span class="sxs-lookup"><span data-stu-id="77c2c-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="77c2c-139">-定数を使用するモジュールの宣言ブロックに配置します。</span><span class="sxs-lookup"><span data-stu-id="77c2c-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="77c2c-140">これにより、整理したり読みやすく、コードを維持します。</span><span class="sxs-lookup"><span data-stu-id="77c2c-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="77c2c-141">関連トピック</span><span class="sxs-lookup"><span data-stu-id="77c2c-141">Related Topics</span></span>  
  
|<span data-ttu-id="77c2c-142">タイトル</span><span class="sxs-lookup"><span data-stu-id="77c2c-142">Title</span></span>|<span data-ttu-id="77c2c-143">説明</span><span class="sxs-lookup"><span data-stu-id="77c2c-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="77c2c-144">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="77c2c-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="77c2c-145">コードを容易に読み取りおよびメンテナンスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="77c2c-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="77c2c-146">参照</span><span class="sxs-lookup"><span data-stu-id="77c2c-146">Reference</span></span>  
 [<span data-ttu-id="77c2c-147">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="77c2c-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="77c2c-148">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="77c2c-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="77c2c-149">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77c2c-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
