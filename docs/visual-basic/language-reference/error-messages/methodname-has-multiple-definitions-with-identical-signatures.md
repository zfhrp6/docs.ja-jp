---
title: '&#39;&lt;methodname&gt; &#39;同じシグネチャを持つ複数の定義'
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 059d152cf9c3fae77ab53a4a9248b36d99614c8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="39ltmethodnamegt39-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="4f1f1-102">&#39;&lt;methodname&gt; &#39;同じシグネチャを持つ複数の定義</span><span class="sxs-lookup"><span data-stu-id="4f1f1-102">&#39;&lt;methodname&gt;&#39; has multiple definitions with identical signatures</span></span>
<span data-ttu-id="4f1f1-103">A`Function`または`Sub`プロシージャ宣言では、前の宣言と同じプロシージャの名前と引数のリストを使用します。</span><span class="sxs-lookup"><span data-stu-id="4f1f1-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="4f1f1-104">考えられる原因の 1 つは、元のプロシージャをオーバー ロードする試みです。</span><span class="sxs-lookup"><span data-stu-id="4f1f1-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="4f1f1-105">オーバー ロードされたプロシージャは、異なる引数リストを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f1f1-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="4f1f1-106">**エラー ID:** BC30269</span><span class="sxs-lookup"><span data-stu-id="4f1f1-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4f1f1-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4f1f1-107">To correct this error</span></span>  
  
-   <span data-ttu-id="4f1f1-108">プロシージャ名か、引数リストを変更するか、重複する宣言を削除します。</span><span class="sxs-lookup"><span data-stu-id="4f1f1-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1f1-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f1f1-109">See Also</span></span>  
 [<span data-ttu-id="4f1f1-110">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="4f1f1-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="4f1f1-111">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="4f1f1-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
