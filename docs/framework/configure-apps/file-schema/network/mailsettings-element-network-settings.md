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
ms.openlocfilehash: a42b10574a1f44d310f86fe3fa99490f2f1981c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="70369-102">&lt;mailSettings&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="70369-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="70369-103">電子メールの送信オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="70369-103">Configures mail sending options.</span></span>  

<span data-ttu-id="70369-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="70369-104">\<configuration></span></span>  
<span data-ttu-id="70369-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="70369-105">\<system.net></span></span>  
<span data-ttu-id="70369-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="70369-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70369-107">構文</span><span class="sxs-lookup"><span data-stu-id="70369-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70369-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="70369-108">Attributes and Elements</span></span>  
 <span data-ttu-id="70369-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="70369-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70369-110">属性</span><span class="sxs-lookup"><span data-stu-id="70369-110">Attributes</span></span>  
 <span data-ttu-id="70369-111">なし。</span><span class="sxs-lookup"><span data-stu-id="70369-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70369-112">子要素</span><span class="sxs-lookup"><span data-stu-id="70369-112">Child Elements</span></span>  
  
|<span data-ttu-id="70369-113">属性</span><span class="sxs-lookup"><span data-stu-id="70369-113">Attribute</span></span>|<span data-ttu-id="70369-114">説明</span><span class="sxs-lookup"><span data-stu-id="70369-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="70369-115">\<smtp > 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="70369-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="70369-116">簡易メール転送プロトコル オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="70369-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70369-117">親要素</span><span class="sxs-lookup"><span data-stu-id="70369-117">Parent Elements</span></span>  
  
|<span data-ttu-id="70369-118">**要素**</span><span class="sxs-lookup"><span data-stu-id="70369-118">**Element**</span></span>|<span data-ttu-id="70369-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="70369-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="70369-120">\<system.Net> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="70369-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="70369-121">.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="70369-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="70369-122">例</span><span class="sxs-lookup"><span data-stu-id="70369-122">Example</span></span>  
 <span data-ttu-id="70369-123">次の例では、既定のネットワーク資格情報を使用して電子メールを送信する適切な SMTP パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="70369-123">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70369-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="70369-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="70369-125">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="70369-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
