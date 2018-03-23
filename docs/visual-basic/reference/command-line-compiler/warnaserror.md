---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ae8ed68045529e626f2788f854d8e6a6933e7e2
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="6ec04-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ec04-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="6ec04-103">コンパイラで最初に発生した警告をエラーとして処理します。</span><span class="sxs-lookup"><span data-stu-id="6ec04-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec04-104">構文</span><span class="sxs-lookup"><span data-stu-id="6ec04-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ec04-105">引数</span><span class="sxs-lookup"><span data-stu-id="6ec04-105">Arguments</span></span>  
  
|<span data-ttu-id="6ec04-106">用語</span><span class="sxs-lookup"><span data-stu-id="6ec04-106">Term</span></span>|<span data-ttu-id="6ec04-107">定義</span><span class="sxs-lookup"><span data-stu-id="6ec04-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="6ec04-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="6ec04-108">+ &#124; -</span></span>|<span data-ttu-id="6ec04-109">任意。</span><span class="sxs-lookup"><span data-stu-id="6ec04-109">Optional.</span></span> <span data-ttu-id="6ec04-110">既定では、`-warnaserror-`が有効になります。 警告は妨げませんコンパイラ出力ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ec04-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="6ec04-111">`-warnaserror`オプションは、同じとして`-warnaserror+`、警告をエラーとして扱うことです。</span><span class="sxs-lookup"><span data-stu-id="6ec04-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="6ec04-112">任意。</span><span class="sxs-lookup"><span data-stu-id="6ec04-112">Optional.</span></span> <span data-ttu-id="6ec04-113">警告 ID のコンマ区切りの一覧の番号を`-warnaserror`オプションが適用されます。</span><span class="sxs-lookup"><span data-stu-id="6ec04-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="6ec04-114">警告 ID が指定されていない場合、`-warnaserror`オプションのすべての警告に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6ec04-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ec04-115">コメント</span><span class="sxs-lookup"><span data-stu-id="6ec04-115">Remarks</span></span>  
 <span data-ttu-id="6ec04-116">`-warnaserror`オプションは、すべての警告をエラーとして扱います。</span><span class="sxs-lookup"><span data-stu-id="6ec04-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="6ec04-117">警告をエラーとしてレポートされる代わりに、通常は報告されるメッセージ。</span><span class="sxs-lookup"><span data-stu-id="6ec04-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="6ec04-118">コンパイラは警告として同じ警告のそれ以降の出現箇所を報告します。</span><span class="sxs-lookup"><span data-stu-id="6ec04-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="6ec04-119">既定では、`-warnaserror-`が有効で、情報提供だけを使用する警告の原因になっています。</span><span class="sxs-lookup"><span data-stu-id="6ec04-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="6ec04-120">`-warnaserror`オプションは、同じとして`-warnaserror+`、警告をエラーとして扱うことです。</span><span class="sxs-lookup"><span data-stu-id="6ec04-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="6ec04-121">いくつかの特定の警告のみを実行する場合に、エラーとして扱う警告番号のコンマ区切りの一覧を指定することがあります。</span><span class="sxs-lookup"><span data-stu-id="6ec04-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ec04-122">`-warnaserror`オプションでは、警告を表示する方法は制御しません。</span><span class="sxs-lookup"><span data-stu-id="6ec04-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="6ec04-123">使用して、 [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)警告を無効にするオプションです。</span><span class="sxs-lookup"><span data-stu-id="6ec04-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="6ec04-124">すべての警告、Visual Studio IDE でのエラーとして扱う-warnaserror を設定するには</span><span class="sxs-lookup"><span data-stu-id="6ec04-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="6ec04-125">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="6ec04-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6ec04-126">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ec04-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="6ec04-127">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ec04-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="6ec04-128">3.確認してください、**すべての警告を無効にする** チェック ボックスがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="6ec04-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="6ec04-129">4.チェック、**すべての警告をエラーとして扱う**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="6ec04-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="6ec04-130">Visual Studio IDE でのエラーとして特定の警告を処理する-warnaserror を設定するには</span><span class="sxs-lookup"><span data-stu-id="6ec04-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="6ec04-131">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="6ec04-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6ec04-132">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ec04-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="6ec04-133">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6ec04-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="6ec04-134">3.確認してください、**すべての警告を無効にする** チェック ボックスがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="6ec04-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="6ec04-135">4.確認、**すべての警告をエラーとして扱う** チェック ボックスがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="6ec04-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="6ec04-136">5.選択**エラー**から、**通知**をエラーとして扱う警告の横にある列です。</span><span class="sxs-lookup"><span data-stu-id="6ec04-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6ec04-137">例</span><span class="sxs-lookup"><span data-stu-id="6ec04-137">Example</span></span>  
 <span data-ttu-id="6ec04-138">次のコードのコンパイル`In.vb`し、最初に見つかった位置が見つかったすべての警告をエラーとして表示することをコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="6ec04-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="6ec04-139">例</span><span class="sxs-lookup"><span data-stu-id="6ec04-139">Example</span></span>  
 <span data-ttu-id="6ec04-140">次のコードのコンパイル`T2.vb`エラーとして使用されていないローカル変数 (42024) に対する警告のみを処理します。</span><span class="sxs-lookup"><span data-stu-id="6ec04-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ec04-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ec04-141">See Also</span></span>  
 [<span data-ttu-id="6ec04-142">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="6ec04-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="6ec04-143">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="6ec04-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="6ec04-144">Visual Basic での警告の構成</span><span class="sxs-lookup"><span data-stu-id="6ec04-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
