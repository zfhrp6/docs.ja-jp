---
title: "/optionstrict |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionstrict
dev_langs:
- VB
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
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
ms.openlocfilehash: c22445cb53ca4f5621cf7aa69ab840b26f8e08c9
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="optionstrict"></a><span data-ttu-id="8ee8f-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="8ee8f-102">/optionstrict</span></span>
<span data-ttu-id="8ee8f-103">暗黙の型変換を制限するための厳密な型のセマンティクスを適用します。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee8f-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ee8f-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8ee8f-105">引数</span><span class="sxs-lookup"><span data-stu-id="8ee8f-105">Arguments</span></span>  
 <span data-ttu-id="8ee8f-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8ee8f-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="8ee8f-107">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-107">Optional.</span></span> <span data-ttu-id="8ee8f-108">`/optionstrict+`オプションは暗黙の型変換を制限します。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="8ee8f-109">このオプションの既定値は`/optionstrict-`です。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="8ee8f-110">`/optionstrict+`オプションは、同じ`/optionstrict`します。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="8ee8f-111">寛容な型の両方を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="8ee8f-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-112">Required.</span></span> <span data-ttu-id="8ee8f-113">厳密な言語セマンティクスが守られていないときに警告します。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ee8f-114">コメント</span><span class="sxs-lookup"><span data-stu-id="8ee8f-114">Remarks</span></span>  
 <span data-ttu-id="8ee8f-115">`/optionstrict+`が有効で唯一の拡大型の変換を暗黙的に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="8ee8f-116">暗黙的な縮小の割り当てなどの型変換、`Decimal`整数型のオブジェクトをオブジェクトの入力をエラーとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="8ee8f-117">暗黙的な縮小の型変換の警告を生成する`/optionstrict:custom`です。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="8ee8f-118">使用`/nowarn:numberlist`特定の警告を無視して`/warnaserror:numberlist`特定の警告をエラーとして処理します。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="8ee8f-119">Visual Studio IDE で/optionstrict を設定するには</span><span class="sxs-lookup"><span data-stu-id="8ee8f-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="8ee8f-120">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8ee8f-121">**プロジェクト** メニューのをクリックして**プロパティです。**</span><span class="sxs-lookup"><span data-stu-id="8ee8f-121">On the **Project** menu, click **Properties.**</span></span> <span data-ttu-id="8ee8f-122">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="8ee8f-123">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-123">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="8ee8f-124">値を変更、 **Option Strict**ボックス。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-124">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="8ee8f-125">/Optionstrict をコードから設定するには</span><span class="sxs-lookup"><span data-stu-id="8ee8f-125">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="8ee8f-126">参照してください[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-126">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ee8f-127">例</span><span class="sxs-lookup"><span data-stu-id="8ee8f-127">Example</span></span>  
 <span data-ttu-id="8ee8f-128">次のコードのコンパイル`Test.vb`厳密な型変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="8ee8f-128">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ee8f-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ee8f-129">See Also</span></span>  
 <span data-ttu-id="8ee8f-130">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="8ee8f-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="8ee8f-131"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="8ee8f-131"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="8ee8f-132"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="8ee8f-132"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="8ee8f-133"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="8ee8f-133"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="8ee8f-134"> [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) </span><span class="sxs-lookup"><span data-stu-id="8ee8f-134"> [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) </span></span>  
<span data-ttu-id="8ee8f-135"> [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md) </span><span class="sxs-lookup"><span data-stu-id="8ee8f-135"> [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md) </span></span>  
<span data-ttu-id="8ee8f-136"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="8ee8f-136"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="8ee8f-137"> [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8ee8f-137"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="8ee8f-138"> [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="8ee8f-138"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
