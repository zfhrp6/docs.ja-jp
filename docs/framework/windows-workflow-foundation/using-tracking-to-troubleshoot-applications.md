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
# <a name="using-tracking-to-troubleshoot-applications"></a>追跡を使用したアプリケーションのトラブルシューティング
Windows Workflow Foundation (WF) では、Windows Workflow Foundation のアプリケーションまたはサービスの実行時に詳細を提供するワークフローの関連情報を追跡することができます。 Windows Workflow Foundation ホストは、ワークフロー インスタンスの実行中にワークフロー イベントをキャプチャできます。 ワークフローは、エラーまたは例外を生成する場合は、その処理のトラブルシューティングの詳細を追跡する Windows Workflow Foundation を使用できます。  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>WF の追跡を使用した WF のトラブルシューティング  
 Windows Workflow Foundation アクティビティの処理内のエラーを検出するには、照会する追跡プロファイルで追跡を有効にできます、 <xref:System.Activities.Tracking.ActivityStateRecord> Faulted の状態にします。 対応するクエリは、次のコードで指定されています。  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 エラーがエラー ハンドラー (<xref:System.Activities.Statements.TryCatch> アクティビティなど) 内で反映および処理される場合、<xref:System.Activities.Tracking.FaultPropagationRecord> を使用して検出できます。 <xref:System.Activities.Tracking.FaultPropagationRecord> は、エラーのソース アクティビティとエラー ハンドラーの名前を示します。 <xref:System.Activities.Tracking.FaultPropagationRecord> には、エラーに関する例外スタックの形式でエラーの詳細が含まれます。<xref:System.Activities.Tracking.FaultPropagationRecord> を定期受信するクエリを次の例に示します。  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 エラーがワークフロー内で処理されない場合は、ワークフロー インスタンスでハンドルされない例外になり、ワークフロー インスタンスは中止されます。 ハンドルされない例外の詳細を把握するために、追跡プロファイルでは、次のように `state name="UnhandledException"` を持つワークフロー インスタンス レコードを照会する必要があります。  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 ワークフロー インスタンスが未処理の例外を検出すると、<xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>オブジェクトは、Windows Workflow Foundation 追跡を有効になっている場合に生成されます。  
  
 この追跡レコードには、例外スタックの形式でエラーの詳細が含まれます。 障害が発生して、未処理の例外が発生したエラー (たとえば、アクティビティ) のソースの詳細があります。Windows Workflow Foundation のエラー イベントにサブスクライブする、追跡参加要素を追加することによって、追跡を有効にします。 この参加要素は、`ActivityStateQuery (state="Faulted")`、<xref:System.Activities.Tracking.FaultPropagationRecord>、および `WorkflowInstanceQuery (state="UnhandledException")` を照会する追跡プロファイルで構成します。  
  
 ETW 追跡参加要素を使用して追跡を有効にした場合、エラー イベントは ETW セッションに書き出されます。 イベントはイベント ビューアーを使用して表示できます。 これをノードの下見つける**イベント ビューアー] の [アプリケーションとサービス ログ] の [Microsoft]-> [Windows アプリケーション サーバー-アプリケーション]-> [** 分析チャネルでします。  
  
## <a name="see-also"></a>関連項目  
 [Windows Server App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [アプリケーション App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201275)
