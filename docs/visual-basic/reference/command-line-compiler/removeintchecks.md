---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 917977d8e5e12c231370ab3c956aca9d96e8a8a8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="removeintchecks"></a><span data-ttu-id="bb95f-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="bb95f-102">/removeintchecks</span></span>
<span data-ttu-id="bb95f-103">オーバーフロー エラーのオンまたはオフ、整数演算のチェックをオンにします。</span><span class="sxs-lookup"><span data-stu-id="bb95f-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb95f-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb95f-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="bb95f-105">引数</span><span class="sxs-lookup"><span data-stu-id="bb95f-105">Arguments</span></span>  
  
|<span data-ttu-id="bb95f-106">用語</span><span class="sxs-lookup"><span data-stu-id="bb95f-106">Term</span></span>|<span data-ttu-id="bb95f-107">定義</span><span class="sxs-lookup"><span data-stu-id="bb95f-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="bb95f-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="bb95f-108">`+` &#124; `-`</span></span>|<span data-ttu-id="bb95f-109">任意。</span><span class="sxs-lookup"><span data-stu-id="bb95f-109">Optional.</span></span> <span data-ttu-id="bb95f-110">`/removeintchecks-`オプションは、すべての整数の計算でオーバーフロー エラーを確認するコンパイラです。</span><span class="sxs-lookup"><span data-stu-id="bb95f-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="bb95f-111">既定値は、`/removeintchecks-` です。</span><span class="sxs-lookup"><span data-stu-id="bb95f-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="bb95f-112">指定する`/removeintchecks`または`/removeintchecks+`エラー チェックが回避し、高速の整数の計算を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bb95f-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="bb95f-113">エラーは次のチェックを行わないただし、し、エラーを発生させず、正しくない結果を格納することがありますデータ型の容量がオーバーフローした場合。</span><span class="sxs-lookup"><span data-stu-id="bb95f-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="bb95f-114">Visual Studio で/removeintchecks を設定するには、統合開発環境</span><span class="sxs-lookup"><span data-stu-id="bb95f-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="bb95f-115">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="bb95f-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bb95f-116">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb95f-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="bb95f-117">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb95f-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="bb95f-118">3.**[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb95f-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="bb95f-119">4.値を変更、**整数オーバーフローのチェックを解除**ボックス。</span><span class="sxs-lookup"><span data-stu-id="bb95f-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bb95f-120">例</span><span class="sxs-lookup"><span data-stu-id="bb95f-120">Example</span></span>  
 <span data-ttu-id="bb95f-121">次のコードのコンパイル`Test.vb`し整数オーバーフロー エラー チェックをオフにします。</span><span class="sxs-lookup"><span data-stu-id="bb95f-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb95f-122">参照</span><span class="sxs-lookup"><span data-stu-id="bb95f-122">See Also</span></span>  
 [<span data-ttu-id="bb95f-123">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="bb95f-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="bb95f-124">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="bb95f-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
