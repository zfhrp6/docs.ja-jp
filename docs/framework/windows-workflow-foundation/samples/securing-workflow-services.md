---
title: "ワークフロー サービスのセキュリティ保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cd7620186ed51110a32e251d5239c85bb90e0f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="securing-workflow-services"></a>ワークフロー サービスのセキュリティ保護
セキュリティで保護されたワークフロー サービス サンプルでは、次の手順を示します。  
  
-   <xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティを使用して基本ワークフロー サービスを作成する。  
  
-   [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 構成を使用して、ワークフロー サービスで使用するセキュリティで保護されたエンドポイントを定義する。  
  
-   カスタム ポリシー内にクレームを作成し、<xref:System.ServiceModel.ServiceAuthorizationManager> を使用してクレームを検証する。  
  
## <a name="demonstrates"></a>使用例  
 WCF セキュリティを使用して、クライアントとワークフロー サービス間の通信、クレーム ベースの承認を保護します。  
  
## <a name="discussion"></a>説明  
 このサンプルでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティ インフラストラクチャを使用して、通常の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと同様にワークフロー サービスをセキュリティで保護する方法を示します。 具体的には、承認にカスタム クレームを使用します。 この例では、<xref:System.ServiceModel.WSHttpBinding> とメッセージ モード セキュリティを Windows 資格情報と共に使用します。  
  
 カスタムの <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) は、クライアントの Windows ユーザー名をチェックし、特定の文字がないか確認します。 該当する文字がある場合は、クレームを作成して <xref:System.IdentityModel.Policy.EvaluationContext> に追加します。 このようにすることで、カスタム ポリシーは、クライアントのユーザー名にこの文字が含まれていることを示すステートメントを作成します。 このクレームは、呼び出しの有効期間においてクエリできます。 該当の文字は `Constants.cs` で検索できます。  
  
 承認ポリシーは、`SecureWorkFlowAuthZManager` 内のクレームを探します。 クレームが見つかると、`true` を返し、ワークフローを続行できるようにします。 クレームが見つからない場合は、`false` を返し、クライアントには "アクセスは拒否されました" メッセージが返されます。 他のクレームもコンテキスト内にあり、`SecureWorkFlowAuthZManager` 内で調べることができます。  
  
#### <a name="to-run-this-sample"></a>このサンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を管理者権限で実行します。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] に SecuringWorkflowServices.sln を読み込みます。  
  
3.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをコンパイルします。  
  
4.  Service プロジェクトをソリューションのスタートアップ プロジェクトに設定します。  
  
5.  Ctrl キーを押しながら F5 キーを押して、デバッグを行わずにサービスを起動します。  
  
6.  Client プロジェクトをソリューションのスタートアップ プロジェクトに設定します。  
  
7.  Ctrl キーを押しながら F5 キーを押して、デバッグを行わずにクライアントを起動します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
