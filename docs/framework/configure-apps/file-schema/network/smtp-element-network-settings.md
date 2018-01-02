---
title: "&lt;smtp&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 598fe3dc2a49187e923cd689f863d0a3327e735f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsmtpgt-element-network-settings"></a>&lt;smtp&gt;要素 (ネットワーク設定)
電子メール送信の配信形式、配信方法、および差出人アドレスを設定します。  
  
 \<configuration>  
\<system.net >  
\<mailSettings >  
\<smtp >  
  
## <a name="syntax"></a>構文  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`deliveryFormat`|送信する電子メールの配信形式を指定します。 指定できる値は SevenBit および International です。|  
|`deliveryMethod`|電子メールの配信方法を指定します。 指定できる値は、network、pickupDirectoryFromIis、および specifiedPickupDirectory です。|  
|`from`|送信する電子メールの差出人アドレスを指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|属性|説明|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|SMTP (Simple Mail Transport Protocol) サーバー用のローカル ディレクトリを設定します。|  
|`network`|外部 SMTP サーバー用のネットワーク オプションを設定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[\<mailSettings> 要素 (ネットワーク設定)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|電子メールの送信オプションを設定します。|  
  
## <a name="example"></a>例  
 次の例では、既定のネットワーク資格情報を使用して電子メールを送信する適切な SMTP パラメーターを指定します。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
