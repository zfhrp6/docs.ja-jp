---
title: "&lt;net.tcp&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# &lt;net.tcp&gt;
複数のプロセスが同じ TCP ポートを共有できる NET.TCP ポート共有サービスの構成設定を指定します。  
  
## 構文  
  
```  
  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
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
|`listenBacklog`|共有接続から受け入れられたが、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスにはまだディスパッチされていない未処理の接続の最大数を指定する整数です。  既定値は 10 です。|  
|`maxPendingAccepts`|整数は、共有サービスの待機エンドポイントで同時に受け入れる未処理のスレッドの最大数を示しています。  既定値は 2 です。|  
|`MaxPendingConnections`|アプリケーションによる受け入れをリスナーで待機できる最大接続数。  このクォータ値を超過すると、新規の受信接続は受け入れられるのを待機せずに切断されます。  メッセージ セキュリティのような接続機能では、クライアントは複数の接続を開くことがあります。  このクォータ値を設定する場合、サービス管理者はこのような追加の接続も考慮する必要があります。  既定値は 10 です。|  
|`receiveTimeout`|フレーム データを読み取り、基礎となる接続から接続ディスパッチを実行するタイムアウトを指定する <xref:System.Timespan> です。  既定値は "00:00:10" です。|  
|`teredoEnabled`|ポート共有サービスが Microsoft Teredo サービスを使用して、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスの代わりに TCP ポートをリッスンするかどうかを示すブール値。  既定値は、`false` です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<allowAccounts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] をホストするプロセスのユーザー アカウントを指定する `securityIdentifier` 属性が含まれており、共有サービスへの接続アクセス権が付与される構成要素のコレクションです。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<system.serviceModel.activation\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|リスナー プロセス SMSvcHost.exe の設定が含まれています。|  
  
## 解説  
 ポート共有の詳細については、「[Net.TCP Port Sharing](http://msdn.microsoft.com/ja-jp/f13692ee-a179-4439-ae72-50db9534eded)」を参照してください。  ポート共有サービスを構成する方法については、「[Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/ja-jp/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)」を参照してください。  
  
## 参照  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>   
 [Net.TCP Port Sharing](http://msdn.microsoft.com/ja-jp/f13692ee-a179-4439-ae72-50db9534eded)   
 [Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/ja-jp/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)