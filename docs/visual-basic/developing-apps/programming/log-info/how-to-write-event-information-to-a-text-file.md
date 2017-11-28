---
title: "方法: イベント情報をテキスト ファイルに書き込む (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 944d874de5c3872f9efe5e287e5354c94c792b95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="dca4d-102">方法: イベント情報をテキスト ファイルに書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dca4d-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="dca4d-103">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="dca4d-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="dca4d-104">この例では、`My.Application.Log.WriteEntry` メソッドを使ってトレース情報をログ ファイルに記録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dca4d-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="dca4d-105">ファイル ログ リスナーを追加および構成するには</span><span class="sxs-lookup"><span data-stu-id="dca4d-105">To add and configure the file log listener</span></span>  
  
1.  <span data-ttu-id="dca4d-106">**ソリューション エクスプローラー** で app.config を右クリックし、 **[開く]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="dca4d-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="dca4d-107">\- または</span><span class="sxs-lookup"><span data-stu-id="dca4d-107">\- or -</span></span>  
  
     <span data-ttu-id="dca4d-108">app.config ファイルがない場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="dca4d-108">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="dca4d-109">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dca4d-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="dca4d-110">**[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="dca4d-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="dca4d-111">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dca4d-111">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="dca4d-112">アプリケーション構成ファイルで `<listeners>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="dca4d-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="dca4d-113">\<listeners> セクションは、最上位の \<configuration> セクションに入れ子になった \<system.diagnostics> セクションにさらに入れ子になっている、名前属性が "DefaultSource" の \<source> セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="dca4d-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3.  <span data-ttu-id="dca4d-114">その `<listeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="dca4d-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4.  <span data-ttu-id="dca4d-115">最上位の `<configuration>` セクションに入れ子になっている `<system.diagnostics>` セクションで、`<sharedListeners>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="dca4d-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="dca4d-116">その `<sharedListeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="dca4d-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="dca4d-117">`customlocation` 属性の値をログ ディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="dca4d-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dca4d-118">リスナー プロパティの値を設定するには、プロパティと同じ名前ですべてが英小文字の属性を使います。</span><span class="sxs-lookup"><span data-stu-id="dca4d-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="dca4d-119">たとえば、`location` 属性と `customlocation` 属性では、<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> プロパティと <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> プロパティの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="dca4d-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="dca4d-120">イベント情報をファイル ログに書き込むには</span><span class="sxs-lookup"><span data-stu-id="dca4d-120">To write event information to the file log</span></span>  
  
-   <span data-ttu-id="dca4d-121">ファイル ログに情報を書き込むには、`My.Application.Log.WriteEntry` メソッドまたは `My.Application.Log.WriteException` メソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="dca4d-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="dca4d-122">詳しくは、「[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)」および「[方法: 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dca4d-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="dca4d-123">アセンブリに対してファイル ログ リスナーを設定すると、リスナーはそのアセンブリから `My.Application.Log` によって書き込まれたすべてのメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="dca4d-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca4d-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="dca4d-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="dca4d-125">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="dca4d-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="dca4d-126">方法 : 例外をログに記録する</span><span class="sxs-lookup"><span data-stu-id="dca4d-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
