---
title: "/removeintchecks |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
dev_langs:
- VB
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
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
ms.openlocfilehash: 25f67774238c6e9a6b3a2c50b3702e43d5a6374c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="removeintchecks"></a><span data-ttu-id="42171-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="42171-102">/removeintchecks</span></span>
<span data-ttu-id="42171-103">オーバーフロー エラーのオン/オフ、整数演算のチェックをオンにします。</span><span class="sxs-lookup"><span data-stu-id="42171-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42171-104">構文</span><span class="sxs-lookup"><span data-stu-id="42171-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="42171-105">引数</span><span class="sxs-lookup"><span data-stu-id="42171-105">Arguments</span></span>  
  
|<span data-ttu-id="42171-106">用語</span><span class="sxs-lookup"><span data-stu-id="42171-106">Term</span></span>|<span data-ttu-id="42171-107">定義</span><span class="sxs-lookup"><span data-stu-id="42171-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="42171-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="42171-108">`+` &#124; `-`</span></span>|<span data-ttu-id="42171-109">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="42171-109">Optional.</span></span> <span data-ttu-id="42171-110">`/removeintchecks-`オプションによって、コンパイラは、すべての整数の計算でオーバーフロー エラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="42171-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="42171-111">既定値は、`/removeintchecks-` です。</span><span class="sxs-lookup"><span data-stu-id="42171-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="42171-112">指定する`/removeintchecks`または`/removeintchecks+`により、エラー チェックを行うと、高速の整数の計算を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="42171-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="42171-113">エラーは、次のチェックを行わないただし、エラーを発生させずに不適切な結果が保存されるデータ型の容量がオーバーフローした場合とします。</span><span class="sxs-lookup"><span data-stu-id="42171-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="42171-114">統合開発環境 Visual Studio で/removeintchecks を設定するには</span><span class="sxs-lookup"><span data-stu-id="42171-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="42171-115">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="42171-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="42171-116">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="42171-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="42171-117">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42171-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="42171-118">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="42171-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="42171-119">3.[詳細設定 **** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="42171-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="42171-120">4.値を変更、**整数オーバーフローのチェックを解除**ボックス。</span><span class="sxs-lookup"><span data-stu-id="42171-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="42171-121">例</span><span class="sxs-lookup"><span data-stu-id="42171-121">Example</span></span>  
 <span data-ttu-id="42171-122">次のコードのコンパイル`Test.vb`し整数オーバーフロー エラー チェックをオフにします。</span><span class="sxs-lookup"><span data-stu-id="42171-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="42171-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="42171-123">See Also</span></span>  
 <span data-ttu-id="42171-124">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="42171-124">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="42171-125"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="42171-125"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
