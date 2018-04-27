---
title: 追跡を使用したアプリケーションのトラブルシューティング
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: adc9a159b8887b0198cf19891f73fdee2a48437b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="a6a61-102">追跡を使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a6a61-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="a6a61-103">Windows Workflow Foundation (WF) では、Windows Workflow Foundation のアプリケーションまたはサービスの実行時に詳細を提供するワークフローの関連情報を追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="a6a61-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="a6a61-104">Windows Workflow Foundation ホストは、ワークフロー インスタンスの実行中にワークフロー イベントをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="a6a61-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="a6a61-105">ワークフローは、エラーまたは例外を生成する場合は、その処理のトラブルシューティングの詳細を追跡する Windows Workflow Foundation を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6a61-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="a6a61-106">WF の追跡を使用した WF のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a6a61-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="a6a61-107">Windows Workflow Foundation アクティビティの処理内のエラーを検出するには、照会する追跡プロファイルで追跡を有効にできます、 <xref:System.Activities.Tracking.ActivityStateRecord> Faulted の状態にします。</span><span class="sxs-lookup"><span data-stu-id="a6a61-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="a6a61-108">対応するクエリは、次のコードで指定されています。</span><span class="sxs-lookup"><span data-stu-id="a6a61-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="a6a61-109">エラーがエラー ハンドラー (<xref:System.Activities.Statements.TryCatch> アクティビティなど) 内で反映および処理される場合、<xref:System.Activities.Tracking.FaultPropagationRecord> を使用して検出できます。</span><span class="sxs-lookup"><span data-stu-id="a6a61-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="a6a61-110"><xref:System.Activities.Tracking.FaultPropagationRecord> は、エラーのソース アクティビティとエラー ハンドラーの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="a6a61-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="a6a61-111"><xref:System.Activities.Tracking.FaultPropagationRecord> には、エラーに関する例外スタックの形式でエラーの詳細が含まれます。<xref:System.Activities.Tracking.FaultPropagationRecord> を定期受信するクエリを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="a6a61-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="a6a61-112">エラーがワークフロー内で処理されない場合は、ワークフロー インスタンスでハンドルされない例外になり、ワークフロー インスタンスは中止されます。</span><span class="sxs-lookup"><span data-stu-id="a6a61-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="a6a61-113">ハンドルされない例外の詳細を把握するために、追跡プロファイルでは、次のように `state name="UnhandledException"` を持つワークフロー インスタンス レコードを照会する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6a61-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="a6a61-114">ワークフロー インスタンスが未処理の例外を検出すると、<xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>オブジェクトは、Windows Workflow Foundation 追跡を有効になっている場合に生成されます。</span><span class="sxs-lookup"><span data-stu-id="a6a61-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="a6a61-115">この追跡レコードには、例外スタックの形式でエラーの詳細が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6a61-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="a6a61-116">障害が発生して、未処理の例外が発生したエラー (たとえば、アクティビティ) のソースの詳細があります。Windows Workflow Foundation のエラー イベントにサブスクライブする、追跡参加要素を追加することによって、追跡を有効にします。</span><span class="sxs-lookup"><span data-stu-id="a6a61-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="a6a61-117">この参加要素は、`ActivityStateQuery (state="Faulted")`、<xref:System.Activities.Tracking.FaultPropagationRecord>、および `WorkflowInstanceQuery (state="UnhandledException")` を照会する追跡プロファイルで構成します。</span><span class="sxs-lookup"><span data-stu-id="a6a61-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="a6a61-118">ETW 追跡参加要素を使用して追跡を有効にした場合、エラー イベントは ETW セッションに書き出されます。</span><span class="sxs-lookup"><span data-stu-id="a6a61-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="a6a61-119">イベントはイベント ビューアーを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="a6a61-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="a6a61-120">これをノードの下見つける**イベント ビューアー] の [アプリケーションとサービス ログ] の [Microsoft]-> [Windows アプリケーション サーバー-アプリケーション]-> [** 分析チャネルでします。</span><span class="sxs-lookup"><span data-stu-id="a6a61-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a61-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6a61-121">See Also</span></span>  
 [<span data-ttu-id="a6a61-122">Windows Server App Fabric の監視</span><span class="sxs-lookup"><span data-stu-id="a6a61-122">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="a6a61-123">アプリケーション App Fabric の監視</span><span class="sxs-lookup"><span data-stu-id="a6a61-123">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
