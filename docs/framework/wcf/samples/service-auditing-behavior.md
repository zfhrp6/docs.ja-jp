---
title: "サービス監査動作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 140793e41be012a777dbfa4bf66528612ab33da7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="service-auditing-behavior"></a>サービス監査動作
このサンプルでは、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> を使用して、サービス操作中にセキュリティ イベントの監査を有効にする方法を示します。 このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。 サービスとクライアントの構成されているを使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。 `mode`の属性、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)に設定されている`Message`と`clientCredentialType`に設定されている`Windows`です。 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービス構成ファイルは、次のように `serviceSecurityAudit` 要素を使用して監査を構成します。  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、コンソール ウィンドウで Enter キーを押します。  
  
 結果として得られる監査ログは、イベント ビューアーを実行して表示できます。 監査イベントは既定で、Windows XP の場合はアプリケーション ログに、Windows Server 2003 と Windows Vista の場合はセキュリティ ログに表示されます。 Windows Server 2008 と Windows 7 では、監査イベントをアプリケーション ログとサービス ログに表示できます。 監査イベントの場所を設定して指定することができます、`auditLogLocation`属性を"Application"または"Security"です。 詳細については、次を参照してください。[する方法: セキュリティ イベントの監査](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)です。 イベントをセキュリティ ログに書き込む場合は、[ローカル セキュリティ ポリシー] の [オブジェクト アクセスの監査] で、[成功] と [失敗] のチェック ボックスをオンにする必要があります。  
  
 イベント ログを調べる場合、監査イベントのソースは "ServiceModel Audit 3.0.0.0" です。 サービス承認監査レコードの"ServiceAuthorization"のカテゴリに、メッセージ認証監査レコードは"MessageAuthentication"のカテゴリがします。  
  
 メッセージ認証監査イベントは、メッセージの改ざんや期限切れの有無、クライアントによるサービス認証の成否などに適用されます。 このイベントでは、認証の成功または失敗に関する情報とクライアント ID、およびメッセージ送信先のエンドポイントとそのメッセージに関連付けられたアクションに関する情報が提供されます。  
  
 サービス承認監査イベントは、サービス承認マネージャーによって決定される承認に適用されます。 このイベントでは、承認の成功または失敗に関する情報とクライアント ID、メッセージ送信先のエンドポイント、そのメッセージに関連付けられたアクション、受信メッセージから生成された承認コンテキストの ID、およびアクセス決定を行った承認マネージャーの種類に関する情報が提供されます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
## <a name="see-also"></a>参照  
 [監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [方法 : セキュリティ イベントを監査する](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
