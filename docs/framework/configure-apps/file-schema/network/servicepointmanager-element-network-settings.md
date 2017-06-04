---
title: "&lt;servicePointManager&gt; 要素 (ネットワーク設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<servicePointManager> 要素"
  - "servicePointManager 要素"
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 16
---
# &lt;servicePointManager&gt; 要素 (ネットワーク設定)
ネットワーク リソースへの接続を設定します。  
  
## 構文  
  
```  
  
      <servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**Attribute**|**説明**|  
|-------------------|------------|  
|`checkCertificateName`|証明書を使用する前に、システムで証明書の名前がサーバー ホスト名に一致することを確認する必要があるかどうかを指定します。  既定値は `true` です。|  
|`checkCertificateRevocationList`|証明書を使用する前に、システムで証明書が取り消されていることをチェックする必要があるかどうかを指定します。  既定値は `false` です。|  
|`dnsRefreshTimeout`|ドメイン ネーム サービス \(DNS\) 解決が DNS ラウンド ロビン オプションと共にキャッシュされる期間をミリ秒で指定します。  既定値は 120,000 ミリ秒 \(2 分\) です。|  
|`enableDnsRoundRobin`|複数のインターネット プロトコル \(IP: Internet Protocol\) アドレスを持つホスト名の DNS 解決がすべてのアドレスを返すか、最初のアドレスだけを返すかを指定します。  既定値は `false` です。|  
|`encryptionPolicy`|<xref:System.Net.ServicePointManager> インスタンスの SSL\/TLS セッションに適用する暗号化ポリシーを指定します。  有効値は、<xref:System.Net.Security.EncryptionPolicy> 列挙型の値と同じです。  暗号化ポリシーが `NoEncryption` に設定されている場合は、<xref:System.Security.Authentication.CipherAlgorithmType> を使用する必要があります。  既定値は `RequireEncryption` です。|  
|`expect100Continue`|POST メソッドがサーバーから `100-continue` 応答を受け取ることを想定する必要があるかどうかを指定します。  既定値は `true` です。|  
|`useNagleAlgorithm`|サービス ポイント マネージャーによって制御される接続が、Nagle アルゴリズムを使用するかどうかを指定します。  既定値は `true` です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## 解説  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 参照  
 <xref:System.Net.ServicePointManager>   
 <xref:System.Net.Security.EncryptionPolicy>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)