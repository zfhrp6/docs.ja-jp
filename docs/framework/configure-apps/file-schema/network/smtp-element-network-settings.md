---
title: "&lt;smtp&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f5b2a3b7eec17fbdd12181c29f610d2b2ad32bd4
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="2f3ec-102">&lt;smtp&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="2f3ec-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2f3ec-103">配信形式、配信方法を構成し、電子メールを送信するためのアドレスからです。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="2f3ec-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2f3ec-104">\<configuration></span></span>  
<span data-ttu-id="2f3ec-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2f3ec-105">\<system.net></span></span>  
<span data-ttu-id="2f3ec-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="2f3ec-106">\<mailSettings></span></span>  
<span data-ttu-id="2f3ec-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="2f3ec-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f3ec-108">構文</span><span class="sxs-lookup"><span data-stu-id="2f3ec-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f3ec-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2f3ec-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2f3ec-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f3ec-111">属性</span><span class="sxs-lookup"><span data-stu-id="2f3ec-111">Attributes</span></span>  
  
|<span data-ttu-id="2f3ec-112">属性</span><span class="sxs-lookup"><span data-stu-id="2f3ec-112">Attribute</span></span>|<span data-ttu-id="2f3ec-113">説明</span><span class="sxs-lookup"><span data-stu-id="2f3ec-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="2f3ec-114">発信メールの配信形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="2f3ec-115">指定できる値は SevenBit および International です。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="2f3ec-116">電子メールの配信方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="2f3ec-117">指定できる値は、network、pickupDirectoryFromIis、および specifiedPickupDirectory です。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="2f3ec-118">指定、出力方向の電子メールの差出人アドレスです。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f3ec-119">子要素</span><span class="sxs-lookup"><span data-stu-id="2f3ec-119">Child Elements</span></span>  
  
|<span data-ttu-id="2f3ec-120">属性</span><span class="sxs-lookup"><span data-stu-id="2f3ec-120">Attribute</span></span>|<span data-ttu-id="2f3ec-121">説明</span><span class="sxs-lookup"><span data-stu-id="2f3ec-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="2f3ec-122">SMTP (Simple Mail Transport Protocol) サーバー用のローカル ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="2f3ec-123">外部 SMTP サーバー用のネットワーク オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f3ec-124">親要素</span><span class="sxs-lookup"><span data-stu-id="2f3ec-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2f3ec-125">**要素**</span><span class="sxs-lookup"><span data-stu-id="2f3ec-125">**Element**</span></span>|<span data-ttu-id="2f3ec-126">**説明**</span><span class="sxs-lookup"><span data-stu-id="2f3ec-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2f3ec-127">\<mailSettings> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="2f3ec-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="2f3ec-128">電子メールの送信オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2f3ec-129">例</span><span class="sxs-lookup"><span data-stu-id="2f3ec-129">Example</span></span>  
 <span data-ttu-id="2f3ec-130">次の例では、既定のネットワーク資格情報を使用して電子メールを送信する適切な SMTP パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f3ec-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f3ec-131">参照</span><span class="sxs-lookup"><span data-stu-id="2f3ec-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="2f3ec-132">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="2f3ec-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
