---
title: "/nowarn |Microsoft ドキュメント"
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
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
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
ms.openlocfilehash: 308bf24c2a397a75f36b97062dde7380b90c8994
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="nowarn"></a><span data-ttu-id="0f446-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="0f446-102">/nowarn</span></span>
<span data-ttu-id="0f446-103">警告を生成するコンパイラの機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="0f446-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f446-104">構文</span><span class="sxs-lookup"><span data-stu-id="0f446-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f446-105">引数</span><span class="sxs-lookup"><span data-stu-id="0f446-105">Arguments</span></span>  
  
|<span data-ttu-id="0f446-106">用語</span><span class="sxs-lookup"><span data-stu-id="0f446-106">Term</span></span>|<span data-ttu-id="0f446-107">定義</span><span class="sxs-lookup"><span data-stu-id="0f446-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="0f446-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="0f446-108">Optional.</span></span> <span data-ttu-id="0f446-109">しないか、コンパイラの警告の ID 番号のコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="0f446-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="0f446-110">警告の Id が指定されていない場合、すべての警告は抑制されます。</span><span class="sxs-lookup"><span data-stu-id="0f446-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f446-111">コメント</span><span class="sxs-lookup"><span data-stu-id="0f446-111">Remarks</span></span>  
 <span data-ttu-id="0f446-112">`/nowarn`オプションは、コンパイラの警告が発生しないようにします。</span><span class="sxs-lookup"><span data-stu-id="0f446-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="0f446-113">個々 の警告を抑制するのに警告の ID を提供、`/nowarn`コロンの後ろのオプションです。</span><span class="sxs-lookup"><span data-stu-id="0f446-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="0f446-114">複数の警告番号コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="0f446-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="0f446-115">警告 id の数値の一部だけを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f446-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="0f446-116">ある BC42024、未使用のローカル変数に対して警告を抑制する場合の指定など`/nowarn:42024`します。</span><span class="sxs-lookup"><span data-stu-id="0f446-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="0f446-117">警告 ID 番号の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="0f446-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="0f446-118">統合開発環境 Visual Studio で/nowarn を設定するには</span><span class="sxs-lookup"><span data-stu-id="0f446-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0f446-119">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="0f446-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0f446-120">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="0f446-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="0f446-121">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f446-121">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="0f446-122">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f446-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0f446-123">3.選択、**すべての警告を無効にする**をすべての警告を無効にする チェック ボックスです。</span><span class="sxs-lookup"><span data-stu-id="0f446-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="0f446-124">または</span><span class="sxs-lookup"><span data-stu-id="0f446-124">- or -</span></span><br />     <span data-ttu-id="0f446-125">特定の警告を無効にするには、**なし**警告の横にあるドロップダウン リストからです。</span><span class="sxs-lookup"><span data-stu-id="0f446-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0f446-126">例</span><span class="sxs-lookup"><span data-stu-id="0f446-126">Example</span></span>  
 <span data-ttu-id="0f446-127">次のコードのコンパイル`T2.vb`すべての警告は表示されません。</span><span class="sxs-lookup"><span data-stu-id="0f446-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="0f446-128">例</span><span class="sxs-lookup"><span data-stu-id="0f446-128">Example</span></span>  
 <span data-ttu-id="0f446-129">次のコードのコンパイル`T2.vb`と、使用されていないローカル変数 (42024) に警告が表示されません。</span><span class="sxs-lookup"><span data-stu-id="0f446-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f446-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f446-130">See Also</span></span>  
 <span data-ttu-id="0f446-131">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0f446-131">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0f446-132"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="0f446-132"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="0f446-133"> [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="0f446-133"> [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span></span>
