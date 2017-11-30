---
title: "エラーが発生していないときに Resume を実行することはできません。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a><span data-ttu-id="f1fda-102">エラーが発生していないときに Resume を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="f1fda-102">Resume without error</span></span>
<span data-ttu-id="f1fda-103">A`Resume`ステートメントは、外部のエラー処理コードを表示またはコードは、エラーがなかった場合でも、エラー ハンドラーにジャンプします。</span><span class="sxs-lookup"><span data-stu-id="f1fda-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f1fda-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f1fda-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="f1fda-105">移動、`Resume`ステートメント、エラー ハンドラーを削除したりします。</span><span class="sxs-lookup"><span data-stu-id="f1fda-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="f1fda-106">ラベルにジャンプは、プロシージャ間発生することはできないため、エラー ハンドラーを識別するラベルをプロシージャ内で検索します。</span><span class="sxs-lookup"><span data-stu-id="f1fda-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="f1fda-107">対象として指定されている重複するラベルを検索する場合、`GoTo`ステートメントではなく、`On Error GoTo`ステートメントでは、目的の宛先と一致する行のラベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="f1fda-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1fda-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1fda-108">See Also</span></span>  
 [<span data-ttu-id="f1fda-109">Resume ステートメント</span><span class="sxs-lookup"><span data-stu-id="f1fda-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="f1fda-110">On Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="f1fda-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
