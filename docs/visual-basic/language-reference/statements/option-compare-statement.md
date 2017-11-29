---
title: "Option Compare ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 281b18322f5be4e7dadcb9533680b25016a44c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="option-compare-statement"></a><span data-ttu-id="a7fbb-102">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="a7fbb-102">Option Compare Statement</span></span>
<span data-ttu-id="a7fbb-103">文字列データを比較するときに使用する既定の比較方法を宣言します。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7fbb-104">構文</span><span class="sxs-lookup"><span data-stu-id="a7fbb-104">Syntax</span></span>  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="a7fbb-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="a7fbb-105">Parts</span></span>  
  
|<span data-ttu-id="a7fbb-106">用語</span><span class="sxs-lookup"><span data-stu-id="a7fbb-106">Term</span></span>|<span data-ttu-id="a7fbb-107">定義</span><span class="sxs-lookup"><span data-stu-id="a7fbb-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="a7fbb-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-108">Optional.</span></span> <span data-ttu-id="a7fbb-109">文字列比較は、文字の内部バイナリ表現から派生した並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="a7fbb-110">この種類の比較は、文字列にテキストとして解釈されない文字を含めることができる場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="a7fbb-111">この場合、大文字と小文字の区別など、アルファベットの等値比較にバイアスをかけないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="a7fbb-112">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-112">Optional.</span></span> <span data-ttu-id="a7fbb-113">文字列比較は、システムのロケールによって決まる、大文字と小文字を区別しないテキストの並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="a7fbb-114">この種類の比較は、文字列にすべてのテキスト文字が含まれており、大文字と小文字を区別しないことや類縁の文字など、アルファベットの等値を考慮して文字列を比較する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="a7fbb-115">たとえば、`A` と `a` は等しく、`Ä` と `ä` は `B` と `b` よりも前に位置すると見なされるようにできます。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7fbb-116">コメント</span><span class="sxs-lookup"><span data-stu-id="a7fbb-116">Remarks</span></span>  
 <span data-ttu-id="a7fbb-117">使用した場合、`Option Compare` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="a7fbb-118">`Option Compare` ステートメントでは、文字列の比較方法 (`Binary` または `Text`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="a7fbb-119">既定のテキスト比較方法は `Binary` です。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="a7fbb-120">`Binary` 比較では、各文字列の各文字の Unicode 数値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="a7fbb-121">`Text` 比較では、現在のカルチャでの語彙的意味に基づいて各 Unicode 文字が比較されます。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="a7fbb-122">Microsoft Windows では、並べ替え順序はコード ページによって決まります。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="a7fbb-123">詳細については、「[コード ページ](/cpp/c-runtime-library/code-pages)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="a7fbb-124">次の例では、英語/ヨーロッパ言語のコード ページ (ANSI 1252) の文字が、`Option Compare Binary` を使用して並べ替えられ、一般的なバイナリ並べ替え順序が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="a7fbb-125">`Option Compare Text` を使用して同じコード ページの同じ文字を並べ替えると、次のテキスト並べ替え順序が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="a7fbb-126">Option Compare ステートメントが指定されていない場合</span><span class="sxs-lookup"><span data-stu-id="a7fbb-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="a7fbb-127">ソース コードが含まれていない場合、`Option Compare`ステートメントでは、 **Option Compare**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="a7fbb-128">設定が指定されたコマンド ライン コンパイラを使用する場合、 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-128">If you use the command-line compiler, the setting specified by the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="a7fbb-129">IDE で Option Compare を設定するには</span><span class="sxs-lookup"><span data-stu-id="a7fbb-129">To set Option Compare in the IDE</span></span>  
  
1.  <span data-ttu-id="a7fbb-130">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="a7fbb-131">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-131">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="a7fbb-132">詳細については、次を参照してください。 [NIB: プロジェクト デザイナーでプロジェクトのプロパティを管理する](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)です。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-132">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="a7fbb-133">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-133">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="a7fbb-134">値を設定、 **Option Compare**ボックス。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-134">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="a7fbb-135">プロジェクトを作成するときに、 **Option Compare**の設定、**コンパイル** タブに設定されている、 **Option Compare**での設定、**オプション**ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-135">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="a7fbb-136">この設定を変更する、**ツール** メニューのをクリックして**オプション**です。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-136">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="a7fbb-137">**オプション** ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、クリックして**既定値は VB**です。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-137">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="a7fbb-138">初期の既定の設定**VB の既定値**は**バイナリ**です。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-138">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="a7fbb-139">コマンド ラインで Option Compare を設定するには</span><span class="sxs-lookup"><span data-stu-id="a7fbb-139">To set Option Compare on the command line</span></span>  
  
-   <span data-ttu-id="a7fbb-140">含める、 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)コンパイラ オプション、 **vbc**コマンド。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-140">Include the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7fbb-141">例</span><span class="sxs-lookup"><span data-stu-id="a7fbb-141">Example</span></span>  
 <span data-ttu-id="a7fbb-142">次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法としてバイナリ比較を設定します。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-142">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="a7fbb-143">このコードを使用するには、`Option Compare Binary` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-143">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="a7fbb-144">例</span><span class="sxs-lookup"><span data-stu-id="a7fbb-144">Example</span></span>  
 <span data-ttu-id="a7fbb-145">次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法として大文字と小文字を区別しないテキスト並べ替え順序を設定します。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-145">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="a7fbb-146">このコードを使用するには、`Option Compare Text` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。</span><span class="sxs-lookup"><span data-stu-id="a7fbb-146">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a7fbb-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7fbb-147">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>  
 <xref:Microsoft.VisualBasic.Strings.Replace%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [<span data-ttu-id="a7fbb-148">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="a7fbb-148">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="a7fbb-149">比較演算子</span><span class="sxs-lookup"><span data-stu-id="a7fbb-149">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="a7fbb-150">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="a7fbb-150">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="a7fbb-151">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="a7fbb-151">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="a7fbb-152">文字列関数</span><span class="sxs-lookup"><span data-stu-id="a7fbb-152">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)  
 [<span data-ttu-id="a7fbb-153">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="a7fbb-153">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="a7fbb-154">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="a7fbb-154">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
