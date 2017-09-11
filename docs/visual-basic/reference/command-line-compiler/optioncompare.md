---
title: "/optioncompare |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
dev_langs:
- VB
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
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
ms.openlocfilehash: c9512427cda0b6a3bcb0c1fe338b47ff9f779d19
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="optioncompare"></a><span data-ttu-id="e99ec-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="e99ec-102">/optioncompare</span></span>
<span data-ttu-id="e99ec-103">文字列比較の方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e99ec-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e99ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="e99ec-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="e99ec-105">コメント</span><span class="sxs-lookup"><span data-stu-id="e99ec-105">Remarks</span></span>  
 <span data-ttu-id="e99ec-106">指定できます`/optioncompare`で&2; つの形式:`/optioncompare:binary`バイナリ文字列比較を使用して`/optioncompare:text`テキスト文字列の比較を使用します。</span><span class="sxs-lookup"><span data-stu-id="e99ec-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="e99ec-107">既定では、コンパイラを使用して`/optioncompare:binary`します。</span><span class="sxs-lookup"><span data-stu-id="e99ec-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="e99ec-108">Microsoft Windows では、使用されているコード ページは、バイナリ並べ替え順を決定します。</span><span class="sxs-lookup"><span data-stu-id="e99ec-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="e99ec-109">一般的なバイナリ並べ替え順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e99ec-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="e99ec-110">テキスト ベースの文字列比較は、システムのロケールで決定される小文字を区別しないテキスト並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="e99ec-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="e99ec-111">一般的なテキストの並べ替え順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e99ec-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="e99ec-112">Visual Studio IDE で/optioncompare を設定するには</span><span class="sxs-lookup"><span data-stu-id="e99ec-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="e99ec-113">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e99ec-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e99ec-114">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="e99ec-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="e99ec-115">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e99ec-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="e99ec-116">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e99ec-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="e99ec-117">値を変更、 **Option Compare**ボックス。</span><span class="sxs-lookup"><span data-stu-id="e99ec-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="e99ec-118">/Optioncompare をコードから設定するには</span><span class="sxs-lookup"><span data-stu-id="e99ec-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="e99ec-119">参照してください[Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="e99ec-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e99ec-120">例</span><span class="sxs-lookup"><span data-stu-id="e99ec-120">Example</span></span>  
 <span data-ttu-id="e99ec-121">次のコードでは、P`rojFile.vb`バイナリ文字列比較を使用しています。</span><span class="sxs-lookup"><span data-stu-id="e99ec-121">The following code compiles P`rojFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e99ec-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e99ec-122">See Also</span></span>  
 <span data-ttu-id="e99ec-123">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="e99ec-123">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="e99ec-124"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="e99ec-124"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="e99ec-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="e99ec-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="e99ec-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="e99ec-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="e99ec-127"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="e99ec-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="e99ec-128"> [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e99ec-128"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="e99ec-129"> [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="e99ec-129"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
