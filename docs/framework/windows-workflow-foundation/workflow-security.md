---
title: "ワークフローのセキュリティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プログラミング [WF], ワークフローのセキュリティ"
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# ワークフローのセキュリティ
[!INCLUDE[wf](../../../includes/wf-md.md)] は、Microsoft SQL Server や [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] などの複数のさまざまなテクノロジと統合されています。  これらのテクノロジと相互作用するうえで、不適切に実行された場合にワークフローでセキュリティの問題が発生することがあります。  
  
## 永続化のセキュリティに関する注意事項  
  
1.  <xref:System.Activities.Statements.Delay> アクティビティと永続化を使用するワークフローは、サービスによって再アクティブ化する必要があります。  Windows AppFabric はワークフロー管理サービス \(WMS\) を使用して、タイマーが期限切れのワークフローを再アクティブ化します。  WMS は <xref:System.ServiceModel.WorkflowServiceHost> を作成して、再アクティブ化されたワークフローをホストします。  WMS サービスが停止した場合、永続化されたワークフローはタイマーが時間切れになっていると再アクティブ化されません。  
  
2.  永続的なインスタンスへのアクセスは、アプリケーション ドメイン外の安全でないエンティティから保護する必要があります。  また、開発者は、悪意のあるコードが永続性インスタンス化コードと同じアプリケーション ドメインで実行できないようにする必要があります。  
  
3.  永続性インスタンス化は、高い \(管理者の\) アクセス許可で実行しないでください。  
  
4.  アプリケーション ドメインの外部で処理されるデータは、保護する必要があります。  
  
5.  セキュリティの分離を必要とするアプリケーションは、スキーマ抽象化と同じインスタンスを共有しないようにします。  このようなアプリケーションは、異なるストア プロバイダーを使用するか、別のストアのインスタンス化を使用するように構成されたストア プロバイダーを使用する必要があります。  
  
## SQL サーバーのセキュリティに関する注意事項  
  
-   子アクティビティ、場所、ブックマーク、ホストの拡張機能、またはスコープを多数使用する場合、またはペイロードが非常に大きいブックマークを使用する場合、メモリが不足したり、永続化の実行中に必要以上のディスク容量が割り当てられる可能性があります。  オブジェクト レベルおよびデータベース レベルのセキュリティを使用すると、このような状態を緩和できます。  
  
-   <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用する場合、インスタンス ストアをセキュリティで保護する必要があります。  「[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][SQL Server ベスト プラクティス](http://go.microsoft.com/fwlink/?LinkId=164972)」。  
  
-   インスタンス ストアの機密情報は暗号化する必要があります。  「[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][SQL のセキュリティの暗号化](http://go.microsoft.com/fwlink/?LinkId=164976)」。  
  
-   多くの場合、データベース接続文字列は構成ファイルに含まれているので、Windows レベルのセキュリティ \(ACL\) を使用して、構成ファイル \(通常は Web.Config\) が安全であるように、またログインとパスワードの情報が接続文字列に含まれないようにする必要があります。  Windows 認証をデータベースと Web サーバー間で代わりに使用する必要があります。  
  
## WorkflowServiceHost に関する考慮事項  
  
-   ワークフローで使用されている [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] のエンドポイントは、セキュリティで保護される必要があります。  「[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF のセキュリティの概要](http://go.microsoft.com/fwlink/?LinkID=164975)」。  
  
-   <xref:System.ServiceModel.ServiceAuthorizationManager> を使用して、ホスト レベルの認証を実装できます。  詳細については、「[方法 : サービスで使用するカスタム承認マネージャーを作成する](http://go.microsoft.com/fwlink/?LinkId=192228)」を参照してください。  これは、サンプル「[ワークフロー サービスのセキュリティ保護](../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md)」でも説明されています。  
  
-   受信メッセージの ServiceSecurityContext は、OperationContext へのアクセスによって、ワーク フロー内からも使用できます。  詳細については、「[ワークフロー サービスから OperationContext へのアクセス](../../../docs/framework/wcf/feature-details/accessing-operationcontext-from-a-workflow-service.md)」を参照してください。  
  
## WF Security Pack CTP  
 Microsoft WF Security Pack CTP 1 は、[.NET Framework 4](http://msdn.microsoft.com/netframework/default.aspx) \(WF 4\) の [Windows Workflow Foundation](http://msdn.microsoft.com/netframework/aa663328.aspx) と [Windows Identity Foundation \(WIF\)](http://msdn.microsoft.com/security/aa570351.aspx) に基づく、一連のアクティビティとその実装の最初の Community Technology Preview \(CTP\) リリースです。  Microsoft WF Security Pack CTP 1 には、アクティビティおよび、ワークフローを使用してさまざまなセキュリティ関連のシナリオを簡単に有効にする方法を示すそのデザイナーの両方が含まれています。これらには以下のものが含まれます。  
  
1.  ワークフローのクライアント ID の偽装  
  
2.  PrincipalPermission やクレームの検証などの内部ワークフローの認証  
  
3.  ユーザー名\/パスワードやセキュリティ トークン サービス \(STS\) から取得するトークンなど、ワークフローで指定される ClientCredentials を使用した認証されたメッセージ  
  
4.  WS\-Trust ActAs を使用して、クライアント セキュリティ トークンをバックエンド サービス \(クレーム ベースの委任\) にフロー  
  
 詳細については、また WF Security Pack CTP をダウンロードするには、「[WF Security Pack CTP](http://wf.codeplex.com/releases/view/48114)」を参照してください。