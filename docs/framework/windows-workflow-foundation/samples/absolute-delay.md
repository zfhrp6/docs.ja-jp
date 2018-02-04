---
title: "絶対遅延"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60e3b65851dba68b4d01d6e4195b5faf99b583de
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="absolute-delay"></a><span data-ttu-id="606cf-102">絶対遅延</span><span class="sxs-lookup"><span data-stu-id="606cf-102">Absolute Delay</span></span>
<span data-ttu-id="606cf-103">このサンプルの主要なシナリオは、ワークフロー アプリケーションで永続的なタイマーを使用して、指定した <xref:System.DateTime> まで遅延することです。</span><span class="sxs-lookup"><span data-stu-id="606cf-103">The main scenario for this sample is to delay until a specified <xref:System.DateTime> using durable timers in a workflow application.</span></span> <span data-ttu-id="606cf-104">これは、特定の <xref:System.Activities.Statements.Delay> (または分数/秒数) の遅延のみ行うことができるため、組み込みの <xref:System.TimeSpan> アクティビティの使用とは異なります。</span><span class="sxs-lookup"><span data-stu-id="606cf-104">This is different from using the built-in <xref:System.Activities.Statements.Delay> activity as this will only allow you to delay for a given <xref:System.TimeSpan> (or number of minutes/seconds).</span></span>  
  
 <span data-ttu-id="606cf-105">この区別を行う現実のシナリオとして、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="606cf-105">Some real-life scenarios in which you may want to make this distinction include the following:</span></span>  
  
1.  <span data-ttu-id="606cf-106">メールの送信を 30 秒遅延させて、誤りがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="606cf-106">You want to delay sending a mail for 30 seconds to make sure you didn’t make any errors.</span></span>  
  
2.  <span data-ttu-id="606cf-107">時間外に作業し、通常の営業時間 (午前 8 時など) まですべてのメールを遅延させます。</span><span class="sxs-lookup"><span data-stu-id="606cf-107">You are working overtime and want to delay all of your mails until normal business hours (such as 8 am).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="606cf-108">使用例</span><span class="sxs-lookup"><span data-stu-id="606cf-108">Demonstrates</span></span>  
  
1.  <span data-ttu-id="606cf-109">絶対遅延を実装するための <xref:System.Activities.Statements.DurableTimerExtension></span><span class="sxs-lookup"><span data-stu-id="606cf-109"><xref:System.Activities.Statements.DurableTimerExtension> for implementing Absolute Delay</span></span>  
  
2.  <span data-ttu-id="606cf-110">永続的なタイマーに <xref:System.Activities.WorkflowApplication> を使用した永続性の設定</span><span class="sxs-lookup"><span data-stu-id="606cf-110">Setting up persistence using <xref:System.Activities.WorkflowApplication> for Durable Timers</span></span>  
  
3.  <span data-ttu-id="606cf-111">拡張ポイントを使用するための <xref:System.Activities.NativeActivity%601> の使用</span><span class="sxs-lookup"><span data-stu-id="606cf-111">Use of <xref:System.Activities.NativeActivity%601> for using Extensibility points</span></span>  
  
4.  <span data-ttu-id="606cf-112">SendEmail アクティビティでの <xref:System.Activities.CodeActivity%601> の使用</span><span class="sxs-lookup"><span data-stu-id="606cf-112">Use of <xref:System.Activities.CodeActivity%601> in the SendEmail activity</span></span>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  <span data-ttu-id="606cf-113">XAML のみのワークフロー</span><span class="sxs-lookup"><span data-stu-id="606cf-113">XAML-only workflow</span></span>  
  
 <span data-ttu-id="606cf-114">このサンプルでは、<xref:System.DateTime> を取得するカスタム アクティビティの作成方法と、永続的なタイマーを使用して遅延期間を登録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="606cf-114">This sample demonstrates how to create a custom activity which takes in a <xref:System.DateTime> and uses durable timers to register the delay duration.</span></span> <span data-ttu-id="606cf-115">永続的なタイマーを使用している場合は、<xref:System.Activities.NativeActivity> を使用してブックマークを作成する必要があります。このブックマークをタイマー拡張に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="606cf-115">When using durable timers, you must use a <xref:System.Activities.NativeActivity> to create a bookmark, as you will need to register this bookmark with the timer extension.</span></span> <span data-ttu-id="606cf-116">このサンプルでは、永続的なタイマーが時間切れになると、`OnTimerExpired` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="606cf-116">In this sample, when the durable timer expires, the `OnTimerExpired` method will be called.</span></span> <span data-ttu-id="606cf-117">タイマー拡張を <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> イベントに追加して、この情報がランタイムに確実に提供されるようにします。</span><span class="sxs-lookup"><span data-stu-id="606cf-117">Make sure that you are adding the timer extension in the <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> event to ensure you are providing the runtime with this information.</span></span> <span data-ttu-id="606cf-118">永続的なタイマーは <xref:System.DateTime> のみを取得するため、その他の実装詳細として挙げられるものは、<xref:System.TimeSpan> から <xref:System.DateTime> に変換するためのロジックを実装する必要があることのみです。</span><span class="sxs-lookup"><span data-stu-id="606cf-118">The only other implementation detail is that you will need to implement logic to convert from <xref:System.DateTime> to <xref:System.TimeSpan>, as durable timers only take in a <xref:System.DateTime>.</span></span> <span data-ttu-id="606cf-119">次の操作を行うことで、精度に小さな逸脱があることに注意します。</span><span class="sxs-lookup"><span data-stu-id="606cf-119">Do note that there is a small lapse in accuracy by doing</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="606cf-120"><xref:System.DateTime> から <xref:System.TimeSpan> への変換により、精度が若干低下します。</span><span class="sxs-lookup"><span data-stu-id="606cf-120">There is a small loss of accuracy by converting from <xref:System.DateTime> to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="606cf-121">このサンプルは、<xref:System.Activities.WorkflowApplication> の永続性をオンにする方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="606cf-121">This sample also demonstrates how to turn on persistence for a <xref:System.Activities.WorkflowApplication>.</span></span> <span data-ttu-id="606cf-122">このサンプルでは、タイマーの時間切れを待機している間のアイドル時間中にワークフロー データが永続性データベースにアンロードされる永続的なタイマーを使用します。</span><span class="sxs-lookup"><span data-stu-id="606cf-122">For this particular sample, we will be using durable timers in which the workflow data will be unloaded into the persistence database during the idle time while waiting for timer to expire.</span></span> <span data-ttu-id="606cf-123">この実装は、他の永続性アクションにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="606cf-123">This implementation can also be used for other persistence actions.</span></span> <span data-ttu-id="606cf-124">このサンプルは、SQL Server で永続性接続文字列を設定する方法、およびワークフロー インスタンスのデータを永続化するためにインスタンス ストアを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="606cf-124">This sample shows how to set up the persistence connection string with SQL Server, and how to create the instance store in order to persist the data for workflow instances.</span></span> <span data-ttu-id="606cf-125">ワークフロー インスタンスを実行可能にするイベントが発生した後でワークフローを再開する方法に関するロジックも提供されています。</span><span class="sxs-lookup"><span data-stu-id="606cf-125">Logic is provided on how to resume the workflow once an event is raised which makes the workflow instance runnable.</span></span>  
  
 <span data-ttu-id="606cf-126">このサンプルをステップ実行するを組み込みの待機時間を開始および完了に時間がかかると送信される電子メール メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="606cf-126">As you step through this sample, you will see the time in which the built-in delay begins and completes, which in turn will cause an email message to be sent.</span></span> <span data-ttu-id="606cf-127">ここから、AbsoluteDelay アクティビティは指定した <xref:System.DateTime> まで (または <xref:System.DateTime> を経過している場合は 0 秒間) 停止します。時間切れになると、電子メールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="606cf-127">From there, the AbsoluteDelay activity will halt until a specified <xref:System.DateTime> (or 0 seconds if the <xref:System.DateTime> has expired) which in turn will send out an email upon expiration.</span></span> <span data-ttu-id="606cf-128">これは、組み込みの <xref:System.Activities.Statements.Delay> 機能と AbsoluteDelay アクティビティの使用の 2 つの異なるユース ケースを示します。</span><span class="sxs-lookup"><span data-stu-id="606cf-128">This will show the two different use cases of the built-in <xref:System.Activities.Statements.Delay> functionality versus using an AbsoluteDelay activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="606cf-129">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="606cf-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="606cf-130">SQL Server Express (またはそれ以降) がコンピューターにインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="606cf-130">Ensure you have SQL Server Express (or higher) installed on your machine</span></span>  
  
2.  <span data-ttu-id="606cf-131">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトで setup.cmd (WF/Basic/Services/AbsoluteDelay/CS にあります) を実行して AbsoluteDelaySampleDB データベースを作成し、永続性スキーマと永続性ロジックを作成します。</span><span class="sxs-lookup"><span data-stu-id="606cf-131">Run setup.cmd (from WF/Basic/Services/AbsoluteDelay/CS) in a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt to create the AbsoluteDelaySampleDB database, create the persistence schema and create the persistence logic.</span></span>  
  
3.  <span data-ttu-id="606cf-132">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="606cf-132">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="606cf-133">Delay アクティビティに Duration を指定します。</span><span class="sxs-lookup"><span data-stu-id="606cf-133">Specify the Duration in the Delay activity.</span></span>  
  
5.  <span data-ttu-id="606cf-134">AbsoluteDelay アクティビティに ExpirationTime を指定します。</span><span class="sxs-lookup"><span data-stu-id="606cf-134">Specify the ExpirationTime in the AbsoluteDelay activity.</span></span>  
  
6.  <span data-ttu-id="606cf-135">SendMail アクティビティの SendMailTo、SendMailFrom、SendMailSubject、SendMailBody、SmtpHost の各フィールドを更新します。</span><span class="sxs-lookup"><span data-stu-id="606cf-135">Update the SendMailTo, SendMailFrom, SendMailSubject, SendMailBody, and SmtpHost fields in the SendMail activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="606cf-136">有効な SMTP ホストを入力しない場合は、アプリケーションで SMTP 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="606cf-136">If you do not enter a valid SMTP host, the application will throw a SMTP exception.</span></span>  
  
7.  <span data-ttu-id="606cf-137">選択して、ソリューションをビルド**ビルド**、**ソリューションのビルド**です。</span><span class="sxs-lookup"><span data-stu-id="606cf-137">Build the solution by selecting **Build**, **Build Solution**.</span></span>  
  
8.  <span data-ttu-id="606cf-138">キーを押して、ソリューションを実行**f5 キーを押して**です。</span><span class="sxs-lookup"><span data-stu-id="606cf-138">Run the solution by pressing **F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="606cf-139">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="606cf-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="606cf-140">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="606cf-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="606cf-141">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="606cf-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="606cf-142">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="606cf-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
