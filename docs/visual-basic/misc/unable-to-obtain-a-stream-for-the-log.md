---
title: "ログのストリームを取得できません"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dd3051b2331502c9f4f3430bbf88731b307d1b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="1052f-102">ログのストリームを取得できません</span><span class="sxs-lookup"><span data-stu-id="1052f-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="1052f-103">ログのストリームを取得できません。</span><span class="sxs-lookup"><span data-stu-id="1052f-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="1052f-104">潜在的なファイル名に基づいて\<名 > は既に使用中です。</span><span class="sxs-lookup"><span data-stu-id="1052f-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="1052f-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>可能性のあるすべてのログ ファイル名に基づいているために、クラスは、新しいログ ファイルを作成できませんでした\<名 > は既に使用中です。</span><span class="sxs-lookup"><span data-stu-id="1052f-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="1052f-106">ログ ファイルが多すぎる場合、アプリケーションにアーキテクチャの問題がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1052f-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="1052f-107">詳細については、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> クラスのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1052f-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1052f-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1052f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="1052f-109"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> プロパティを <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> または <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> に設定して、ログ ファイル名に日付スタンプを含めます。</span><span class="sxs-lookup"><span data-stu-id="1052f-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="1052f-110">既存のログをアーカイブし、それらをコンピューターから削除して、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> オブジェクトが新しいログを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1052f-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1052f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="1052f-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="1052f-112">My.Application.Log オブジェクト</span><span class="sxs-lookup"><span data-stu-id="1052f-112">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="1052f-113">My.Log オブジェクト</span><span class="sxs-lookup"><span data-stu-id="1052f-113">My.Log Object</span></span>](../../visual-basic/language-reference/objects/my-log-object.md)
