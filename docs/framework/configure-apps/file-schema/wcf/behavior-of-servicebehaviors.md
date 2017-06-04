---
title: "&lt;serviceBehaviors&gt; の &lt;behavior&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;serviceBehaviors&gt; の &lt;behavior&gt;
`behavior` 要素には、サービスの動作設定のコレクションが含まれます。  各動作には、それぞれの `name` によってインデックスが付けられます。  サービスは、[\<endpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) 要素の `behaviorConfiguration` 属性を使用して、この名前で各動作にリンクできます。  これにより、設定を再定義することなく、エンドポイント間で共通の動作構成を共有できます。  [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。  既定の構成、および名前のないバインディングと動作の詳細については、「[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)」および「[WCF サービスの簡略化された構成](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
> [!NOTE]
>  Windows Workflow アクティビティに固有の動作要素 \([\<sendMessageChannelCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md) 要素など\) については、「[\<serviceBehaviors\> の \<behavior\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)」のページを参照してください。  
  
## 構文  
  
```  
  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
       <behavior name="String" />  
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|name|動作の構成名を含む一意の文字列。  この値は、要素の識別文字列として機能するため、一意のユーザー定義の文字列である必要があります。  [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。  既定の構成、および名前のないバインディングと動作の詳細については、「[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)」および「[WCF サービスの簡略化された構成](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)|DataContractSerializer 用の構成データが含まれています。|  
|[\<persistenceProvider\>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistenceprovider.md)|使用する永続化プロバイダーの実装の型と、永続化操作に使用するタイムアウトを指定します。|  
|[\<routing\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|ルーティング構成の動的な変更を可能にするルーティング サービスへの実行時アクセスを提供します。|  
|[\<serviceAuthenticationManager\>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthenticationmanager.md)|サービス レベルで転送、メッセージ、または送信元の有効性を確立するワークフロー構成要素を提供します。|  
|[\<serviceAuthorization\>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)|サービス操作へのアクセスを承認する設定を指定します。|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。|  
|[\<serviceDebug\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)|[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスのデバッグおよびヘルプ情報機能を指定します。|  
|[\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)|サービス エンドポイントの探索可能性を指定します。|  
|[\<serviceMetadata\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)|サービス メタデータと関連情報の公開を指定します。|  
|[\<serviceSecurityAudit\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)|サービス操作中にセキュリティ イベントの監査を有効にする設定を指定します。|  
|[\<serviceThrottling\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスの調整機構を指定します。|  
|[\<serviceTimeouts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicetimeouts.md)|サービスのタイムアウトを指定します。|  
|[\<workflowRuntime\>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|ワークフロー ベースの [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスをホストするための WorkflowRuntime のインスタンスの設定を指定します。|  
|[\<useRequestHeadersForMetadataAddress\>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|メタデータのアドレス情報を要求メッセージ ヘッダーから取得できるようにします。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|サービス動作要素のコレクション。|