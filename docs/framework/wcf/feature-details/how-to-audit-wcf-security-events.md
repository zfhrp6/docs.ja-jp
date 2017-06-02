---
title: "方法 : Windows Communication Foundation セキュリティ イベントを監査する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "セキュリティ [WCF], イベントの監査"
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
caps.latest.revision: 19
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 19
---
# 方法 : Windows Communication Foundation セキュリティ イベントを監査する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] にはセキュリティ イベントを Windows イベント ログに記録する機能があります。これは Windows イベント ビューアーに表示できます。  このトピックでは、セキュリティ イベントをログ出力するようにアプリケーションを設定する方法について説明します。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 監査については、「[監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)」を参照してください。  
  
### セキュリティ イベントを監査するコードを記述するには  
  
1.  監査ログの場所を指定します。  それには、次のコードに示すように、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> クラスの <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> プロパティに <xref:System.ServiceModel.AuditLogLocation> 列挙体のいずれかの値を設定します。  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation> 列挙体には `Application`、`Security`、および `Default` の 3 つの値が定義されています。  これは、イベント ビューアーを開いたとき、セキュリティ ログとアプリケーション ログのどちらが表示されるかを表します。  `Default` を指定した場合の動作は、アプリケーションが稼働するオペレーティング システムに依存します。  ログの場所を指定せずに監査機能を有効にした場合、セキュリティ ログに書き込み可能なプラットフォームであれば `Security` ログに、そうでなければ `Application` ログに出力するようになります。  セキュリティ ログへの書き込みが可能なのは、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] と [!INCLUDE[wv](../../../../includes/wv-md.md)] に限ります。  
  
2.  イベントの種類を監査対象として設定します。  サービス レベルのイベントとメッセージ レベルの承認イベントを同時に監査できます。  それには、次のコードに示すように、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> プロパティまたは <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> プロパティに <xref:System.ServiceModel.AuditLevel> 列挙体のいずれかの値を設定します。  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  ログ監査イベントに関して、単に無視してアプリケーションの処理を続行するか、それとも失敗を通知するかを設定します。  次のコードに示すように、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> プロパティに `true` または `false` を設定します。  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     `SuppressAuditFailure` プロパティの既定値は `true` なので、監査に失敗してもアプリケーションには影響しません。  それ以外の場合は、例外がスローされます。  正常な監査に関するログは、Verbose レベルで出力されます。  異常発生時には、Error レベルでトレースが出力されます。  
  
4.  既存の <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> を、<xref:System.ServiceModel.ServiceHost> の説明にある動作のコレクションから削除します。  動作のコレクションは、<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> プロパティからアクセスできます。また、<xref:System.ServiceModel.ServiceHostBase.Description%2A> プロパティからもアクセスできます。  その後、次のコードに示すように、新しい <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> を同じコレクションに追加します。  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### 構成ファイルで監査を設定するには  
  
1.  構成ファイルで監査を設定するには、web.config ファイルの [\<behaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) セクションに [\<behavior\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 要素を追加します。  その後、次の例に示すように、[\<serviceSecurityAudit\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) 要素を追加し、必要な属性を設定します。  
  
    ```  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"   
                serviceAuthorizationAuditLevel="None"   
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2.  次の例に示すように、サービスに対して動作を指定する必要があります。  
  
    ```  
    <services>  
        <service type="WCS.Samples.Service.Echo"   
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"   
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
  
    ```  
  
## 使用例  
 <xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成し、新しい <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> をその動作のコレクションに追加するコード例を次に示します。  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## .NET Framework セキュリティ  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> プロパティを `true` に設定すると、セキュリティ監査を生成する失敗が抑制されます \(`false` に設定した場合は、例外がスローされます\)。  ただし、次の Windows の **"ローカル セキュリティ設定"** プロパティを有効にした場合、監査イベントを生成する失敗により Windows が直ちにシャットダウンします。  
  
 **監査 : セキュリティ監査を記録できない場合システムを直ちにシャット ダウンします。**  
  
 プロパティを設定するには、**\[ローカル セキュリティ 設定\]** ダイアログ ボックスを開きます。  **\[セキュリティの設定\]** の **\[ローカル ポリシー\]** フォルダーをクリックします。  次に、**\[セキュリティ オプション\]** をクリックします。  
  
 <xref:System.ServiceModel.AuditLogLocation> プロパティが <xref:System.ServiceModel.AuditLogLocation> に設定されている場合で、**\[オブジェクト アクセスの監査\]** が **\[ローカル セキュリティ ポリシー\]** で設定されていないときは、監査イベントはセキュリティ ログに書き込まれません。  エラーが返らない場合でも、監査エントリはセキュリティ ログに書き込まれません。  
  
## 参照  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>   
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>   
 <xref:System.ServiceModel.AuditLogLocation>   
 [監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)