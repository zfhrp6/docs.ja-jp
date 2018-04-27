---
title: '方法 : 現在、印刷ジョブが印刷可能であるかどうかを検出する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eef74cfa290614e530fa22a34533c7924d4af1b4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a><span data-ttu-id="bf640-102">方法 : 現在、印刷ジョブが印刷可能であるかどうかを検出する</span><span class="sxs-lookup"><span data-stu-id="bf640-102">How to: Discover Whether a Print Job Can Be Printed At This Time of Day</span></span>
<span data-ttu-id="bf640-103">印刷キューは常に使用できません、1 日 24 時間です。</span><span class="sxs-lookup"><span data-stu-id="bf640-103">Print queues are not always available for 24 hours a day.</span></span> <span data-ttu-id="bf640-104">1 日の特定の時刻に使用できないように設定できます開始と終了の時刻のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="bf640-104">They have start and end time properties that can be set to make them unavailable at certain times of day.</span></span> <span data-ttu-id="bf640-105">たとえば、この機能は、特定の部門午後 5 時以降後に排他的に使用するプリンターを予約するは使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf640-105">This feature can be used, for example, to reserve a printer for the exclusive use of a certain department after 5 P.M..</span></span> <span data-ttu-id="bf640-106">その部門は、別のキュー サービスの他の部門よりプリンターを使用して必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf640-106">That department would have a different queue servicing the printer than other departments use.</span></span> <span data-ttu-id="bf640-107">午後 5 時以降に他の部署のキューを設定すると、する部門用のキューを設定することが常に使用します。</span><span class="sxs-lookup"><span data-stu-id="bf640-107">The queue for the other departments would be set to be unavailable after 5 P.M., while queue for the favored department could be set to be available at all times.</span></span>  
  
 <span data-ttu-id="bf640-108">さらに、印刷ジョブ自体は、指定した期間内でのみ印刷できるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="bf640-108">Moreover, print jobs themselves can be set to be printable only within a specified span of time.</span></span>  
  
 <span data-ttu-id="bf640-109"><xref:System.Printing.PrintQueue>と<xref:System.Printing.PrintSystemJobInfo>で公開されているクラス、 [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework の特定の印刷ジョブが、現時点で特定のキューに印刷できるかどうかをリモートで確認の手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="bf640-109">The <xref:System.Printing.PrintQueue> and <xref:System.Printing.PrintSystemJobInfo> classes exposed in the [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] of Microsoft .NET Framework provide a means for remotely checking whether a given print job can print on a given queue at the current time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf640-110">例</span><span class="sxs-lookup"><span data-stu-id="bf640-110">Example</span></span>  
 <span data-ttu-id="bf640-111">次の例は、印刷ジョブに問題を診断できるサンプルです。</span><span class="sxs-lookup"><span data-stu-id="bf640-111">The example below is a sample that can diagnose problems with a print job.</span></span>  
  
 <span data-ttu-id="bf640-112">この種の関数の 2 つの主な手順は次があります。</span><span class="sxs-lookup"><span data-stu-id="bf640-112">There are two major steps for this kind of function as follows.</span></span>  
  
1.  <span data-ttu-id="bf640-113">読み取り、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>のプロパティ、<xref:System.Printing.PrintQueue>をそれらの間は、現在の時刻かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="bf640-113">Read the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties of the <xref:System.Printing.PrintQueue> to determine whether the current time is between them.</span></span>  
  
2.  <span data-ttu-id="bf640-114">読み取り、<xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>と<xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A>のプロパティ、<xref:System.Printing.PrintSystemJobInfo>をそれらの間は、現在の時刻かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="bf640-114">Read the <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> and <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> properties of the <xref:System.Printing.PrintSystemJobInfo> to determine whether the current time is between them.</span></span>  
  
 <span data-ttu-id="bf640-115">これらのプロパティは、ファクトから複雑な問題が発生するが、<xref:System.DateTime>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bf640-115">But complications arise from the fact that these properties are not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="bf640-116">それらは<xref:System.Int32>午前 0 時から時間を分単位として日の時刻を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bf640-116">Instead they are <xref:System.Int32> objects that express the time of day as the number of minutes since midnight.</span></span> <span data-ttu-id="bf640-117">さらに、this、午前 0 時では、現在のタイム ゾーンは UTC (協定世界時) の午前 0 時です。</span><span class="sxs-lookup"><span data-stu-id="bf640-117">Moreover, this is not midnight in the current time zone, but midnight UTC (Coordinated Universal Time).</span></span>  
  
 <span data-ttu-id="bf640-118">最初のコード例は、静的メソッドを表示**ReportQueueAndJobAvailability**、渡された、<xref:System.Printing.PrintSystemJobInfo>ジョブが現在の時刻に印刷するかどうかを判断するヘルパー メソッドを呼び出すと、印刷できない場合、ときにそのことができます。</span><span class="sxs-lookup"><span data-stu-id="bf640-118">The first code example presents the static method **ReportQueueAndJobAvailability**, which is passed a <xref:System.Printing.PrintSystemJobInfo> and calls helper methods to determine whether the job can print at the current time and, if not, when it can print.</span></span> <span data-ttu-id="bf640-119">注意して、<xref:System.Printing.PrintQueue>メソッドに渡されません。</span><span class="sxs-lookup"><span data-stu-id="bf640-119">Notice that a <xref:System.Printing.PrintQueue> is not passed to the method.</span></span> <span data-ttu-id="bf640-120">これは、ため、<xref:System.Printing.PrintSystemJobInfo>のキューへの参照が含まれています、<xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="bf640-120">This is because the <xref:System.Printing.PrintSystemJobInfo> includes a reference to the queue in its <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> property.</span></span>  
  
 <span data-ttu-id="bf640-121">下位の方法には、オーバー ロードされた**1 つ**いずれかのメソッド、<xref:System.Printing.PrintQueue>または<xref:System.Printing.PrintSystemJobInfo>をパラメーターとして。</span><span class="sxs-lookup"><span data-stu-id="bf640-121">The subordinate methods include the overloaded **ReportAvailabilityAtThisTime** method which can take either a <xref:System.Printing.PrintQueue> or a <xref:System.Printing.PrintSystemJobInfo> as a parameter.</span></span> <span data-ttu-id="bf640-122">**また**です。</span><span class="sxs-lookup"><span data-stu-id="bf640-122">There is also a **TimeConverter.ConvertToLocalHumanReadableTime**.</span></span> <span data-ttu-id="bf640-123">以下は、すべてこれらのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bf640-123">All of these methods are discussed below.</span></span>  
  
 <span data-ttu-id="bf640-124">**ReportQueueAndJobAvailability**メソッドを確認するかどうか、キューまたは印刷ジョブが使用可能なこの時点ではまずします。</span><span class="sxs-lookup"><span data-stu-id="bf640-124">The **ReportQueueAndJobAvailability** method begins by checking to see if either the queue or the print job is unavailable at this time.</span></span> <span data-ttu-id="bf640-125">かどうかを確認するのいずれかが使用可能な場合は、使用できないキュー。</span><span class="sxs-lookup"><span data-stu-id="bf640-125">If either of them is unavailable, it then checks to see if the queue unavailable.</span></span> <span data-ttu-id="bf640-126">使用できませんこのファクトとすると、キュー利用可能になるもう一度時刻、メソッドが報告されます。</span><span class="sxs-lookup"><span data-stu-id="bf640-126">If it is not available, then the method reports this fact and the time when the queue will become available again.</span></span> <span data-ttu-id="bf640-127">ジョブを確認し、[次へ] の時刻を報告使用可能な場合は、ときにまたがるに印刷できるときにします。</span><span class="sxs-lookup"><span data-stu-id="bf640-127">It then checks the job and if it is unavailable, it reports the next time span when it when it can print.</span></span> <span data-ttu-id="bf640-128">最後に、ジョブを印刷できる最も早い時刻を報告します。</span><span class="sxs-lookup"><span data-stu-id="bf640-128">Finally, the method reports the earliest time when the job can print.</span></span> <span data-ttu-id="bf640-129">これは、次の 2 倍の後です。</span><span class="sxs-lookup"><span data-stu-id="bf640-129">This is the later of following two times.</span></span>  
  
-   <span data-ttu-id="bf640-130">印刷キューが次に利用可能な時間。</span><span class="sxs-lookup"><span data-stu-id="bf640-130">The time when the print queue is next available.</span></span>  
  
-   <span data-ttu-id="bf640-131">印刷ジョブが次に利用可能な時間。</span><span class="sxs-lookup"><span data-stu-id="bf640-131">The time when the print job is next available.</span></span>  
  
 <span data-ttu-id="bf640-132">1 日の時間を報告するときに、<xref:System.DateTime.ToShortTimeString%2A>のため、このメソッドは、年、月、および出力からの日数を表示しません。 メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bf640-132">When reporting times of day, the <xref:System.DateTime.ToShortTimeString%2A> method is also called because this method suppresses the years, months, and days from the output.</span></span> <span data-ttu-id="bf640-133">特定の年、月、または日数を印刷キューまたは印刷ジョブのいずれかの可用性を制限することはできません。</span><span class="sxs-lookup"><span data-stu-id="bf640-133">You cannot restrict the availability of either a print queue or a print job to particular years, months, or days.</span></span>  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 <span data-ttu-id="bf640-134">2 つのオーバー ロード、 **1 つ**メソッドはのみそれらに渡される型を除いて同一、<xref:System.Printing.PrintQueue>バージョンを記載します。</span><span class="sxs-lookup"><span data-stu-id="bf640-134">The two overloads of the **ReportAvailabilityAtThisTime** method are identical except for the type passed to them, so only the <xref:System.Printing.PrintQueue> version is presented below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf640-135">サンプルはジェネリック メソッドを作成していないため、メソッドが型を除いて同一であることの質問を発生させます**1 つ\<T >** です。</span><span class="sxs-lookup"><span data-stu-id="bf640-135">The fact that the methods are identical except for type raises the question of why the sample does not create a generic method **ReportAvailabilityAtThisTime\<T>**.</span></span> <span data-ttu-id="bf640-136">その理由は、このようなメソッドを持つクラスに制限する必要がある、**一度、対象**と**UntilTimeOfDay**メソッドを呼び出すと、プロパティが、ジェネリック メソッドのみに制限できます、1 つのクラスであり、唯一のクラスの両方に共通<xref:System.Printing.PrintQueue>と<xref:System.Printing.PrintSystemJobInfo>ツリーは、継承の<xref:System.Printing.PrintSystemObject>をこのようなプロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="bf640-136">The reason is that such a method would have to be restricted to a class that has the **StartTimeOfDay** and **UntilTimeOfDay** properties that the method calls, but a generic method can only be restricted to a single class and the only class common to both <xref:System.Printing.PrintQueue> and <xref:System.Printing.PrintSystemJobInfo> in the inheritance tree is <xref:System.Printing.PrintSystemObject> which has no such properties.</span></span>  
  
 <span data-ttu-id="bf640-137">**1 つ**メソッド (次のコード例で表されている) の初期化ではまず、 <xref:System.Boolean> sentinel 変数`true`です。</span><span class="sxs-lookup"><span data-stu-id="bf640-137">The **ReportAvailabilityAtThisTime** method (presented in the code example below) begins by initializing a <xref:System.Boolean> sentinel variable to `true`.</span></span> <span data-ttu-id="bf640-138">リセットされます`false`キューが使用できない場合は、します。</span><span class="sxs-lookup"><span data-stu-id="bf640-138">It will be reset to `false`, if the queue is not available.</span></span>  
  
 <span data-ttu-id="bf640-139">メソッドを次に、かどうかをチェック開始「までの間」時間は同じです。</span><span class="sxs-lookup"><span data-stu-id="bf640-139">Next, the method checks to see if the start and "until" times are identical.</span></span> <span data-ttu-id="bf640-140">場合は、キューは常に、使用可能なため、メソッドを返します`true`です。</span><span class="sxs-lookup"><span data-stu-id="bf640-140">If they are, the queue is always available, so the method returns `true`.</span></span>  
  
 <span data-ttu-id="bf640-141">メソッドが、静的なを使用して、キューが使用できない場合、すべての時間、<xref:System.DateTime.UtcNow%2A>として現在の時刻を取得するプロパティ、<xref:System.DateTime>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bf640-141">If the queue is not available all the time, the method uses the static <xref:System.DateTime.UtcNow%2A> property to get the current time as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="bf640-142">(ために、ローカル タイムここは必要ありません、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プロパティでは、それ自体を UTC 時刻でします)。</span><span class="sxs-lookup"><span data-stu-id="bf640-142">(We do not need local time because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are themselves in UTC time.)</span></span>  
  
 <span data-ttu-id="bf640-143">ただし、これら 2 つのプロパティが<xref:System.DateTime>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bf640-143">However, these two properties are not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="bf640-144"><xref:System.Int32>分後に UTC 深夜の数と時間を表すです。</span><span class="sxs-lookup"><span data-stu-id="bf640-144">They are <xref:System.Int32>s expressing the time as the number of minutes-after-UTC-midnight.</span></span> <span data-ttu-id="bf640-145">変換するためは、<xref:System.DateTime>分の後、午前 0 時にオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bf640-145">So we do have to convert our <xref:System.DateTime> object to minutes-after-midnight.</span></span> <span data-ttu-id="bf640-146">インストールが完了したら、メソッドだけが確認する"now"かどうかを参照してください、キューの開始の間、および「まで」回、セットを false の場合は"now"sentinel が 2 つの時刻の間ではありませんし、sentinel を返します。</span><span class="sxs-lookup"><span data-stu-id="bf640-146">When that is done, the method simply checks to see whether "now" is between the queue's start and "until" times, sets the sentinel to false if "now" is not between the two times, and returns the sentinel.</span></span>  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 <span data-ttu-id="bf640-147">**また**(次のコード例で表されている) メソッドは、ディスカッションは簡単なので、Microsoft .NET Framework で導入されたすべてのメソッドを使用しません。</span><span class="sxs-lookup"><span data-stu-id="bf640-147">The **TimeConverter.ConvertToLocalHumanReadableTime** method (presented in the code example below) does not use any methods introduced with Microsoft .NET Framework, so the discussion is brief.</span></span> <span data-ttu-id="bf640-148">メソッドには二重の変換: 分の後、午前 0 時を表す整数値を取得および人間が判読できる時間に変換する必要があります、これをローカル時刻に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf640-148">The method has a double conversion task: it must take an integer expressing minutes-after-midnight and convert it to a human-readable time and it must convert this to the local time.</span></span> <span data-ttu-id="bf640-149">でこれを行う、最初に作成、 <xref:System.DateTime> UTC しを使用して午前 0 時に設定されているオブジェクト、<xref:System.DateTime.AddMinutes%2A>メソッドをメソッドに渡された分を加算します。</span><span class="sxs-lookup"><span data-stu-id="bf640-149">It accomplishes this by first creating a <xref:System.DateTime> object that is set to midnight UTC and then it uses the <xref:System.DateTime.AddMinutes%2A> method to add the minutes that were passed to the method.</span></span> <span data-ttu-id="bf640-150">返されます。 新しい<xref:System.DateTime>メソッドに渡された元の時刻を表すです。</span><span class="sxs-lookup"><span data-stu-id="bf640-150">This returns a new <xref:System.DateTime> expressing the original time that was passed to the method.</span></span> <span data-ttu-id="bf640-151"><xref:System.DateTime.ToLocalTime%2A>メソッドし、この現地時刻に変換します。</span><span class="sxs-lookup"><span data-stu-id="bf640-151">The <xref:System.DateTime.ToLocalTime%2A> method then converts this to local time.</span></span>  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a><span data-ttu-id="bf640-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf640-152">See Also</span></span>  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.Printing.PrintQueue>  
 [<span data-ttu-id="bf640-153">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="bf640-153">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="bf640-154">印刷の概要</span><span class="sxs-lookup"><span data-stu-id="bf640-154">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
