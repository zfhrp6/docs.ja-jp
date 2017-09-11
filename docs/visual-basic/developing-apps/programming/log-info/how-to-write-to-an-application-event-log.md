---
title: "方法: アプリケーション イベント ログに書き込む (Visual Basic)"
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
- Computer.EventLog element
- WriteEntry method
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
caps.latest.revision: 21
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
ms.openlocfilehash: 7cc73b0644003f8231a7792b0b62d143159da075
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="c0dee-102">方法: アプリケーション イベント ログに書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0dee-102">How to: Write to an Application Event Log (Visual Basic)</span></span>
<span data-ttu-id="c0dee-103">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報を書き込めます。</span><span class="sxs-lookup"><span data-stu-id="c0dee-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="c0dee-104">この例では、 `My.Application.Log` がアプリケーション イベント ログにトレース情報を書き込むようにイベント ログ リスナーを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c0dee-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>  
  
 <span data-ttu-id="c0dee-105">セキュリティ ログに書き込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="c0dee-105">You cannot write to the Security log.</span></span> <span data-ttu-id="c0dee-106">システム ログに書き込むためには、LocalSystem または Administrator アカウントのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="c0dee-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>  
  
 <span data-ttu-id="c0dee-107">イベント ログを参照するには、 **サーバー エクスプローラー** または **Windows イベント ビューアー**を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0dee-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="c0dee-108">詳細については、「 [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0dee-108">For more information, see [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0dee-109">Windows 95、Windows 98、および Windows ME (Millennium Edition) では、イベント ログはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c0dee-109">Event logs are not supported on Windows 95, Windows 98, or Windows Millennium Edition.</span></span>  
  
### <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="c0dee-110">イベント ログ リスナーを追加および構成するには</span><span class="sxs-lookup"><span data-stu-id="c0dee-110">To add and configure the event log listener</span></span>  
  
1.  <span data-ttu-id="c0dee-111">**ソリューション エクスプローラー** で app.config を右クリックし、 **[開く]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="c0dee-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="c0dee-112">\- または</span><span class="sxs-lookup"><span data-stu-id="c0dee-112">\- or -</span></span>  
  
     <span data-ttu-id="c0dee-113">app.config ファイルがない場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="c0dee-113">If there is no app.config file,</span></span>  
  
    1.  <span data-ttu-id="c0dee-114">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0dee-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="c0dee-115">**[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="c0dee-115">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="c0dee-116">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0dee-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="c0dee-117">アプリケーション構成ファイルで `<listeners>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="c0dee-117">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="c0dee-118">`<listeners>` セクションは、最上位の `<source>` セクションに入れ子になった `<system.diagnostics>` セクションにさらに入れ子になっている、名前属性が "DefaultSource" の `<configuration>` セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="c0dee-118">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="c0dee-119">その `<listeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="c0dee-119">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  <span data-ttu-id="c0dee-120">最上位の `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、 `<configuration>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="c0dee-120">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="c0dee-121">その `<sharedListeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="c0dee-121">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     <span data-ttu-id="c0dee-122">`APPLICATION_NAME` をアプリケーションの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c0dee-122">Replace `APPLICATION_NAME` with the name of your application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0dee-123">通常、アプリケーションがイベント ログに書き込むのはエラーのみです。</span><span class="sxs-lookup"><span data-stu-id="c0dee-123">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="c0dee-124">ログ出力のフィルター処理の詳細については、「 [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0dee-124">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
### <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="c0dee-125">イベント情報をイベント ログに書き込むには</span><span class="sxs-lookup"><span data-stu-id="c0dee-125">To write event information to the event log</span></span>  
  
-   <span data-ttu-id="c0dee-126">`My.Application.Log.WriteEntry` メソッドまたは `My.Application.Log.WriteException` メソッドを使用して、イベント ログに情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c0dee-126">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="c0dee-127">詳しくは、「[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)」および「[方法: 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c0dee-127">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="c0dee-128">アセンブリに対してイベント ログ リスナーを設定すると、そのアセンブリで `My.Applcation.Log` が書き込んだすべてのメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c0dee-128">After you configure the event log listener for an assembly, it receives all messages that `My.Applcation.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0dee-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0dee-129">See Also</span></span>  
 <span data-ttu-id="c0dee-130"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c0dee-130"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="c0dee-131"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="c0dee-131"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>   
 <span data-ttu-id="c0dee-132"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span><span class="sxs-lookup"><span data-stu-id="c0dee-132"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span></span>   
 <span data-ttu-id="c0dee-133">[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="c0dee-133">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="c0dee-134">[方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="c0dee-134">[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span></span>  
 [<span data-ttu-id="c0dee-135">チュートリアル : My.Application.Log による情報の書き込み先の確認</span><span class="sxs-lookup"><span data-stu-id="c0dee-135">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)

