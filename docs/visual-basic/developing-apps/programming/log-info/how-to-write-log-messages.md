---
title: "方法: ログ メッセージを書き込む (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4d875fd4f95ca51fff565551009e780b17d07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="550d7-102">方法: ログ メッセージを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550d7-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="550d7-103">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーションに関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="550d7-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="550d7-104">この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報をログに記録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="550d7-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="550d7-105">例外情報をログに記録するには、`My.Application.Log.WriteException` メソッドを使います。方法については、「[方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="550d7-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="550d7-106">例</span><span class="sxs-lookup"><span data-stu-id="550d7-106">Example</span></span>  
 <span data-ttu-id="550d7-107">この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="550d7-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="550d7-108">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="550d7-108">.NET Framework Security</span></span>  
 <span data-ttu-id="550d7-109">ログに書き込むデータに、ユーザーのパスワードなどの機密情報が含まれないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="550d7-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="550d7-110">詳しくは、「[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="550d7-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="550d7-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="550d7-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="550d7-112">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="550d7-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="550d7-113">方法 : 例外をログに記録する</span><span class="sxs-lookup"><span data-stu-id="550d7-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="550d7-114">チュートリアル : My.Application.Log による情報の書き込み先の確認</span><span class="sxs-lookup"><span data-stu-id="550d7-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="550d7-115">チュートリアル : My.Application.Log による情報の書き込み先の変更</span><span class="sxs-lookup"><span data-stu-id="550d7-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="550d7-116">チュートリアル : My.Application.Log の出力をフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="550d7-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
