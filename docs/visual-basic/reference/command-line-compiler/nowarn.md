---
title: /nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1eafe8d7ccd6f2c71b754dadc343518948e7146
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="nowarn"></a><span data-ttu-id="aa0a2-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="aa0a2-102">/nowarn</span></span>
<span data-ttu-id="aa0a2-103">警告を生成するコンパイラの機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa0a2-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa0a2-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="aa0a2-105">引数</span><span class="sxs-lookup"><span data-stu-id="aa0a2-105">Arguments</span></span>  
  
|<span data-ttu-id="aa0a2-106">用語</span><span class="sxs-lookup"><span data-stu-id="aa0a2-106">Term</span></span>|<span data-ttu-id="aa0a2-107">定義</span><span class="sxs-lookup"><span data-stu-id="aa0a2-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="aa0a2-108">任意。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-108">Optional.</span></span> <span data-ttu-id="aa0a2-109">コンパイラはしないようにする警告の ID 番号のコンマ区切り一覧。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="aa0a2-110">警告の Id が指定されていない場合、すべての警告は抑制されます。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa0a2-111">コメント</span><span class="sxs-lookup"><span data-stu-id="aa0a2-111">Remarks</span></span>  
 <span data-ttu-id="aa0a2-112">`/nowarn`オプションにより、コンパイラの警告を生成しないことができます。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="aa0a2-113">個々 の警告を抑制するのに警告の ID を指定、`/nowarn`コロンの後ろのオプションです。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="aa0a2-114">複数の警告番号をカンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="aa0a2-115">警告 id の数値の一部だけを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="aa0a2-116">たとえば、BC42024、未使用のローカル変数に対する警告を抑制する場合を指定`/nowarn:42024`です。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="aa0a2-117">警告 ID 番号の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="aa0a2-118">開発環境を統合するには、Visual Studio での/nowarn の設定</span><span class="sxs-lookup"><span data-stu-id="aa0a2-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="aa0a2-119">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="aa0a2-120">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="aa0a2-121">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="aa0a2-122">3.選択、**すべての警告を無効にする**すべての警告を無効にする チェック ボックスです。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="aa0a2-123">または</span><span class="sxs-lookup"><span data-stu-id="aa0a2-123">- or -</span></span><br />     <span data-ttu-id="aa0a2-124">特定の警告を無効にするには、 **None**警告の横にあるドロップダウン リストからです。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aa0a2-125">例</span><span class="sxs-lookup"><span data-stu-id="aa0a2-125">Example</span></span>  
 <span data-ttu-id="aa0a2-126">次のコードのコンパイル`T2.vb`し、すべての警告を表示しません。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="aa0a2-127">例</span><span class="sxs-lookup"><span data-stu-id="aa0a2-127">Example</span></span>  
 <span data-ttu-id="aa0a2-128">次のコードのコンパイル`T2.vb`し、使用されていないローカル変数 (42024) に警告を表示しません。</span><span class="sxs-lookup"><span data-stu-id="aa0a2-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa0a2-129">参照</span><span class="sxs-lookup"><span data-stu-id="aa0a2-129">See Also</span></span>  
 [<span data-ttu-id="aa0a2-130">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="aa0a2-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="aa0a2-131">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="aa0a2-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="aa0a2-132">Visual Basic での警告の構成</span><span class="sxs-lookup"><span data-stu-id="aa0a2-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
