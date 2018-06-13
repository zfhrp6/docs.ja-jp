---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: da1bd6d3b6746561655a82cd49aa0014563a1d40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652910"
---
# <a name="-optionstrict"></a><span data-ttu-id="44f72-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="44f72-102">-optionstrict</span></span>
<span data-ttu-id="44f72-103">暗黙の型変換を制限するための厳密な型のセマンティクスを適用します。</span><span class="sxs-lookup"><span data-stu-id="44f72-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f72-104">構文</span><span class="sxs-lookup"><span data-stu-id="44f72-104">Syntax</span></span>  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="44f72-105">引数</span><span class="sxs-lookup"><span data-stu-id="44f72-105">Arguments</span></span>  
 <span data-ttu-id="44f72-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="44f72-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="44f72-107">任意。</span><span class="sxs-lookup"><span data-stu-id="44f72-107">Optional.</span></span> <span data-ttu-id="44f72-108">`-optionstrict+`オプションは暗黙の型変換を制限します。</span><span class="sxs-lookup"><span data-stu-id="44f72-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="44f72-109">このオプションの既定値は`-optionstrict-`します。</span><span class="sxs-lookup"><span data-stu-id="44f72-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="44f72-110">`-optionstrict+`オプションは、同じ`-optionstrict`です。</span><span class="sxs-lookup"><span data-stu-id="44f72-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="44f72-111">寛容な型の両方を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="44f72-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="44f72-112">必須。</span><span class="sxs-lookup"><span data-stu-id="44f72-112">Required.</span></span> <span data-ttu-id="44f72-113">厳密な言語セマンティクスが守られていない場合に警告します。</span><span class="sxs-lookup"><span data-stu-id="44f72-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44f72-114">コメント</span><span class="sxs-lookup"><span data-stu-id="44f72-114">Remarks</span></span>  
 <span data-ttu-id="44f72-115">ときに`-optionstrict+`が有効になって、唯一の拡大型変換は暗黙的に行われたことができます。</span><span class="sxs-lookup"><span data-stu-id="44f72-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="44f72-116">暗黙的な縮小の割り当てなどの型変換、`Decimal`オブジェクト、整数型のオブジェクトへの入力、エラーとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="44f72-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="44f72-117">暗黙的な縮小の型変換の警告を生成するには、使用`-optionstrict:custom`です。</span><span class="sxs-lookup"><span data-stu-id="44f72-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="44f72-118">使用して`-nowarn:numberlist`特定の警告を無視して`-warnaserror:numberlist`特定の警告をエラーとして処理します。</span><span class="sxs-lookup"><span data-stu-id="44f72-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="44f72-119">Visual Studio IDE で-optionstrict を設定するには</span><span class="sxs-lookup"><span data-stu-id="44f72-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="44f72-120">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="44f72-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="44f72-121">**プロジェクト** メニューのをクリックして**プロパティです。**</span><span class="sxs-lookup"><span data-stu-id="44f72-121">On the **Project** menu, click **Properties.**</span></span>   
  
2.  <span data-ttu-id="44f72-122">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="44f72-122">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="44f72-123">値を変更、 **Option Strict**ボックス。</span><span class="sxs-lookup"><span data-stu-id="44f72-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="44f72-124">-Optionstrict をコードから設定するには</span><span class="sxs-lookup"><span data-stu-id="44f72-124">To set -optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="44f72-125">参照してください[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="44f72-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f72-126">例</span><span class="sxs-lookup"><span data-stu-id="44f72-126">Example</span></span>  
 <span data-ttu-id="44f72-127">次のコードのコンパイル`Test.vb`厳密な型のセマンティクスを使用します。</span><span class="sxs-lookup"><span data-stu-id="44f72-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="44f72-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="44f72-128">See Also</span></span>  
 [<span data-ttu-id="44f72-129">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="44f72-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="44f72-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="44f72-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="44f72-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="44f72-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="44f72-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="44f72-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="44f72-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="44f72-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="44f72-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44f72-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="44f72-135">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="44f72-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="44f72-136">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="44f72-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 <span data-ttu-id="44f72-137">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="44f72-137">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
