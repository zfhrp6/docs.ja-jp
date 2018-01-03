---
title: /warnaserror (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d472795affe0df098d1551daf51a2f0ae20723ba
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="warnaserror-visual-basic"></a><span data-ttu-id="1c000-102">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c000-102">/warnaserror (Visual Basic)</span></span>
<span data-ttu-id="1c000-103">コンパイラで最初に発生した警告をエラーとして処理します。</span><span class="sxs-lookup"><span data-stu-id="1c000-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c000-104">構文</span><span class="sxs-lookup"><span data-stu-id="1c000-104">Syntax</span></span>  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1c000-105">引数</span><span class="sxs-lookup"><span data-stu-id="1c000-105">Arguments</span></span>  
  
|<span data-ttu-id="1c000-106">用語</span><span class="sxs-lookup"><span data-stu-id="1c000-106">Term</span></span>|<span data-ttu-id="1c000-107">定義</span><span class="sxs-lookup"><span data-stu-id="1c000-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="1c000-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="1c000-108">+ &#124; -</span></span>|<span data-ttu-id="1c000-109">任意。</span><span class="sxs-lookup"><span data-stu-id="1c000-109">Optional.</span></span> <span data-ttu-id="1c000-110">既定では、`/warnaserror-`が有効になります。 警告は妨げませんコンパイラ出力ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1c000-110">By default, `/warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="1c000-111">`/warnaserror`オプションは、同じとして`/warnaserror+`、警告をエラーとして扱うことです。</span><span class="sxs-lookup"><span data-stu-id="1c000-111">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="1c000-112">任意。</span><span class="sxs-lookup"><span data-stu-id="1c000-112">Optional.</span></span> <span data-ttu-id="1c000-113">警告 ID のコンマ区切りの一覧の番号を`/warnaserror`オプションが適用されます。</span><span class="sxs-lookup"><span data-stu-id="1c000-113">Comma-delimited list of the warning ID numbers to which the `/warnaserror` option applies.</span></span> <span data-ttu-id="1c000-114">警告 ID が指定されていない場合、`/warnaserror`オプションのすべての警告に適用されます。</span><span class="sxs-lookup"><span data-stu-id="1c000-114">If no warning ID is specified, the `/warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c000-115">コメント</span><span class="sxs-lookup"><span data-stu-id="1c000-115">Remarks</span></span>  
 <span data-ttu-id="1c000-116">`/warnaserror`オプションは、すべての警告をエラーとして扱います。</span><span class="sxs-lookup"><span data-stu-id="1c000-116">The `/warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="1c000-117">警告をエラーとしてレポートされる代わりに、通常は報告されるメッセージ。</span><span class="sxs-lookup"><span data-stu-id="1c000-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="1c000-118">コンパイラは警告として同じ警告のそれ以降の出現箇所を報告します。</span><span class="sxs-lookup"><span data-stu-id="1c000-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="1c000-119">既定では、`/warnaserror-`が有効で、情報提供だけを使用する警告の原因になっています。</span><span class="sxs-lookup"><span data-stu-id="1c000-119">By default, `/warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="1c000-120">`/warnaserror`オプションは、同じとして`/warnaserror+`、警告をエラーとして扱うことです。</span><span class="sxs-lookup"><span data-stu-id="1c000-120">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="1c000-121">いくつかの特定の警告のみを実行する場合に、エラーとして扱う警告番号のコンマ区切りの一覧を指定することがあります。</span><span class="sxs-lookup"><span data-stu-id="1c000-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c000-122">`/warnaserror`オプションでは、警告を表示する方法は制御しません。</span><span class="sxs-lookup"><span data-stu-id="1c000-122">The `/warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="1c000-123">使用して、 [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)警告を無効にするオプションです。</span><span class="sxs-lookup"><span data-stu-id="1c000-123">Use the [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="1c000-124">すべての警告、Visual Studio IDE でのエラーとして扱う/warnaserror を設定するには</span><span class="sxs-lookup"><span data-stu-id="1c000-124">To set /warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="1c000-125">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1c000-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1c000-126">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c000-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1c000-127">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c000-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1c000-128">3.確認してください、**すべての警告を無効にする** チェック ボックスがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="1c000-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="1c000-129">4.チェック、**すべての警告をエラーとして扱う**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="1c000-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="1c000-130">Visual Studio IDE でのエラーとして特定の警告を処理する/warnaserror を設定するには</span><span class="sxs-lookup"><span data-stu-id="1c000-130">To set /warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="1c000-131">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1c000-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1c000-132">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c000-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="1c000-133">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c000-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1c000-134">3.確認してください、**すべての警告を無効にする** チェック ボックスがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="1c000-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="1c000-135">4.確認、**すべての警告をエラーとして扱う** チェック ボックスがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="1c000-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="1c000-136">5.選択**エラー**から、**通知**をエラーとして扱う警告の横にある列です。</span><span class="sxs-lookup"><span data-stu-id="1c000-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1c000-137">例</span><span class="sxs-lookup"><span data-stu-id="1c000-137">Example</span></span>  
 <span data-ttu-id="1c000-138">次のコードのコンパイル`In.vb`し、最初に見つかった位置が見つかったすべての警告をエラーとして表示することをコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="1c000-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="1c000-139">例</span><span class="sxs-lookup"><span data-stu-id="1c000-139">Example</span></span>  
 <span data-ttu-id="1c000-140">次のコードのコンパイル`T2.vb`エラーとして使用されていないローカル変数 (42024) に対する警告のみを処理します。</span><span class="sxs-lookup"><span data-stu-id="1c000-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c000-141">参照</span><span class="sxs-lookup"><span data-stu-id="1c000-141">See Also</span></span>  
 [<span data-ttu-id="1c000-142">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1c000-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1c000-143">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="1c000-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="1c000-144">Visual Basic での警告の構成</span><span class="sxs-lookup"><span data-stu-id="1c000-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
