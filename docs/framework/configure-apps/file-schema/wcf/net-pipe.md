---
title: "&lt;net.pipe&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# &lt;net.pipe&gt;
名前付きパイプ接続の有効期間を管理し、名前付きパイプを介して到着するアクティベーション要求を処理する名前付きパイプ アクティベーション サービスの構成設定を指定します。  
  
## 構文  
  
```  
  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## 型  
 `Type`  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`maxPendingAccepts`|整数は、共有サービスの待機エンドポイントで同時に受け入れる未処理のスレッドの最大数を示しています。  既定値は 2 です。|  
|`maxPendingConnections`|ディスパッチを待機できる最大接続数を指定する整数。  既定値は 100 です。|  
|`receiveTimeout`|フレーム データを読み取り、基礎となる接続から接続ディスパッチを実行するタイムアウトを指定する <xref:System.Timespan> です。  既定値は "00:00:10" です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<allowAccounts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] をホストするプロセスのユーザー アカウントを指定する `securityIdentifier` 属性が含まれており、共有サービスへの接続アクセス権が付与される構成要素のコレクションです。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<system.serviceModel.activation\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|リスナー プロセス SMSvcHost.exe の設定が含まれています。|  
  
## 参照  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>