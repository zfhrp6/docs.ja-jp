---
title: レコード番号が正しくありません
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 400879ba37c6b3215d9570ca6eb8eaa06edea03b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="bad-record-number"></a><span data-ttu-id="63c4e-102">レコード番号が正しくありません</span><span class="sxs-lookup"><span data-stu-id="63c4e-102">Bad record number</span></span>
<span data-ttu-id="63c4e-103">`a FileGet`、 `FilePut`、 `FileGetObject`、または `FilePutObject` ステートメント内のレコード番号が 0 以下です。</span><span class="sxs-lookup"><span data-stu-id="63c4e-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="63c4e-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="63c4e-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="63c4e-105">レコード番号の生成で使用される計算を確認します。</span><span class="sxs-lookup"><span data-stu-id="63c4e-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="63c4e-106">レコード番号が含まれている変数、またはレコード番号の計算で使用される変数のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="63c4e-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="63c4e-107">モジュールで `Option Explicit On` を使用しない限り、スペル ミスの変数名は暗黙的に宣言され、0 に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="63c4e-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c4e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="63c4e-108">See Also</span></span>  
 [<span data-ttu-id="63c4e-109">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="63c4e-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
