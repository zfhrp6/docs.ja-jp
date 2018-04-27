---
title: Windows のイベント トレースへの追跡イベント
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1a1038f848563c106ee1cac441b8a247e161e268
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="7365d-102">Windows のイベント トレースへの追跡イベント</span><span class="sxs-lookup"><span data-stu-id="7365d-102">Tracking Events into Event Tracing in Windows</span></span>
<span data-ttu-id="7365d-103">このサンプルでは、Windows Workflow Foundation (WF) ワークフロー サービスの追跡を有効にして、イベント トレース for Windows (ETW) で追跡イベントを出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7365d-103">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="7365d-104">ワークフロー追跡レコードを ETW に出力するために、このサンプルでは ETW 追跡参加要素 (<xref:System.Activities.Tracking.EtwTrackingParticipant>) を使用します。</span><span class="sxs-lookup"><span data-stu-id="7365d-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>  
  
 <span data-ttu-id="7365d-105">このサンプルのワークフローでは、要求を受け取り、入力データの逆数を入力変数に割り当てて、クライアントに逆数を返します。</span><span class="sxs-lookup"><span data-stu-id="7365d-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="7365d-106">入力データが 0 の場合、処理されない 0 による除算の例外が発生し、ワークフローが中止されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="7365d-107">追跡を有効にすると、エラー追跡レコードが ETW に出力され、後でエラーをトラブルシューティングする際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7365d-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="7365d-108">ETW 追跡参加要素は、追跡レコードを定期受信するように追跡プロファイルで構成されています。</span><span class="sxs-lookup"><span data-stu-id="7365d-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="7365d-109">追跡プロファイルは、Web.config ファイルで定義され、構成パラメーターとして ETW 追跡参加要素に渡されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="7365d-110">ETW 追跡参加要素は、ワークフロー サービスの Web.config ファイルで構成され、サービス動作としてサービスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="7365d-111">このサンプルでは、イベント ログの追跡イベントをイベント ビューアーを使用して確認します。</span><span class="sxs-lookup"><span data-stu-id="7365d-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>  
  
## <a name="workflow-tracking-details"></a><span data-ttu-id="7365d-112">ワークフロー追跡の詳細</span><span class="sxs-lookup"><span data-stu-id="7365d-112">Workflow Tracking Details</span></span>  
 <span data-ttu-id="7365d-113">Windows Workflow Foundation では、ワークフロー インスタンスの実行を追跡できる追跡インフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="7365d-113">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="7365d-114">追跡ランタイムは、ワークフロー ライフサイクルに関連するイベント、ワークフロー アクティビティのイベント、およびカスタム イベントを出力するワークフロー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="7365d-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="7365d-115">次の表で、追跡インフラストラクチャの主要コンポーネントの詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="7365d-115">The following table details the primary components of the tracking infrastructure.</span></span>  
  
|<span data-ttu-id="7365d-116">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7365d-116">Component</span></span>|<span data-ttu-id="7365d-117">説明</span><span class="sxs-lookup"><span data-stu-id="7365d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7365d-118">追跡ランタイム</span><span class="sxs-lookup"><span data-stu-id="7365d-118">Tracking runtime</span></span>|<span data-ttu-id="7365d-119">追跡レコードを出力するためのインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="7365d-119">Provides the infrastructure to emit tracking records.</span></span>|  
|<span data-ttu-id="7365d-120">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="7365d-120">Tracking participants</span></span>|<span data-ttu-id="7365d-121">追跡レコードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7365d-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="7365d-122"> には、追跡レコードを Event Tracing for Windows (ETW) イベントとして書き込む追跡参加要素が用意されています。</span><span class="sxs-lookup"><span data-stu-id="7365d-122"> ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|  
|<span data-ttu-id="7365d-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="7365d-123">Tracking profile</span></span>|<span data-ttu-id="7365d-124">ワークフロー インスタンスから出力された追跡レコードのサブセットを追跡参加要素から定期受信するためのフィルター機構。</span><span class="sxs-lookup"><span data-stu-id="7365d-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|  
  
 <span data-ttu-id="7365d-125">次の表で、ワークフロー ランタイムが出力する追跡レコードの詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="7365d-125">The following table details the tracking records that the workflow runtime emits.</span></span>  
  
|<span data-ttu-id="7365d-126">追跡レコード</span><span class="sxs-lookup"><span data-stu-id="7365d-126">Tracking record</span></span>|<span data-ttu-id="7365d-127">説明</span><span class="sxs-lookup"><span data-stu-id="7365d-127">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="7365d-128">ワークフロー インスタンスの追跡レコード</span><span class="sxs-lookup"><span data-stu-id="7365d-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="7365d-129">ワークフロー インスタンスのライフサイクルを表します。</span><span class="sxs-lookup"><span data-stu-id="7365d-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="7365d-130">たとえば、ワークフローの開始時または完了時にインスタンス レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|  
|<span data-ttu-id="7365d-131">アクティビティ状態の追跡レコード</span><span class="sxs-lookup"><span data-stu-id="7365d-131">Activity state tracking records.</span></span>|<span data-ttu-id="7365d-132">アクティビティの実行状況を詳しく記録します。</span><span class="sxs-lookup"><span data-stu-id="7365d-132">Details activity execution.</span></span> <span data-ttu-id="7365d-133">これらのレコードは、アクティビティをスケジュールしたとき、アクティビティが完了したとき、エラーがスローされたときなど、ワークフロー アクティビティの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="7365d-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|  
|<span data-ttu-id="7365d-134">ブックマーク再開レコード</span><span class="sxs-lookup"><span data-stu-id="7365d-134">Bookmark resumption record.</span></span>|<span data-ttu-id="7365d-135">ワークフロー インスタンス内のブックマークが再開されたときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|  
|<span data-ttu-id="7365d-136">カスタム追跡レコード</span><span class="sxs-lookup"><span data-stu-id="7365d-136">Custom tracking records.</span></span>|<span data-ttu-id="7365d-137">ワークフロー作成者はカスタム追跡レコードを作成し、カスタム アクティビティ内で出力できます。</span><span class="sxs-lookup"><span data-stu-id="7365d-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="7365d-138">このレコードは、アクティビティが別のアクティビティをスケジュールするときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-138">This record is emitted when an activity schedules another activity.</span></span>|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="7365d-139">このレコードは、アクティビティからエラーが伝達されたときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-139">This record is emitted when a fault is propagated from an activity.</span></span>|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="7365d-140">このレコードは、アクティビティが別のアクティビティによって取り消されたときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-140">This record is emitted when an activity is canceled by another activity.</span></span>|  
  
 <span data-ttu-id="7365d-141">追跡参加要素は、追跡プロファイルを使用して、出力された追跡レコードのサブセットを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="7365d-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="7365d-142">追跡プロファイルには、特定の追跡レコード タイプを定期受信するための追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7365d-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="7365d-143">追跡プロファイルは、コードで指定したり、構成で指定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7365d-143">Tracking profiles can be specified in code or in configuration.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7365d-144">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="7365d-144">To use this sample</span></span>  
  
1.  <span data-ttu-id="7365d-145">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、EtwTrackingParticipantSample.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7365d-145">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EtwTrackingParticipantSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7365d-146">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7365d-146">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7365d-147">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7365d-147">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="7365d-148">既定では、サービスがリッスンしているポート 53797 (http://localhost:53797/SampleWorkflowService.xamlx)です。</span><span class="sxs-lookup"><span data-stu-id="7365d-148">By default, the service is listening on port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span></span>  
  
4.  <span data-ttu-id="7365d-149">[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、WCF テスト クライアントを開きます。</span><span class="sxs-lookup"><span data-stu-id="7365d-149">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="7365d-150">WCF テスト クライアント (WcfTestClient.exe) にあります、 \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]インストール フォルダー > \Common7\IDE\ フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="7365d-150">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="7365d-151">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] の既定のインストール フォルダーは C:\Program Files\Microsoft Visual Studio 10.0 です。</span><span class="sxs-lookup"><span data-stu-id="7365d-151">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
5.  <span data-ttu-id="7365d-152">WCF テスト クライアントで、次のように選択します。**サービスの追加**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="7365d-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="7365d-153">入力ボックスにエンドポイントのアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="7365d-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="7365d-154">既定値は、http://localhost:53797/SampleWorkflowService.xamlx です。</span><span class="sxs-lookup"><span data-stu-id="7365d-154">The default is http://localhost:53797/SampleWorkflowService.xamlx.</span></span>  
  
6.  <span data-ttu-id="7365d-155">イベント ビューアー アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="7365d-155">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="7365d-156">サービスを呼び出す前に起動してからイベント ビューアー、**開始**メニューの **実行**に入力`eventvwr.exe`です。</span><span class="sxs-lookup"><span data-stu-id="7365d-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="7365d-157">ワークフロー サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7365d-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="7365d-158">イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、および**Microsoft**です。</span><span class="sxs-lookup"><span data-stu-id="7365d-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="7365d-159">右クリック**Microsoft**選択**ビュー**し**分析およびデバッグ ログ**分析を有効にして、デバッグ ログに</span><span class="sxs-lookup"><span data-stu-id="7365d-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>  
  
     <span data-ttu-id="7365d-160">いることを確認、 **分析およびデバッグ ログ**オプションはオンにします。</span><span class="sxs-lookup"><span data-stu-id="7365d-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
8.  <span data-ttu-id="7365d-161">イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 **アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="7365d-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="7365d-162">右クリック**分析**選択**ログの有効化**を有効にする、**分析**ログ。</span><span class="sxs-lookup"><span data-stu-id="7365d-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>  
  
9. <span data-ttu-id="7365d-163">WCF テスト クライアントで、`GetData` をダブルクリックしてサービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="7365d-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>  
  
     <span data-ttu-id="7365d-164">`GetData` メソッドが開きます。</span><span class="sxs-lookup"><span data-stu-id="7365d-164">This opens the `GetData` method.</span></span> <span data-ttu-id="7365d-165">この要求はパラメーターを 1 つ受け取ります。値が 0 (既定値) になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7365d-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>  
  
     <span data-ttu-id="7365d-166">をクリックして**呼び出す**です。</span><span class="sxs-lookup"><span data-stu-id="7365d-166">Click **Invoke**.</span></span>  
  
10. <span data-ttu-id="7365d-167">ワークフローから出力されたイベントを確認します。</span><span class="sxs-lookup"><span data-stu-id="7365d-167">Observe the events emitted from the workflow.</span></span>  
  
     <span data-ttu-id="7365d-168">イベント ビューアーに戻りに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 **アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="7365d-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="7365d-169">右クリック**分析**選択**更新**です。</span><span class="sxs-lookup"><span data-stu-id="7365d-169">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="7365d-170">イベント ビューアーにワークフロー イベントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="7365d-171">ワークフロー実行イベントが表示され、その中にワークフローのエラーに対応する未処理の例外が含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7365d-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="7365d-172">また、アクティビティがエラーをスローしたことを示す警告イベントもワークフロー アクティビティから出力されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>  
  
11. <span data-ttu-id="7365d-173">エラーがスローされないように入力データを 0 以外にして、手順 9. と 10. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="7365d-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>  
  
 <span data-ttu-id="7365d-174">追跡プロファイルを使用すると、実行時にワークフロー インスタンスの状態が変化したときに生成されるイベントを定期受信できます。</span><span class="sxs-lookup"><span data-stu-id="7365d-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="7365d-175">監視の要件に応じて、ワークフローの主な状態変化の少数のセットを定期受信する、大まかなプロファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7365d-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="7365d-176">それとは反対に、後で実行を十分に再構築できるほど出力が豊富な、詳細なプロファイルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="7365d-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="7365d-177">このサンプルでは、イベントの少数のセットを出力する `HealthMonitoring Tracking Profile` を使用して、ワークフロー ランタイムから ETW に出力されるイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="7365d-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="7365d-178">Web.config には、それよりも多くのワークフロー追跡イベントを出力する `Troubleshooting Tracking Profile` という名前の別のプロファイルも用意されています。</span><span class="sxs-lookup"><span data-stu-id="7365d-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="7365d-179">[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] をインストールすると、Machine.config ファイルでは、空の名前の既定のプロファイルが構成されています。</span><span class="sxs-lookup"><span data-stu-id="7365d-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="7365d-180">このプロファイルは、プロファイル名が指定されなかった場合や空のプロファイル名が指定された場合に、ETW 追跡動作の構成で使用されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>  
  
 <span data-ttu-id="7365d-181">状態監視追跡プロファイルでは、ワークフロー インスタンス レコードとアクティビティ エラー伝達レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="7365d-182">このプロファイルは、Web.config 構成ファイルに次の追跡プロファイルを追加して作成されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>  
  
```xml  
<<tracking>  
      <profiles>  
        <trackingProfile name="HealthMonitoring Tracking Profile">  
          <workflow activityDefinitionId="*">  
            <workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="Started"/>  
                  <state name="Completed"/>  
                  <state name="Aborted"/>  
                  <state name="UnhandledException"/>  
                </states>  
            </workflowInstanceQuery>  
           </workflowInstanceQueries>  
            <faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
            </faultPropagationQueries>  
          </workflow>  
        </trackingProfile>  
       </profiles>  
</tracking>  
```  
  
 <span data-ttu-id="7365d-183">プロファイルを変更するには、`EtwTrackingParticipant` 構成を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="7365d-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="7365d-184">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="7365d-184">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="7365d-185">イベント ビューアーを開きます。</span><span class="sxs-lookup"><span data-stu-id="7365d-185">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="7365d-186">移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーションサーバー アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="7365d-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="7365d-187">右クリック**分析**選択**ログの無効化**です。</span><span class="sxs-lookup"><span data-stu-id="7365d-187">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="7365d-188">移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーションサーバー アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="7365d-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="7365d-189">右クリック**分析**選択**ログの消去**です。</span><span class="sxs-lookup"><span data-stu-id="7365d-189">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="7365d-190">選択、**オフ**イベントをクリアするにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="7365d-190">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="7365d-191">既知の問題</span><span class="sxs-lookup"><span data-stu-id="7365d-191">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7365d-192">イベント ビューアーの既知の問題により、ETW イベントをデコードできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7365d-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="7365d-193">その場合、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-193">You may see an error message that looks like the following.</span></span>  
>   
>  <span data-ttu-id="7365d-194">イベント ID の説明\<id > 元の Microsoft Windows アプリケーション サーバー-アプリケーションが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="7365d-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="7365d-195">このイベントを発生させるコンポーネントがローカル コンピューターにインストールされていないか、インストールが破損しています。</span><span class="sxs-lookup"><span data-stu-id="7365d-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="7365d-196">ローカル コンピューターにコンポーネントをインストールするか、コンポーネントを修復してください。</span><span class="sxs-lookup"><span data-stu-id="7365d-196">You can install or repair the component on the local computer.</span></span>  
>   
>  <span data-ttu-id="7365d-197">このエラーが発生した場合は、操作ウィンドウで [最新の情報に更新] をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="7365d-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="7365d-198">これにより、イベントが正常にデコードされます。</span><span class="sxs-lookup"><span data-stu-id="7365d-198">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7365d-199">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7365d-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7365d-200">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7365d-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7365d-201">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7365d-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7365d-202">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7365d-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a><span data-ttu-id="7365d-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="7365d-203">See Also</span></span>  
 [<span data-ttu-id="7365d-204">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="7365d-204">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
