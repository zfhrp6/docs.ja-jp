---
title: "方法: ログ メッセージを書き込む (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ffc45b93250ba9e909776352b702be2e8295435d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="0b5fd-102">方法: ログ メッセージを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b5fd-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="0b5fd-103">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーションに関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="0b5fd-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="0b5fd-104">この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報をログに記録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0b5fd-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="0b5fd-105">例外情報をログに記録するには、`My.Application.Log.WriteException` メソッドを使います。方法については、「[方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0b5fd-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b5fd-106">例</span><span class="sxs-lookup"><span data-stu-id="0b5fd-106">Example</span></span>  
 <span data-ttu-id="0b5fd-107">この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="0b5fd-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 <span data-ttu-id="0b5fd-108">[!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0b5fd-108">[!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0b5fd-109">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0b5fd-109">.NET Framework Security</span></span>  
 <span data-ttu-id="0b5fd-110">ログに書き込むデータに、ユーザーのパスワードなどの機密情報が含まれないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="0b5fd-110">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="0b5fd-111">詳しくは、「[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0b5fd-111">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5fd-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b5fd-112">See Also</span></span>  
 <span data-ttu-id="0b5fd-113"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0b5fd-113"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="0b5fd-114"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="0b5fd-114"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>   
 <span data-ttu-id="0b5fd-115"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span><span class="sxs-lookup"><span data-stu-id="0b5fd-115"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span></span>   
 <span data-ttu-id="0b5fd-116">[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="0b5fd-116">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="0b5fd-117">[方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="0b5fd-117">[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span></span>  
 <span data-ttu-id="0b5fd-118">[チュートリアル : My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="0b5fd-118">[Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span></span>  
 <span data-ttu-id="0b5fd-119">[チュートリアル : My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="0b5fd-119">[Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span></span>  
 [<span data-ttu-id="0b5fd-120">チュートリアル : My.Application.Log の出力をフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="0b5fd-120">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)

