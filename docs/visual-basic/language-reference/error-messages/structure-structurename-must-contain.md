---
title: 構造体 &#39;&lt;structurename&gt;&#39; には、少なくとも 1 つのインスタンス メンバー変数、またはマークされていないには、少なくとも 1 つのインスタンスのイベント宣言 &#39; に含める必要がありますカスタム &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b28dd59271bdaca52072710ea797fae6e9168eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="5b78f-102">構造体 &#39;&lt;structurename&gt;&#39; には、少なくとも 1 つのインスタンス メンバー変数、またはマークされていないには、少なくとも 1 つのインスタンスのイベント宣言 &#39; に含める必要がありますカスタム &#39;</span><span class="sxs-lookup"><span data-stu-id="5b78f-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="5b78f-103">構造体の定義は、すべての非共有変数または非共有のカスタム イベントには含まれません。</span><span class="sxs-lookup"><span data-stu-id="5b78f-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="5b78f-104">すべての構造体を変数または総称してすべてのインスタンスに (共有) の代わりに特定のインスタンスに適用されるイベントのいずれかが適用される場合があります ([Shared](../../../visual-basic/language-reference/modifiers/shared.md))。</span><span class="sxs-lookup"><span data-stu-id="5b78f-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="5b78f-105">非共有の定数、プロパティ、およびプロシージャは、この要件を満たしていません。</span><span class="sxs-lookup"><span data-stu-id="5b78f-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="5b78f-106">さらに、非共有変数がなく、1 つだけの非共有イベントがある場合は、そのイベントすることはできません、`Custom`イベント。</span><span class="sxs-lookup"><span data-stu-id="5b78f-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="5b78f-107">**エラー ID:** BC30941</span><span class="sxs-lookup"><span data-stu-id="5b78f-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5b78f-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5b78f-108">To correct this error</span></span>  
  
-   <span data-ttu-id="5b78f-109">少なくとも 1 つの変数またはイベントではない定義`Shared`です。</span><span class="sxs-lookup"><span data-stu-id="5b78f-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="5b78f-110">1 つだけイベントを定義する場合は、非カスタムと非共有があります。</span><span class="sxs-lookup"><span data-stu-id="5b78f-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b78f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b78f-111">See Also</span></span>  
 [<span data-ttu-id="5b78f-112">構造体</span><span class="sxs-lookup"><span data-stu-id="5b78f-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="5b78f-113">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="5b78f-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="5b78f-114">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="5b78f-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
