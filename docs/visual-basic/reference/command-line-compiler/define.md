---
title: "/define (Visual Basic) |Microsoft ドキュメント"
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
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: 15
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
ms.openlocfilehash: e4eac32b4ab7259b9d3fd2ec37e21406c4cec326
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="define-visual-basic"></a><span data-ttu-id="fa916-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa916-102">/define (Visual Basic)</span></span>
<span data-ttu-id="fa916-103">条件付きコンパイル定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="fa916-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa916-104">構文</span><span class="sxs-lookup"><span data-stu-id="fa916-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa916-105">引数</span><span class="sxs-lookup"><span data-stu-id="fa916-105">Arguments</span></span>  
  
|<span data-ttu-id="fa916-106">用語</span><span class="sxs-lookup"><span data-stu-id="fa916-106">Term</span></span>|<span data-ttu-id="fa916-107">定義</span><span class="sxs-lookup"><span data-stu-id="fa916-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="fa916-108">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="fa916-108">Required.</span></span> <span data-ttu-id="fa916-109">定義する記号。</span><span class="sxs-lookup"><span data-stu-id="fa916-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="fa916-110">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="fa916-110">Optional.</span></span> <span data-ttu-id="fa916-111">`symbol` に代入する値。</span><span class="sxs-lookup"><span data-stu-id="fa916-111">The value to assign `symbol`.</span></span> <span data-ttu-id="fa916-112">場合`value`文字列では、バック スラッシュ/引用符のシーケンスで囲む必要があります (\\") 引用符の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="fa916-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="fa916-113">値が指定されていない場合は、True として処理されます。</span><span class="sxs-lookup"><span data-stu-id="fa916-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa916-114">コメント</span><span class="sxs-lookup"><span data-stu-id="fa916-114">Remarks</span></span>  
 <span data-ttu-id="fa916-115">`/define` オプションは、ソース ファイル内で `#Const` プリプロセッサ ディレクティブを使用するのと同じ効果を持ちます。ただし、`/define` で定義された定数は public で、プロジェクト内のすべてのファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="fa916-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="fa916-116">このオプションで作成される記号を `#If`...`Then`...`#Else` ディレクティブで使用すると、ソース ファイルを条件付きでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="fa916-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="fa916-117">`/d` は `/define` の省略形です。</span><span class="sxs-lookup"><span data-stu-id="fa916-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="fa916-118">記号の定義をコンマで区切ると、`/define` を使用して複数の記号を定義できます。</span><span class="sxs-lookup"><span data-stu-id="fa916-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="fa916-119">Visual Studio 統合開発環境で /define を設定するには</span><span class="sxs-lookup"><span data-stu-id="fa916-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="fa916-120">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="fa916-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fa916-121">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="fa916-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="fa916-122">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa916-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="fa916-123">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa916-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="fa916-124">3.[ **詳細設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa916-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="fa916-125">4.値を変更、**カスタム定数**ボックス。</span><span class="sxs-lookup"><span data-stu-id="fa916-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fa916-126">例</span><span class="sxs-lookup"><span data-stu-id="fa916-126">Example</span></span>  
 <span data-ttu-id="fa916-127">2 つの条件付きコンパイル定数を定義して使用する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fa916-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 <span data-ttu-id="fa916-128">[!code-vb[VbVbalrCompiler #&45;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fa916-128">[!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa916-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa916-129">See Also</span></span>  
 <span data-ttu-id="fa916-130">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="fa916-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="fa916-131"> [#If.#Else ディレクティブ。](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="fa916-131"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="fa916-132"> [#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md) </span><span class="sxs-lookup"><span data-stu-id="fa916-132"> [#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) </span></span>  
<span data-ttu-id="fa916-133"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="fa916-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
