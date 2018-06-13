---
title: ステートメントは、行の外側でブロックを終了できません&#39;場合&#39;ステートメント
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596685"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="4db00-102">ステートメントは、行の外側でブロックを終了できません&#39;場合&#39;ステートメント</span><span class="sxs-lookup"><span data-stu-id="4db00-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="4db00-103">単一行`If`ステートメントがコロン (:) のうちの 1 つで区切られた複数のステートメントを含む、`End`単一行の外部のコントロール ブロックのステートメント`If`です。</span><span class="sxs-lookup"><span data-stu-id="4db00-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="4db00-104">単一行`If`ステートメントは使用しないで、`End If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4db00-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="4db00-105">**エラー ID:** BC32005</span><span class="sxs-lookup"><span data-stu-id="4db00-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4db00-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4db00-106">To correct this error</span></span>  
  
-   <span data-ttu-id="4db00-107">単一行を移動`If`ステートメントを含むコントロール ブロックの外側、`End If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4db00-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db00-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="4db00-108">See Also</span></span>  
 [<span data-ttu-id="4db00-109">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="4db00-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
