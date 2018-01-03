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
ms.openlocfilehash: 62669ec40803170cb623382b09472b82121d26bb
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="define-visual-basic"></a><span data-ttu-id="1d304-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d304-102">/define (Visual Basic)</span></span>
<span data-ttu-id="1d304-103">条件付きコンパイル定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="1d304-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d304-104">構文</span><span class="sxs-lookup"><span data-stu-id="1d304-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d304-105">引数</span><span class="sxs-lookup"><span data-stu-id="1d304-105">Arguments</span></span>  
  
|<span data-ttu-id="1d304-106">用語</span><span class="sxs-lookup"><span data-stu-id="1d304-106">Term</span></span>|<span data-ttu-id="1d304-107">定義</span><span class="sxs-lookup"><span data-stu-id="1d304-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="1d304-108">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="1d304-108">Required.</span></span> <span data-ttu-id="1d304-109">定義する記号。</span><span class="sxs-lookup"><span data-stu-id="1d304-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="1d304-110">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1d304-110">Optional.</span></span> <span data-ttu-id="1d304-111">`symbol` に代入する値。</span><span class="sxs-lookup"><span data-stu-id="1d304-111">The value to assign `symbol`.</span></span> <span data-ttu-id="1d304-112">場合`value`文字列で、バック スラッシュ/引用符のシーケンスで囲む必要があります (\\") 引用符の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="1d304-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="1d304-113">値が指定されていない場合は、True として処理されます。</span><span class="sxs-lookup"><span data-stu-id="1d304-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d304-114">コメント</span><span class="sxs-lookup"><span data-stu-id="1d304-114">Remarks</span></span>  
 <span data-ttu-id="1d304-115">`/define` オプションは、ソース ファイル内で `#Const` プリプロセッサ ディレクティブを使用するのと同じ効果を持ちます。ただし、`/define` で定義された定数は public で、プロジェクト内のすべてのファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1d304-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="1d304-116">このオプションで作成される記号を `#If`...`Then`...`#Else` ディレクティブで使用すると、ソース ファイルを条件付きでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="1d304-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="1d304-117">`/d` は `/define` の省略形です。</span><span class="sxs-lookup"><span data-stu-id="1d304-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="1d304-118">記号の定義をコンマで区切ると、`/define` を使用して複数の記号を定義できます。</span><span class="sxs-lookup"><span data-stu-id="1d304-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="1d304-119">Visual Studio 統合開発環境で /define を設定するには</span><span class="sxs-lookup"><span data-stu-id="1d304-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1d304-120">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1d304-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1d304-121">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d304-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1d304-122">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d304-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1d304-123">3.**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d304-123">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="1d304-124">4.値を変更、**カスタム定数**ボックス。</span><span class="sxs-lookup"><span data-stu-id="1d304-124">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d304-125">例</span><span class="sxs-lookup"><span data-stu-id="1d304-125">Example</span></span>  
 <span data-ttu-id="1d304-126">2 つの条件付きコンパイル定数を定義して使用する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d304-126">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1d304-127">参照</span><span class="sxs-lookup"><span data-stu-id="1d304-127">See Also</span></span>  
 [<span data-ttu-id="1d304-128">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1d304-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1d304-129">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="1d304-129">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="1d304-130">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="1d304-130">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="1d304-131">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="1d304-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
