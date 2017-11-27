---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6f602e0b0b23345bf1f5aae843bd44bd2642bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="optioncompare"></a><span data-ttu-id="e48b7-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="e48b7-102">/optioncompare</span></span>
<span data-ttu-id="e48b7-103">文字列比較の方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e48b7-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e48b7-104">構文</span><span class="sxs-lookup"><span data-stu-id="e48b7-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="e48b7-105">コメント</span><span class="sxs-lookup"><span data-stu-id="e48b7-105">Remarks</span></span>  
 <span data-ttu-id="e48b7-106">指定できます`/optioncompare`で 2 つの形式のいずれかの:`/optioncompare:binary`バイナリ文字列比較を使用して`/optioncompare:text`テキスト文字列の比較を使用します。</span><span class="sxs-lookup"><span data-stu-id="e48b7-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="e48b7-107">既定では、コンパイラを使用して`/optioncompare:binary`です。</span><span class="sxs-lookup"><span data-stu-id="e48b7-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="e48b7-108">Microsoft Windows では、使用されているコード ページは、バイナリ並べ替え順を決定します。</span><span class="sxs-lookup"><span data-stu-id="e48b7-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="e48b7-109">通常、バイナリ並べ替え順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e48b7-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="e48b7-110">テキストに基づく文字列比較は、システムのロケールによって決まる、大文字と小文字のテキストの並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="e48b7-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="e48b7-111">一般的なテキストの並べ替え順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e48b7-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="e48b7-112">Visual Studio IDE で/optioncompare を設定するには</span><span class="sxs-lookup"><span data-stu-id="e48b7-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="e48b7-113">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e48b7-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e48b7-114">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e48b7-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="e48b7-115">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e48b7-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="e48b7-116">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e48b7-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="e48b7-117">値を変更、 **Option Compare**ボックス。</span><span class="sxs-lookup"><span data-stu-id="e48b7-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="e48b7-118">/Optioncompare をコードから設定するには</span><span class="sxs-lookup"><span data-stu-id="e48b7-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="e48b7-119">参照してください[Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="e48b7-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e48b7-120">例</span><span class="sxs-lookup"><span data-stu-id="e48b7-120">Example</span></span>  
 <span data-ttu-id="e48b7-121">次のコードのコンパイル`ProjFile.vb`バイナリ文字列比較を使用しています。</span><span class="sxs-lookup"><span data-stu-id="e48b7-121">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e48b7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e48b7-122">See Also</span></span>  
 [<span data-ttu-id="e48b7-123">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="e48b7-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e48b7-124">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e48b7-124">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="e48b7-125">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="e48b7-125">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="e48b7-126">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="e48b7-126">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="e48b7-127">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="e48b7-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="e48b7-128">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="e48b7-128">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 <span data-ttu-id="e48b7-129">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="e48b7-129">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
