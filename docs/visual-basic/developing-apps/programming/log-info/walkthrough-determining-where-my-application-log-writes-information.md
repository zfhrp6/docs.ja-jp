---
title: "My.Application.Log による情報の書き込み先の確認 (Visual Basic)"
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
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
caps.latest.revision: 24
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
ms.openlocfilehash: 36c91f607a5a9d0dcf65ee6e049b9a49cdd37929
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="97504-102">チュートリアル: My.Application.Log による情報の書き込み先の確認 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97504-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="97504-103">`My.Application.Log` オブジェクトは、複数のログ リスナーに情報を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="97504-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="97504-104">ログ リスナーは、コンピューターの構成ファイルで設定し、アプリケーションの構成ファイルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="97504-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="97504-105">このトピックでは、既定の設定について、およびアプリケーションの設定を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="97504-105">This topic describes the default settings and how to determine the settings for your application.</span></span>  
  
 <span data-ttu-id="97504-106">既定の出力場所について詳しくは、「[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97504-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="97504-107">My.Application.Log のリスナーを確認するには</span><span class="sxs-lookup"><span data-stu-id="97504-107">To determine the listeners for My.Application.Log</span></span>  
  
1.  <span data-ttu-id="97504-108">アセンブリの構成ファイルを見つけます。</span><span class="sxs-lookup"><span data-stu-id="97504-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="97504-109">アセンブリを開発中の段階では、 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ソリューション エクスプローラー **から**の app.config にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="97504-109">If you are developing the assembly, you can access the app.config in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] from the **Solution Explorer**.</span></span> <span data-ttu-id="97504-110">開発が終了すると、構成ファイルはアセンブリの名前に ".config" を付け加えたファイル名で、アセンブリと同じディレクトリに配置されています。</span><span class="sxs-lookup"><span data-stu-id="97504-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="97504-111">アセンブリによっては、構成ファイルがない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="97504-111">Not every assembly has a configuration file.</span></span>  
  
     <span data-ttu-id="97504-112">構成ファイルは XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="97504-112">The configuration file is an XML file.</span></span>  
  
2.  <span data-ttu-id="97504-113">`<listeners>` セクション内にある、 `<source>` 属性が "DefaultSource" の `name` セクションで、 `<sources>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="97504-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="97504-114">`<sources>` セクションは、最上位の `<system.diagnostics>` セクション内の `<configuration>` セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="97504-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
     <span data-ttu-id="97504-115">これらのセクションがない場合には、 `My.Application.Log` のログ リスナーは、コンピューターの構成ファイルで設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97504-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="97504-116">以下の手順は、コンピューターの構成ファイルの定義を確認する方法の説明です。</span><span class="sxs-lookup"><span data-stu-id="97504-116">The following steps describe how to determine what the computer configuration file defines:</span></span>  
  
    1.  <span data-ttu-id="97504-117">コンピューターの machine.config ファイルを見つけます。</span><span class="sxs-lookup"><span data-stu-id="97504-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="97504-118">通常は、 *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* ディレクトリにあります。 `SystemRoot` はオペレーティング システム ディレクトリ、 `frameworkVersion` は [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="97504-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
         <span data-ttu-id="97504-119">machine.config の設定は、アプリケーションの構成ファイルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="97504-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>  
  
         <span data-ttu-id="97504-120">以下に示すオプションの要素が存在しない場合には、自分で作成できます。</span><span class="sxs-lookup"><span data-stu-id="97504-120">If the optional elements listed below do not exist, you can create them.</span></span>  
  
    2.  <span data-ttu-id="97504-121">最上位の `<listeners>` セクション内にある `<source>` セクション内の `name` セクションで、 `<sources>` 属性が "DefaultSource" の `<system.diagnostics>` セクション内の `<configuration>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="97504-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
         <span data-ttu-id="97504-122">これらのセクションがない場合、 `My.Application.Log` にあるのは既定のログ リスナーのみです。</span><span class="sxs-lookup"><span data-stu-id="97504-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>  
  
3.  <span data-ttu-id="97504-123"><`listeners>` セクションで <`add>` 要素を見つけます。</span><span class="sxs-lookup"><span data-stu-id="97504-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>  
  
     <span data-ttu-id="97504-124">これらの要素は、名前付きのログ リスナーを `My.Application.Log` のソースに追加します。</span><span class="sxs-lookup"><span data-stu-id="97504-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>  
  
4.  <span data-ttu-id="97504-125">最上位の `<add>` セクション内にある `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、ログ リスナーの名前の `<configuration>` 要素を見つけます。</span><span class="sxs-lookup"><span data-stu-id="97504-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="97504-126">多くの型の共有リスナーでは、リスナーがデータを書き込む先は、リスナーの初期化データで指定されています。</span><span class="sxs-lookup"><span data-stu-id="97504-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>  
  
    -   <span data-ttu-id="97504-127"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=fullName> リスナーは、導入部で説明したように、ファイル ログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="97504-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=fullName> listener writes to a file log, as described in the introduction.</span></span>  
  
    -   <span data-ttu-id="97504-128"><xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName> リスナーは、 `initializeData` パラメーターで指定された、コンピューターのイベント ログに情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="97504-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="97504-129">イベント ログを参照するには、 **サーバー エクスプローラー** または **Windows イベント ビューアー**を使用できます。</span><span class="sxs-lookup"><span data-stu-id="97504-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="97504-130">詳細については、「 [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97504-130">For more information, see [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).</span></span>  
  
    -   <span data-ttu-id="97504-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName> リスナーおよび <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName> リスナーは、 `initializeData` パラメーターで指定されたファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="97504-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName> listeners write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="97504-132"><xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName> リスナーは、コマンド ライン コンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="97504-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName> listener writes to the command-line console.</span></span>  
  
    -   <span data-ttu-id="97504-133">他の型のログ リスナーが情報を書き込む先については、その型のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="97504-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97504-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="97504-134">See Also</span></span>  
 <span data-ttu-id="97504-135"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="97504-135"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="97504-136"><xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="97504-136"><xref:System.Diagnostics.DefaultTraceListener></span></span>   
 <span data-ttu-id="97504-137"><xref:System.Diagnostics.EventLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="97504-137"><xref:System.Diagnostics.EventLogTraceListener></span></span>   
 <span data-ttu-id="97504-138"><xref:System.Diagnostics.DelimitedListTraceListener></span><span class="sxs-lookup"><span data-stu-id="97504-138"><xref:System.Diagnostics.DelimitedListTraceListener></span></span>   
 <span data-ttu-id="97504-139"><xref:System.Diagnostics.XmlWriterTraceListener></span><span class="sxs-lookup"><span data-stu-id="97504-139"><xref:System.Diagnostics.XmlWriterTraceListener></span></span>   
 <span data-ttu-id="97504-140"><xref:System.Diagnostics.ConsoleTraceListener></span><span class="sxs-lookup"><span data-stu-id="97504-140"><xref:System.Diagnostics.ConsoleTraceListener></span></span>   
 <span data-ttu-id="97504-141"><xref:System.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="97504-141"><xref:System.Diagnostics></span></span>   
 <span data-ttu-id="97504-142">[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="97504-142">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="97504-143">[方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="97504-143">[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span></span>  
 <span data-ttu-id="97504-144">[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span><span class="sxs-lookup"><span data-stu-id="97504-144">[How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span></span>  
 <span data-ttu-id="97504-145">[チュートリアル : My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="97504-145">[Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span></span>  
 <span data-ttu-id="97504-146">[.NET Framework の ETW イベント](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299) </span><span class="sxs-lookup"><span data-stu-id="97504-146">[ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299) </span></span>  
 [<span data-ttu-id="97504-147">トラブルシューティング : ログ リスナー</span><span class="sxs-lookup"><span data-stu-id="97504-147">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

