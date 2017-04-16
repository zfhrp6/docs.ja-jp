---
title: "&lt;diagnostics&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# &lt;diagnostics&gt;
`diagnostics` 要素は、ランタイムの検査と管理を行う管理者が使用できる設定を定義します。  
  
## 構文  
  
```  
  
<system.serviceModel>  
   <diagnostics etwProviderId=”String”  
       performanceCounters="Off/ServiceOnly/All/Default"         
       wmiProviderEnabled="Boolean" >  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
          maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
             <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|etwProviderId|イベントを ETW セッションに書き込むイベント追跡プロバイダーの識別子を指定する文字列。|  
|performanceCounters|アセンブリのパフォーマンス カウンターが有効であるかどうかを指定します。  有効な値は、次のとおりです。<br /><br /> -   Off: パフォーマンス カウンターは無効です。<br />-   ServiceOnly: このサービスに関連するパフォーマンス カウンターのみ有効です。<br />-   All: パフォーマンス カウンターを実行時に表示できます。<br />-   既定値 : 単一のパフォーマンス カウンター インスタンス \_WCF\_Admin が作成されます。  このインスタンスは、インフラストラクチャで使用される SQM データのコレクションを有効にするために使用されます。  このインスタンスのカウンター値は更新されず、0 のままになります。  WCF の構成が存在しない場合は、これが既定値になります。|  
|wmiProviderEnabled|アセンブリの WMI プロバイダーが有効であるかどうかを指定するブール値。  ユーザーが Windows Communication Foundation \(WCF\) の検査および制御機能に対する実行時アクセス権を取得するには、WMI プロバイダーが必要です。  既定値は、`false` です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<endToEndTracing\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|サービス アプリケーションの実行中にエンドツーエンドのトレースのさまざまな側面を有効または無効にするための構成要素。|  
|[\<messageLogging\>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|WCF メッセージ ログの設定について説明します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|serviceModel|すべての WCF 構成要素のルート要素です。|  
  
## 解説  
 `diagnostics` セクションは、アセンブリに配置されるすべてのサービスの診断設定を定義します。  アセンブリ内のサービスが 1 つでない限り、サービス レベル別に診断設定を定義することはできません。  属性は、セクションの要件に応じて設定されます。  
  
## 使用例  
  
```  
<diagnostics wmiProviderEnabled="false"  
       performanceCounters="all">  
       <messageLogging logEntireMessage="true"  
          logMalformedMessages="true"  
          logMessagesAtServiceLevel="true"  
          logMessagesAtTransportLevel="true"  
          maxMessagesToLog="42"  
          maxSizeOfMessageToLog="42">  
         <filters>  
         <clear />  
    </filters>  
       </messageLogging>  
</diagnostics>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>   
 <xref:System.ServiceModel.Diagnostics>