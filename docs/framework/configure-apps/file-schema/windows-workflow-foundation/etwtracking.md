---
title: '&lt;etwTracking&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 6defccdd6a81a1c00a4b65fa9214c86e6cccbea2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756746"
---
# <a name="ltetwtrackinggt"></a>&lt;etwTracking&gt;
により、サービスを使用して ETW の追跡を使用するサービスの動作、<xref:System.Activities.Tracking.EtwTrackingParticipant>です。  
  
\<system.ServiceModel >  
\<ビヘイビアー >  
\<serviceBehaviors>  
\<behavior>  
\<etwTracking >  
  
## <a name="syntax"></a>構文  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|profileName|この動作に関連付けられた追跡プロファイルの名前を指定する文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<動作 > の\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|動作の要素を指定します。|  
  
## <a name="remarks"></a>コメント  
 サービスの動作構成に追加すると、この構成要素により、ワークフロー サービスの追跡参加要素が構成されます。  
  
 追跡参加要素は、ワークフローから生成される追跡データを取得し、それを別のメディアに保存するために使用します。 同様に、追跡レコードの後処理はすべて、追跡参加要素内でも実行できます。  
  
## <a name="example"></a>例  
 次の構成例は、Web.config ファイルで構成されている標準の ETW 追跡参加要素を示します。  
  
 追跡レコードを ETW に書き込むため、ETW 追跡参加要素を使用するプロバイダー Id が定義されている、 **\<診断 >** セクションです。 追跡参加要素には、その要素が定期受信した追跡レコードを指定するためのプロファイルが関連付けられています。 これは、 **profileName**の属性、 **\<追加 >** 要素。 これらを定義すると、追跡参加要素に追加されます、  **\<etwTracking >** サービス動作。 これにより、選択した追跡参加要素がワークフロー インスタンスの拡張機能に追加され、追跡レコードの受信が開始されます。  
  
```xml  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [ワークフローの追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [追跡参加要素](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
