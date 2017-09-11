---
title: "アプリケーションからの情報のログ記録 (Visual Basic)"
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
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 58f21df20425b0164586143ad5af6f363a90c3ef
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="14f3d-102">アプリケーションからの情報のログ記録 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14f3d-102">Logging Information from the Application (Visual Basic)</span></span>
<span data-ttu-id="14f3d-103">このセクションには、`My.Application.Log` オブジェクトまたは `My.Log` オブジェクトを使ってアプリケーションの情報を記録する方法と、アプリケーションのログ機能を拡張する方法に関するトピックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="14f3d-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="14f3d-104">`Log` オブジェクトはアプリケーションのログ リスナーに情報を書き込むためのメソッドを提供し、`Log` オブジェクトの高度な `TraceSource` プロパティは詳細な構成情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="14f3d-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="14f3d-105">`Log` オブジェクトは、アプリケーションの構成ファイルによって構成されます。</span><span class="sxs-lookup"><span data-stu-id="14f3d-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="14f3d-106">`My.Log` オブジェクトは、ASP.NET アプリケーションでのみ使うことができます。</span><span class="sxs-lookup"><span data-stu-id="14f3d-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="14f3d-107">クライアント アプリケーションの場合は `My.Application.Log` を使います。</span><span class="sxs-lookup"><span data-stu-id="14f3d-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="14f3d-108">詳細については、「<xref:Microsoft.VisualBasic.Logging.Log>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14f3d-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="14f3d-109">タスク</span><span class="sxs-lookup"><span data-stu-id="14f3d-109">Tasks</span></span>  
  
|<span data-ttu-id="14f3d-110">目的</span><span class="sxs-lookup"><span data-stu-id="14f3d-110">To</span></span>|<span data-ttu-id="14f3d-111">参照トピック</span><span class="sxs-lookup"><span data-stu-id="14f3d-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="14f3d-112">イベントの情報をアプリケーションのログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="14f3d-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="14f3d-113">方法: ログ メッセージを書き込む</span><span class="sxs-lookup"><span data-stu-id="14f3d-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="14f3d-114">例外の情報をアプリケーションのログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="14f3d-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="14f3d-115">方法 : 例外をログに記録する</span><span class="sxs-lookup"><span data-stu-id="14f3d-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="14f3d-116">アプリケーションの起動時または終了時に、トレース情報をアプリケーションのログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="14f3d-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="14f3d-117">方法 : アプリケーションの起動時または終了時にメッセージをログに記録する</span><span class="sxs-lookup"><span data-stu-id="14f3d-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="14f3d-118">テキスト ファイルに情報を書き込むように `My.Application.Log` を構成します。</span><span class="sxs-lookup"><span data-stu-id="14f3d-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="14f3d-119">方法 : イベント情報をテキスト ファイルに書き込む</span><span class="sxs-lookup"><span data-stu-id="14f3d-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="14f3d-120">イベント ログに情報を書き込むように `My.Application.Log` を構成します。</span><span class="sxs-lookup"><span data-stu-id="14f3d-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="14f3d-121">方法 : アプリケーション イベント ログに書き込む</span><span class="sxs-lookup"><span data-stu-id="14f3d-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="14f3d-122">`My.Application.Log` が情報を書き込む場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="14f3d-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="14f3d-123">チュートリアル : My.Application.Log による情報の書き込み先の変更</span><span class="sxs-lookup"><span data-stu-id="14f3d-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="14f3d-124">`My.Application.Log` が情報を書き込む場所を取得します。</span><span class="sxs-lookup"><span data-stu-id="14f3d-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="14f3d-125">チュートリアル : My.Application.Log による情報の書き込み先の確認</span><span class="sxs-lookup"><span data-stu-id="14f3d-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="14f3d-126">`My.Application.Log` のカスタム ログ リスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="14f3d-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="14f3d-127">チュートリアル : カスタム ログ リスナーの作成</span><span class="sxs-lookup"><span data-stu-id="14f3d-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="14f3d-128">`My.Application.Log` ログの出力をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="14f3d-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="14f3d-129">チュートリアル : My.Application.Log の出力をフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="14f3d-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="14f3d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="14f3d-130">See Also</span></span>  
 <span data-ttu-id="14f3d-131"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="14f3d-131"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="14f3d-132">[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="14f3d-132">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 [<span data-ttu-id="14f3d-133">トラブルシューティング : ログ リスナー</span><span class="sxs-lookup"><span data-stu-id="14f3d-133">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

