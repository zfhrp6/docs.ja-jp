---
title: ".NET Framework のログ記録の制御"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90de9dd6bd32eb2142dceb98c142f3c50a0a5691
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="41790-102">.NET Framework のログ記録の制御</span><span class="sxs-lookup"><span data-stu-id="41790-102">Controlling .NET Framework Logging</span></span>
<span data-ttu-id="41790-103">Windows イベント トレーシング (ETW: Event Tracing for Windows) を使用して共通言語ランタイム (CLR: Common Language Runtime) イベントを記録できます。</span><span class="sxs-lookup"><span data-stu-id="41790-103">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="41790-104">トレースの作成および表示には次のツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="41790-104">You can create and view traces by using the following tools:</span></span>  
  
-   <span data-ttu-id="41790-105">Windows オペレーティング システムに含まれる [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) および [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) コマンド ライン ツール。</span><span class="sxs-lookup"><span data-stu-id="41790-105">The [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) and [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) command-line tools, which are included with the Windows operating system.</span></span>  
  
-   <span data-ttu-id="41790-106">[Windows Performance Toolkit](http://msdn.microsoft.com/library/windows/hardware/hh162945.aspx) の [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) ツール。</span><span class="sxs-lookup"><span data-stu-id="41790-106">The [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) tools in the [Windows Performance Toolkit](http://msdn.microsoft.com/library/windows/hardware/hh162945.aspx).</span></span> <span data-ttu-id="41790-107">Xperf の詳細については、[Windows のパフォーマンスに関するブログ](http://go.microsoft.com/fwlink/?LinkId=179509)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41790-107">For more information about Xperf, see the [Windows Performance blog](http://go.microsoft.com/fwlink/?LinkId=179509).</span></span>  
  
 <span data-ttu-id="41790-108">CLR イベントの情報をキャプチャするには、コンピューターに CLR プロバイダーがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="41790-108">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="41790-109">プロバイダーがインストールされているかどうかを確認するには、コマンド プロンプトで「`logman query providers`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="41790-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="41790-110">プロバイダーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="41790-110">A list of providers is displayed.</span></span> <span data-ttu-id="41790-111">その一覧に、次のような CLR プロバイダーのエントリが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="41790-111">This list should contain an entry for the CLR provider, as follows.</span></span>  
  
```  
Provider                                 GUID  
-------------------------------------------------------------------------------  
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.  
```  
  
 <span data-ttu-id="41790-112">一覧に CLR プロバイダーが含まれていない場合は、Windows Vista 以降のオペレーティング システムで Windows [Wevtutil](http://go.microsoft.com/fwlink/?LinkID=150915) コマンド ライン ツールを使用してインストールできます。</span><span class="sxs-lookup"><span data-stu-id="41790-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](http://go.microsoft.com/fwlink/?LinkID=150915) command-line tool.</span></span> <span data-ttu-id="41790-113">管理者としてコマンド プロンプト ウィンドウを開き、</span><span class="sxs-lookup"><span data-stu-id="41790-113">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="41790-114">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] のフォルダー (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\) に移動します。</span><span class="sxs-lookup"><span data-stu-id="41790-114">Change the prompt directory to the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="41790-115">このフォルダーに、CLR-ETW.man ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="41790-115">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="41790-116">コマンド プロンプトで次のコマンドを入力して CLR プロバイダーをインストールします。</span><span class="sxs-lookup"><span data-stu-id="41790-116">At the command prompt, type the following command to install the CLR provider:</span></span>  
  
 `wevtutil im CLR-ETW.man`  
  
## <a name="capturing-clr-etw-events"></a><span data-ttu-id="41790-117">CLR ETW イベントのキャプチャ</span><span class="sxs-lookup"><span data-stu-id="41790-117">Capturing CLR ETW Events</span></span>  
 <span data-ttu-id="41790-118">コマンド ライン ツールの [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) および [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) を使用して ETW イベントをキャプチャできます。また、[Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) および [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) ツールを使用してトレース イベントをデコードできます。</span><span class="sxs-lookup"><span data-stu-id="41790-118">You can use the [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) and [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) command-line tools to capture ETW events, and the [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) and [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) tools to decode the trace events.</span></span>  
  
 <span data-ttu-id="41790-119">ログを有効にするには、次の 3 つの項目を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41790-119">To turn on logging, a user must specify three things:</span></span>  
  
-   <span data-ttu-id="41790-120">通信先のプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="41790-120">The provider to communicate to.</span></span>  
  
-   <span data-ttu-id="41790-121">キーワード セットを表す 64 ビットの数値。</span><span class="sxs-lookup"><span data-stu-id="41790-121">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="41790-122">各キーワードは、プロバイダーが有効にできる一連のイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="41790-122">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="41790-123">この数値は、有効にするキーワードの組み合わせを表します。</span><span class="sxs-lookup"><span data-stu-id="41790-123">The number represents a combined set of keywords to turn on.</span></span>  
  
-   <span data-ttu-id="41790-124">記録レベル (詳細度) を表す小さな数値。</span><span class="sxs-lookup"><span data-stu-id="41790-124">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="41790-125">レベル 1 が最も簡易であり、レベル 5 が最も詳細になります。</span><span class="sxs-lookup"><span data-stu-id="41790-125">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="41790-126">レベル 0 は既定値であり、プロバイダー固有であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="41790-126">Level 0 is a default whose meaning is provider-specific.</span></span>  
  
#### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="41790-127">Logman を使用して CLR ETW イベントをキャプチャするには</span><span class="sxs-lookup"><span data-stu-id="41790-127">To capture CLR ETW events using Logman</span></span>  
  
1.  <span data-ttu-id="41790-128">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="41790-128">At the command prompt, type:</span></span>  
  
     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`  
  
     <span data-ttu-id="41790-129">それぞれの文字について以下に説明します。</span><span class="sxs-lookup"><span data-stu-id="41790-129">where:</span></span>  
  
    -   <span data-ttu-id="41790-130">`-p` パラメーターはプロバイダーの GUID を識別します。</span><span class="sxs-lookup"><span data-stu-id="41790-130">The `-p` parameter identifies the provider GUID.</span></span>  
  
    -   <span data-ttu-id="41790-131">`0x1CCBD` は、発生するイベントのカテゴリを指定しています。</span><span class="sxs-lookup"><span data-stu-id="41790-131">`0x1CCBD` specifies the categories of events that will be raised.</span></span>  
  
    -   <span data-ttu-id="41790-132">`0x5` は、ログ レベルを設定しています (この場合は詳細 (5))。</span><span class="sxs-lookup"><span data-stu-id="41790-132">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>  
  
    -   <span data-ttu-id="41790-133">`-ets` パラメーターは、コマンドをイベント トレース セッションに送信するように指定します。</span><span class="sxs-lookup"><span data-stu-id="41790-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>  
  
    -   <span data-ttu-id="41790-134">`-ct perf` パラメーターは、`QueryPerformanceCounter` 関数を使用して各イベントのタイム スタンプを記録するように指定します。</span><span class="sxs-lookup"><span data-stu-id="41790-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>  
  
2.  <span data-ttu-id="41790-135">イベントの記録を停止するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="41790-135">To stop logging the events, type:</span></span>  
  
     `logman stop clrevents -ets`  
  
     <span data-ttu-id="41790-136">これにより、clrevents.etl という名前のバイナリ トレース ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="41790-136">This command creates a binary trace file named clrevents.etl.</span></span>  
  
#### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="41790-137">Xperf を使用して CLR ETW イベントをキャプチャするには</span><span class="sxs-lookup"><span data-stu-id="41790-137">To capture CLR ETW events using Xperf</span></span>  
  
1.  <span data-ttu-id="41790-138">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="41790-138">At the command prompt, type:</span></span>  
  
     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`  
  
     <span data-ttu-id="41790-139">GUID には CLR ETW プロバイダーの GUID を指定します。`0x1CCBD:5` を指定すると、レベル 5 (詳細) 以下のすべての内容がトレースされます。</span><span class="sxs-lookup"><span data-stu-id="41790-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>  
  
2.  <span data-ttu-id="41790-140">トレースを停止するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="41790-140">To stop tracing, type:</span></span>  
  
     `Xperf -stop clr`  
  
     <span data-ttu-id="41790-141">これにより、clrevents.etl という名前のトレース ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="41790-141">This command creates a trace file named clrevents.etl.</span></span>  
  
## <a name="viewing-clr-etw-events"></a><span data-ttu-id="41790-142">CLR ETW イベントの表示</span><span class="sxs-lookup"><span data-stu-id="41790-142">Viewing CLR ETW Events</span></span>  
 <span data-ttu-id="41790-143">CLR ETW イベントを表示するには、以下のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="41790-143">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="41790-144">イベントの詳細については、「[CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41790-144">For a description of the events, see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md).</span></span>  
  
#### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="41790-145">Tracerpt を使用して CLR ETW イベントを表示するには</span><span class="sxs-lookup"><span data-stu-id="41790-145">To view CLR ETW events using Tracerpt</span></span>  
  
-   <span data-ttu-id="41790-146">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="41790-146">At the command prompt, type:</span></span>  
  
     `tracerpt clrevents.etl`  
  
     <span data-ttu-id="41790-147">これにより、dumpfile.xml と summary.txt という 2 つのファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="41790-147">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="41790-148">dumpfile.xml ファイルはすべてのイベントの一覧で、summary.txt はイベントの概要です。</span><span class="sxs-lookup"><span data-stu-id="41790-148">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>  
  
#### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="41790-149">Xperf を使用して CLR ETW イベントを表示するには</span><span class="sxs-lookup"><span data-stu-id="41790-149">To view CLR ETW events using Xperf</span></span>  
  
-   <span data-ttu-id="41790-150">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="41790-150">At the command prompt, type:</span></span>  
  
     `xperf clrevents.etl`  
  
     <span data-ttu-id="41790-151">Xperf ETL ファイル ビューアーが開きます。</span><span class="sxs-lookup"><span data-stu-id="41790-151">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="41790-152">このビューアーでは、CLR イベントは、**[一般的なイベント]** ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="41790-152">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="41790-153">種類別に分類されたイベントのデータ グリッドを表示するには、このビューで時間帯を選択し、マウスを右クリックして **[概要]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="41790-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>  
  
#### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="41790-154">.etl ファイルをコンマ区切り値ファイルに変換するには</span><span class="sxs-lookup"><span data-stu-id="41790-154">To convert the .etl file to a comma-separated value file</span></span>  
  
-   <span data-ttu-id="41790-155">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="41790-155">At the command prompt, type:</span></span>  
  
     `xperf -i clrevents.etl -f clrevents.csv`  
  
     <span data-ttu-id="41790-156">このコマンドを使用すると、XPerf によって、表示可能なコンマ区切り値 (CSV) ファイルとしてイベントがダンプされます。</span><span class="sxs-lookup"><span data-stu-id="41790-156">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="41790-157">イベントが異なればフィールドも異なるので、この CSV ファイルには、データの前に複数のヘッダー行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="41790-157">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="41790-158">すべての行の先頭のフィールドはイベントの種類を表します。このフィールドは、残りのフィールドを判別するために使用されるヘッダーを示します。</span><span class="sxs-lookup"><span data-stu-id="41790-158">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41790-159">参照</span><span class="sxs-lookup"><span data-stu-id="41790-159">See Also</span></span>  
 [<span data-ttu-id="41790-160">Windows パフォーマンス ツールキット</span><span class="sxs-lookup"><span data-stu-id="41790-160">Windows Performance Toolkit</span></span>](http://go.microsoft.com/fwlink/?LinkID=161141)  
 [<span data-ttu-id="41790-161">共通言語ランタイムの ETW イベント</span><span class="sxs-lookup"><span data-stu-id="41790-161">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
