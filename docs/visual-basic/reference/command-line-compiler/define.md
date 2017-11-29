---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a><span data-ttu-id="cfb88-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfb88-102">/define (Visual Basic)</span></span>
<span data-ttu-id="cfb88-103">条件付きコンパイル定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="cfb88-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb88-104">構文</span><span class="sxs-lookup"><span data-stu-id="cfb88-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="cfb88-105">引数</span><span class="sxs-lookup"><span data-stu-id="cfb88-105">Arguments</span></span>  
  
|<span data-ttu-id="cfb88-106">用語</span><span class="sxs-lookup"><span data-stu-id="cfb88-106">Term</span></span>|<span data-ttu-id="cfb88-107">定義</span><span class="sxs-lookup"><span data-stu-id="cfb88-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="cfb88-108">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="cfb88-108">Required.</span></span> <span data-ttu-id="cfb88-109">定義する記号。</span><span class="sxs-lookup"><span data-stu-id="cfb88-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="cfb88-110">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="cfb88-110">Optional.</span></span> <span data-ttu-id="cfb88-111">`symbol` に代入する値。</span><span class="sxs-lookup"><span data-stu-id="cfb88-111">The value to assign `symbol`.</span></span> <span data-ttu-id="cfb88-112">場合`value`文字列で、バック スラッシュ/引用符のシーケンスで囲む必要があります (\\") 引用符の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="cfb88-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="cfb88-113">値が指定されていない場合は、True として処理されます。</span><span class="sxs-lookup"><span data-stu-id="cfb88-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfb88-114">コメント</span><span class="sxs-lookup"><span data-stu-id="cfb88-114">Remarks</span></span>  
 <span data-ttu-id="cfb88-115">`/define` オプションは、ソース ファイル内で `#Const` プリプロセッサ ディレクティブを使用するのと同じ効果を持ちます。ただし、`/define` で定義された定数は public で、プロジェクト内のすべてのファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="cfb88-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="cfb88-116">このオプションで作成される記号を `#If`...`Then`...`#Else` ディレクティブで使用すると、ソース ファイルを条件付きでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="cfb88-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="cfb88-117">`/d` は `/define` の省略形です。</span><span class="sxs-lookup"><span data-stu-id="cfb88-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="cfb88-118">記号の定義をコンマで区切ると、`/define` を使用して複数の記号を定義できます。</span><span class="sxs-lookup"><span data-stu-id="cfb88-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="cfb88-119">Visual Studio 統合開発環境で /define を設定するには</span><span class="sxs-lookup"><span data-stu-id="cfb88-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="cfb88-120">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="cfb88-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="cfb88-121">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfb88-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="cfb88-122">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfb88-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="cfb88-123">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfb88-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="cfb88-124">3.**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cfb88-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="cfb88-125">4.値を変更、**カスタム定数**ボックス。</span><span class="sxs-lookup"><span data-stu-id="cfb88-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cfb88-126">例</span><span class="sxs-lookup"><span data-stu-id="cfb88-126">Example</span></span>  
 <span data-ttu-id="cfb88-127">2 つの条件付きコンパイル定数を定義して使用する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cfb88-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cfb88-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfb88-128">See Also</span></span>  
 [<span data-ttu-id="cfb88-129">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="cfb88-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="cfb88-130">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="cfb88-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="cfb88-131">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="cfb88-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="cfb88-132">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="cfb88-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
