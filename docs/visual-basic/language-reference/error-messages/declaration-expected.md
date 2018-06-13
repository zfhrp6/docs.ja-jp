---
title: 宣言が必要です。
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: c5c9b665b78c7c63c55292e38cc96ee8b2962a61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583891"
---
# <a name="declaration-expected"></a><span data-ttu-id="3c707-102">宣言が必要です。</span><span class="sxs-lookup"><span data-stu-id="3c707-102">Declaration expected</span></span>
<span data-ttu-id="3c707-103">Loop ステートメント、または割り当てなどの代入ステートメントは、プロシージャの外に発生します。</span><span class="sxs-lookup"><span data-stu-id="3c707-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="3c707-104">外部のプロシージャ宣言のみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="3c707-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="3c707-105">または、プログラミング要素が宣言されている宣言キーワードを使用せずなど`Dim`または`Const`です。</span><span class="sxs-lookup"><span data-stu-id="3c707-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="3c707-106">**エラー ID:** BC30188</span><span class="sxs-lookup"><span data-stu-id="3c707-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3c707-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3c707-107">To correct this error</span></span>  
  
-   <span data-ttu-id="3c707-108">代入ステートメントをプロシージャの本体に移動します。</span><span class="sxs-lookup"><span data-stu-id="3c707-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
-   <span data-ttu-id="3c707-109">適切な宣言キーワードで宣言を開始します。</span><span class="sxs-lookup"><span data-stu-id="3c707-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
-   <span data-ttu-id="3c707-110">宣言キーワードのスペルが間違っていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3c707-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c707-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c707-111">See Also</span></span>  
 [<span data-ttu-id="3c707-112">手順</span><span class="sxs-lookup"><span data-stu-id="3c707-112">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="3c707-113">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="3c707-113">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
