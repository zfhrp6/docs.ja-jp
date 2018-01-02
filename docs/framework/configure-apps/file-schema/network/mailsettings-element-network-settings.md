---
title: "&lt;mailSettings&gt;要素 (ネットワーク設定)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5ae9ecdfa9cccb7c70c153153b921151aad50e7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltmailsettingsgt-element-network-settings"></a>&lt;mailSettings&gt;要素 (ネットワーク設定)
電子メールの送信オプションを設定します。  

\<configuration>  
\<system.net >  
\<mailSettings >  
  
## <a name="syntax"></a>構文  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|属性|説明|  
|---------------|-----------------|  
|[\<smtp > 要素 (ネットワーク設定)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|簡易メール転送プロトコル オプションを構成します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[\<system.Net> 要素 (ネットワーク設定)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## <a name="example"></a>例  
 次の例では、既定のネットワーク資格情報を使用して電子メールを送信する適切な SMTP パラメーターを指定します。  
  
```xml  
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
  
## <a name="see-also"></a>参照  
 <xref:System.Net.Mail.SmtpClient>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
