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
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="aea94-102">&lt;mailSettings&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="aea94-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="aea94-103">電子メールの送信オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="aea94-103">Configures mail sending options.</span></span>  

<span data-ttu-id="aea94-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aea94-104">\<configuration></span></span>  
<span data-ttu-id="aea94-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="aea94-105">\<system.net></span></span>  
<span data-ttu-id="aea94-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="aea94-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea94-107">構文</span><span class="sxs-lookup"><span data-stu-id="aea94-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aea94-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="aea94-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aea94-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="aea94-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aea94-110">属性</span><span class="sxs-lookup"><span data-stu-id="aea94-110">Attributes</span></span>  
 <span data-ttu-id="aea94-111">なし。</span><span class="sxs-lookup"><span data-stu-id="aea94-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aea94-112">子要素</span><span class="sxs-lookup"><span data-stu-id="aea94-112">Child Elements</span></span>  
  
|<span data-ttu-id="aea94-113">属性</span><span class="sxs-lookup"><span data-stu-id="aea94-113">Attribute</span></span>|<span data-ttu-id="aea94-114">説明</span><span class="sxs-lookup"><span data-stu-id="aea94-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="aea94-115">\<smtp > 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="aea94-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="aea94-116">簡易メール転送プロトコル オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="aea94-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aea94-117">親要素</span><span class="sxs-lookup"><span data-stu-id="aea94-117">Parent Elements</span></span>  
  
|<span data-ttu-id="aea94-118">**要素**</span><span class="sxs-lookup"><span data-stu-id="aea94-118">**Element**</span></span>|<span data-ttu-id="aea94-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="aea94-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="aea94-120">\<system.Net> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="aea94-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="aea94-121">.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="aea94-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aea94-122">例</span><span class="sxs-lookup"><span data-stu-id="aea94-122">Example</span></span>  
 <span data-ttu-id="aea94-123">次の例では、既定のネットワーク資格情報を使用して電子メールを送信する適切な SMTP パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="aea94-123">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aea94-124">参照</span><span class="sxs-lookup"><span data-stu-id="aea94-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="aea94-125">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="aea94-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
