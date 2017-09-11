---
title: "/optioninfer |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioninfer
dev_langs:
- VB
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: 19
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
ms.openlocfilehash: 4bcc35da2a255ca75805c8a918027d2ccb61b154
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="optioninfer"></a><span data-ttu-id="e7d3d-102">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="e7d3d-102">/optioninfer</span></span>
<span data-ttu-id="e7d3d-103">変数宣言でローカル型推論を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d3d-104">構文</span><span class="sxs-lookup"><span data-stu-id="e7d3d-104">Syntax</span></span>  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7d3d-105">引数</span><span class="sxs-lookup"><span data-stu-id="e7d3d-105">Arguments</span></span>  
  
|<span data-ttu-id="e7d3d-106">用語</span><span class="sxs-lookup"><span data-stu-id="e7d3d-106">Term</span></span>|<span data-ttu-id="e7d3d-107">定義</span><span class="sxs-lookup"><span data-stu-id="e7d3d-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="e7d3d-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e7d3d-108">`+` &#124; `-`</span></span>|<span data-ttu-id="e7d3d-109">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-109">Optional.</span></span> <span data-ttu-id="e7d3d-110">`/optioninfer+` を指定してローカル型推論を有効にするか、または `/optioninfer-` を指定してローカル型推論をブロックします。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-110">Specify `/optioninfer+` to enable local type inference, or `/optioninfer-` to block it.</span></span> <span data-ttu-id="e7d3d-111">`/optioninfer` オプションは、何も値を指定しない場合、`/optioninfer+` と同じです。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-111">The `/optioninfer` option, with no value specified, is the same as `/optioninfer+`.</span></span> <span data-ttu-id="e7d3d-112">`/optioninfer` スイッチが存在しない場合の既定値も `/optioninfer+` です。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-112">The default value when the `/optioninfer` switch is not present is also `/optioninfer+`.</span></span> <span data-ttu-id="e7d3d-113">既定値は、Vbc.rsp 応答ファイル内に設定されています。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e7d3d-114">`/noconfig` オプションを使用すると、vbc.rsp に指定するのではなく、コンパイラの内部既定値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-114">You can use the `/noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="e7d3d-115">このオプションのコンパイラの既定値は `/optioninfer-` です。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-115">The compiler default for this option is `/optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7d3d-116">コメント</span><span class="sxs-lookup"><span data-stu-id="e7d3d-116">Remarks</span></span>  
 <span data-ttu-id="e7d3d-117">ソース コード ファイルが含まれている場合、 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)、ステートメントのオーバーライド、`/optioninfer`コマンド ライン コンパイラ設定します。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `/optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="e7d3d-118">Visual Studio IDE で /optioninfer を設定するには</span><span class="sxs-lookup"><span data-stu-id="e7d3d-118">To set /optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="e7d3d-119">プロジェクトを選択**ソリューション エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="e7d3d-120">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="e7d3d-121">詳細については、次を参照してください。 [NIB: プロジェクト デザイナーでプロジェクトのプロパティを管理する](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)です。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-121">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="e7d3d-122">**コンパイル** タブの値を変更、 **Option infer**ボックス。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7d3d-123">例</span><span class="sxs-lookup"><span data-stu-id="e7d3d-123">Example</span></span>  
 <span data-ttu-id="e7d3d-124">次のコードは、ローカル型推論を有効にした状態で `test.vb` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e7d3d-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7d3d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7d3d-125">See Also</span></span>  
 <span data-ttu-id="e7d3d-126">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="e7d3d-127"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-127"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="e7d3d-128"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-128"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="e7d3d-129"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-129"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="e7d3d-130"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="e7d3d-131"> [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-131"> [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="e7d3d-132"> [ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-132"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="e7d3d-133"> [Visual Basic プロジェクトでは、既定の設定オプション ダイアログ ボックス](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-133"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span></span>  
<span data-ttu-id="e7d3d-134"> [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-134"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="e7d3d-135"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="e7d3d-135"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="e7d3d-136"> [コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)</span><span class="sxs-lookup"><span data-stu-id="e7d3d-136"> [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)</span></span>
