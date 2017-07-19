---
title: "&lt;mailSettings&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<mailSettings> 要素"
  - "mailSettings 要素"
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;mailSettings&gt; 要素 (ネットワーク設定)
電子メールの送信オプションを設定します。  
  
## 構文  
  
```  
  
      <mailSettings  
  <smtp> … </smtp>  
/mailsettings>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|Attribute|説明|  
|---------------|--------|  
|[\<smtp\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|SMTP \(Simple Mail Transport Protocol\) オプションを設定します。|  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[\<system.Net\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## 使用例  
 既定のネットワーク資格情報を使用して電子メールを送信するために、適切な SMTP パラメーターを指定するコード例を次に示します。  
  
```  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.Mail.SmtpClient>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)