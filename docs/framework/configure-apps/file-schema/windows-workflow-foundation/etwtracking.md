---
title: "&lt;etwTracking&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;etwTracking&gt;
<xref:System.Activities.Tracking.ETWTrackingParticipant> を使用した、サービスによる ETW 追跡の利用を可能にするサービス動作。  
  
## 構文  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <etwTracking profileName=”String” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|profileName|この動作に関連付けられた追跡プロファイルの名前を指定する文字列。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<serviceBehaviors\> の \<behavior\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|動作の要素を指定します。|  
  
## 解説  
 サービスの動作構成に追加すると、この構成要素により、ワークフロー サービスの追跡参加要素が構成されます。  
  
 追跡参加要素は、ワークフローから生成される追跡データを取得し、それを別のメディアに保存するために使用します。  同様に、追跡レコードの後処理はすべて、追跡参加要素内でも実行できます。  
  
## 使用例  
 次の構成例は、Web.config ファイルで構成されている標準の ETW 追跡参加要素を示します。  
  
 ETW 追跡参加要素が追跡レコードを ETW に書き込むために使用するプロバイダー ID は、**\<diagnostics\>** セクションで定義されます。  追跡参加要素には、その要素が定期受信した追跡レコードを指定するためのプロファイルが関連付けられています。  これは、**profileName** 要素の **\<add\>** 属性で定義されます。  これらが定義されると、追跡参加要素は **\<etwTracking\>** サービス動作に追加されます。  これにより、選択した追跡参加要素がワークフロー インスタンスの拡張機能に追加され、追跡レコードの受信が開始されます。  
  
```  
  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## 参照  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>   
 [ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [追跡参加要素](../../../../../docs/framework/windows-workflow-foundation//tracking-participants.md)