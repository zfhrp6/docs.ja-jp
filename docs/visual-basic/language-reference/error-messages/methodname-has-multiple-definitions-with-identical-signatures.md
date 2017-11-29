---
title: "&#39;です。&lt;methodname&gt;&#39; 同じシグネチャを持つ複数の定義"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords: BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1a71d51690d6318a559a94ac81de625289d7587d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39ltmethodnamegt39-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="8bc09-102">&#39;です。&lt;methodname&gt;&#39; 同じシグネチャを持つ複数の定義</span><span class="sxs-lookup"><span data-stu-id="8bc09-102">&#39;&lt;methodname&gt;&#39; has multiple definitions with identical signatures</span></span>
<span data-ttu-id="8bc09-103">A`Function`または`Sub`プロシージャ宣言では、前の宣言と同じプロシージャの名前と引数のリストを使用します。</span><span class="sxs-lookup"><span data-stu-id="8bc09-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="8bc09-104">考えられる原因の 1 つは、元のプロシージャをオーバー ロードする試みです。</span><span class="sxs-lookup"><span data-stu-id="8bc09-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="8bc09-105">オーバー ロードされたプロシージャは、異なる引数リストを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="8bc09-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="8bc09-106">**エラー ID:** BC30269</span><span class="sxs-lookup"><span data-stu-id="8bc09-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8bc09-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8bc09-107">To correct this error</span></span>  
  
-   <span data-ttu-id="8bc09-108">プロシージャ名か、引数リストを変更するか、重複する宣言を削除します。</span><span class="sxs-lookup"><span data-stu-id="8bc09-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc09-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bc09-109">See Also</span></span>  
 [<span data-ttu-id="8bc09-110">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="8bc09-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="8bc09-111">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="8bc09-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
