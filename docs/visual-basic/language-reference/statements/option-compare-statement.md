---
title: "Option Compare ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
dev_langs:
- VB
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword
- binary comparison
- strings [Visual Basic], returning from functions
- binary comparison, Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword, Option Compare statement
- Binary keyword, Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 00618cd914c06b896d68b4074464af866f747895
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="option-compare-statement"></a><span data-ttu-id="72e9a-102">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="72e9a-102">Option Compare Statement</span></span>
<span data-ttu-id="72e9a-103">文字列データを比較するときに使用する既定の比較方法を宣言します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e9a-104">構文</span><span class="sxs-lookup"><span data-stu-id="72e9a-104">Syntax</span></span>  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="72e9a-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="72e9a-105">Parts</span></span>  
  
|<span data-ttu-id="72e9a-106">用語</span><span class="sxs-lookup"><span data-stu-id="72e9a-106">Term</span></span>|<span data-ttu-id="72e9a-107">定義</span><span class="sxs-lookup"><span data-stu-id="72e9a-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="72e9a-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="72e9a-108">Optional.</span></span> <span data-ttu-id="72e9a-109">文字列比較は、文字の内部バイナリ表現から派生した並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="72e9a-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="72e9a-110">この種類の比較は、文字列にテキストとして解釈されない文字を含めることができる場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="72e9a-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="72e9a-111">この場合、大文字と小文字の区別など、アルファベットの等値比較にバイアスをかけないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="72e9a-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="72e9a-112">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="72e9a-112">Optional.</span></span> <span data-ttu-id="72e9a-113">文字列比較は、システムのロケールによって決まる、大文字と小文字を区別しないテキストの並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="72e9a-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="72e9a-114">この種類の比較は、文字列にすべてのテキスト文字が含まれており、大文字と小文字を区別しないことや類縁の文字など、アルファベットの等値を考慮して文字列を比較する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="72e9a-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="72e9a-115">たとえば、`A` と `a` は等しく、`Ä` と `ä` は `B` と `b` よりも前に位置すると見なされるようにできます。</span><span class="sxs-lookup"><span data-stu-id="72e9a-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72e9a-116">コメント</span><span class="sxs-lookup"><span data-stu-id="72e9a-116">Remarks</span></span>  
 <span data-ttu-id="72e9a-117">使用した場合、`Option Compare` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72e9a-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="72e9a-118">`Option Compare` ステートメントでは、文字列の比較方法 (`Binary` または `Text`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="72e9a-119">既定のテキスト比較方法は `Binary` です。</span><span class="sxs-lookup"><span data-stu-id="72e9a-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="72e9a-120">`Binary` 比較では、各文字列の各文字の Unicode 数値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="72e9a-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="72e9a-121">`Text` 比較では、現在のカルチャでの語彙的意味に基づいて各 Unicode 文字が比較されます。</span><span class="sxs-lookup"><span data-stu-id="72e9a-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="72e9a-122">Microsoft Windows では、並べ替え順序はコード ページによって決まります。</span><span class="sxs-lookup"><span data-stu-id="72e9a-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="72e9a-123">詳細については、「[コード ページ](https://docs.microsoft.com/cpp/c-runtime-library/code-pages)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="72e9a-123">For more information, see [Code Pages](https://docs.microsoft.com/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="72e9a-124">次の例では、英語/ヨーロッパ言語のコード ページ (ANSI 1252) の文字が、`Option Compare Binary` を使用して並べ替えられ、一般的なバイナリ並べ替え順序が生成されます。</span><span class="sxs-lookup"><span data-stu-id="72e9a-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="72e9a-125">
          `Option Compare Text` を使用して同じコード ページの同じ文字を並べ替えると、次のテキスト並べ替え順序が生成されます。</span><span class="sxs-lookup"><span data-stu-id="72e9a-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="72e9a-126">Option Compare ステートメントが指定されていない場合</span><span class="sxs-lookup"><span data-stu-id="72e9a-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="72e9a-127">ソース コードが含まれていない場合、`Option Compare`ステートメント、 **Option Compare**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="72e9a-128">設定が指定されたコマンド ライン コンパイラを使用する場合、 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-128">If you use the command-line compiler, the setting specified by the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="72e9a-129">IDE で Option Compare を設定するには</span><span class="sxs-lookup"><span data-stu-id="72e9a-129">To set Option Compare in the IDE</span></span>  
  
1.  <span data-ttu-id="72e9a-130">**ソリューション エクスプ ローラー**プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="72e9a-131">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-131">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="72e9a-132">詳細については、次を参照してください。 [NIB: プロジェクト デザイナーでプロジェクトのプロパティを管理する](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)です。</span><span class="sxs-lookup"><span data-stu-id="72e9a-132">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="72e9a-133">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="72e9a-133">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="72e9a-134">値を設定、 **Option Compare**ボックス。</span><span class="sxs-lookup"><span data-stu-id="72e9a-134">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="72e9a-135">プロジェクトを作成するときに、 **Option Compare**の設定、**コンパイル**に設定されているタブ、 **Option Compare**で設定、**オプション** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="72e9a-135">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="72e9a-136">この設定を変更する、**ツール** メニューのをクリックして**オプション**します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-136">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="72e9a-137">**オプション** ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、 をクリックし、 **VB が既定で**します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-137">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="72e9a-138">初期の既定の設定**VB 既定**は**バイナリ**します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-138">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="72e9a-139">コマンド ラインで Option Compare を設定するには</span><span class="sxs-lookup"><span data-stu-id="72e9a-139">To set Option Compare on the command line</span></span>  
  
-   <span data-ttu-id="72e9a-140">含める、 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)コンパイラ オプションで、 **vbc**コマンドです。</span><span class="sxs-lookup"><span data-stu-id="72e9a-140">Include the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72e9a-141">例</span><span class="sxs-lookup"><span data-stu-id="72e9a-141">Example</span></span>  
 <span data-ttu-id="72e9a-142">次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法としてバイナリ比較を設定します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-142">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="72e9a-143">このコードを使用するには、`Option Compare Binary` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-143">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 <span data-ttu-id="72e9a-144">[!code-vb[VbVbalrStatements #&45;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="72e9a-144">[!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="72e9a-145">例</span><span class="sxs-lookup"><span data-stu-id="72e9a-145">Example</span></span>  
 <span data-ttu-id="72e9a-146">次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法として大文字と小文字を区別しないテキスト並べ替え順序を設定します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-146">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="72e9a-147">このコードを使用するには、`Option Compare Text` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。</span><span class="sxs-lookup"><span data-stu-id="72e9a-147">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 <span data-ttu-id="72e9a-148">[!code-vb[VbVbalrStatements&#46;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="72e9a-148">[!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e9a-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="72e9a-149">See Also</span></span>  
 <span data-ttu-id="72e9a-150"><xref:Microsoft.VisualBasic.Strings.InStr%2A></xref:Microsoft.VisualBasic.Strings.InStr%2A></span><span class="sxs-lookup"><span data-stu-id="72e9a-150"><xref:Microsoft.VisualBasic.Strings.InStr%2A></span></span>   
 <span data-ttu-id="72e9a-151"><xref:Microsoft.VisualBasic.Strings.InStrRev%2A></xref:Microsoft.VisualBasic.Strings.InStrRev%2A></span><span class="sxs-lookup"><span data-stu-id="72e9a-151"><xref:Microsoft.VisualBasic.Strings.InStrRev%2A></span></span>   
 <span data-ttu-id="72e9a-152"><xref:Microsoft.VisualBasic.Strings.Replace%2A></xref:Microsoft.VisualBasic.Strings.Replace%2A></span><span class="sxs-lookup"><span data-stu-id="72e9a-152"><xref:Microsoft.VisualBasic.Strings.Replace%2A></span></span>   
 <span data-ttu-id="72e9a-153"><xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A></span><span class="sxs-lookup"><span data-stu-id="72e9a-153"><xref:Microsoft.VisualBasic.Strings.Split%2A></span></span>   
 <span data-ttu-id="72e9a-154"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></xref:Microsoft.VisualBasic.Strings.StrComp%2A></span><span class="sxs-lookup"><span data-stu-id="72e9a-154"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></span></span>   
<span data-ttu-id="72e9a-155"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="72e9a-155"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="72e9a-156"> [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="72e9a-156"> [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="72e9a-157"> [Visual Basic における比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="72e9a-157"> [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="72e9a-158"> [Like 演算子](../../../visual-basic/language-reference/operators/like-operator.md) </span><span class="sxs-lookup"><span data-stu-id="72e9a-158"> [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md) </span></span>  
<span data-ttu-id="72e9a-159"> [文字列関数](../../../visual-basic/language-reference/functions/string-functions.md) </span><span class="sxs-lookup"><span data-stu-id="72e9a-159"> [String Functions](../../../visual-basic/language-reference/functions/string-functions.md) </span></span>  
<span data-ttu-id="72e9a-160"> [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="72e9a-160"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="72e9a-161"> [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="72e9a-161"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
