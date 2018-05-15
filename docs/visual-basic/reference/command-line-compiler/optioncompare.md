---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1906710ef10634187782f9355146dfa7ccb7748
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-optioncompare"></a><span data-ttu-id="4790f-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="4790f-102">-optioncompare</span></span>
<span data-ttu-id="4790f-103">文字列比較の方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="4790f-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4790f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4790f-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="4790f-105">コメント</span><span class="sxs-lookup"><span data-stu-id="4790f-105">Remarks</span></span>  
 <span data-ttu-id="4790f-106">指定できます`-optioncompare`で 2 つの形式のいずれかの:`-optioncompare:binary`バイナリ文字列比較を使用して`-optioncompare:text`テキスト文字列の比較を使用します。</span><span class="sxs-lookup"><span data-stu-id="4790f-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="4790f-107">既定では、コンパイラを使用して`-optioncompare:binary`です。</span><span class="sxs-lookup"><span data-stu-id="4790f-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="4790f-108">Microsoft Windows では、現在のコード ページは、バイナリ並べ替え順を決定します。</span><span class="sxs-lookup"><span data-stu-id="4790f-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="4790f-109">通常、バイナリ並べ替え順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4790f-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="4790f-110">テキストに基づく文字列比較は、システムのロケールによって決まる、大文字と小文字のテキストの並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="4790f-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="4790f-111">一般的なテキストの並べ替え順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4790f-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="4790f-112">Visual Studio IDE で-optioncompare を設定するには</span><span class="sxs-lookup"><span data-stu-id="4790f-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="4790f-113">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="4790f-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4790f-114">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4790f-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="4790f-115">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4790f-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="4790f-116">値を変更、 **Option Compare**ボックス。</span><span class="sxs-lookup"><span data-stu-id="4790f-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="4790f-117">-Optioncompare をコードから設定するには</span><span class="sxs-lookup"><span data-stu-id="4790f-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="4790f-118">参照してください[Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="4790f-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4790f-119">例</span><span class="sxs-lookup"><span data-stu-id="4790f-119">Example</span></span>  
 <span data-ttu-id="4790f-120">次のコードのコンパイル`ProjFile.vb`バイナリ文字列比較を使用しています。</span><span class="sxs-lookup"><span data-stu-id="4790f-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4790f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="4790f-121">See Also</span></span>  
 [<span data-ttu-id="4790f-122">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="4790f-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4790f-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="4790f-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="4790f-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="4790f-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="4790f-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="4790f-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="4790f-126">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="4790f-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="4790f-127">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="4790f-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 <span data-ttu-id="4790f-128">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="4790f-128">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
