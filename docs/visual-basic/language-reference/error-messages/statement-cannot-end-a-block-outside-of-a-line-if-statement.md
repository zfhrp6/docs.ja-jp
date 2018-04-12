---
title: 'ステートメントは場合行 &#39; の外部でブロックを終了できません (& a) #39 です。ステートメント'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="41779-102">ステートメントは場合行 &#39; の外部でブロックを終了できません (& a) #39 です。ステートメント</span><span class="sxs-lookup"><span data-stu-id="41779-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="41779-103">単一行`If`ステートメントがコロン (:) のうちの 1 つで区切られた複数のステートメントを含む、`End`単一行の外部のコントロール ブロックのステートメント`If`です。</span><span class="sxs-lookup"><span data-stu-id="41779-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="41779-104">単一行`If`ステートメントは使用しないで、`End If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="41779-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="41779-105">**エラー ID:** BC32005</span><span class="sxs-lookup"><span data-stu-id="41779-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41779-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="41779-106">To correct this error</span></span>  
  
-   <span data-ttu-id="41779-107">単一行を移動`If`ステートメントを含むコントロール ブロックの外側、`End If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="41779-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41779-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="41779-108">See Also</span></span>  
 [<span data-ttu-id="41779-109">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="41779-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
