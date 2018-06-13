---
title: エラーが発生していないときに Resume を実行することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 5e45f713a433365b4bbc8286154a3b877b08ec59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597876"
---
# <a name="resume-without-error"></a><span data-ttu-id="edefa-102">エラーが発生していないときに Resume を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="edefa-102">Resume without error</span></span>
<span data-ttu-id="edefa-103">A`Resume`ステートメントは、外部のエラー処理コードを表示またはコードは、エラーがなかった場合でも、エラー ハンドラーにジャンプします。</span><span class="sxs-lookup"><span data-stu-id="edefa-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="edefa-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="edefa-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="edefa-105">移動、`Resume`ステートメント、エラー ハンドラーを削除したりします。</span><span class="sxs-lookup"><span data-stu-id="edefa-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="edefa-106">ラベルにジャンプは、プロシージャ間発生することはできないため、エラー ハンドラーを識別するラベルをプロシージャ内で検索します。</span><span class="sxs-lookup"><span data-stu-id="edefa-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="edefa-107">対象として指定されている重複するラベルを検索する場合、`GoTo`ステートメントではなく、`On Error GoTo`ステートメントでは、目的の宛先と一致する行のラベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="edefa-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edefa-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="edefa-108">See Also</span></span>  
 [<span data-ttu-id="edefa-109">Resume ステートメント</span><span class="sxs-lookup"><span data-stu-id="edefa-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="edefa-110">On Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="edefa-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
