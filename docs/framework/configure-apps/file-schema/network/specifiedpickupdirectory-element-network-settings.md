---
title: "&lt;specifiedPickupDirectory&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ffe34e6a811dd644b149a0fda12f1d1cd338c761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="a5c72-102">&lt;specifiedPickupDirectory&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="a5c72-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="a5c72-103">SMTP (Simple Mail Transport Protocol) サーバー用のローカル ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="a5c72-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="a5c72-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a5c72-104">\<configuration></span></span>  
<span data-ttu-id="a5c72-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="a5c72-105">\<system.net></span></span>  
<span data-ttu-id="a5c72-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="a5c72-106">\<mailSettings></span></span>  
<span data-ttu-id="a5c72-107">\<smtp ></span><span class="sxs-lookup"><span data-stu-id="a5c72-107">\<smtp></span></span>  
<span data-ttu-id="a5c72-108">\<specifiedPickupDirectory ></span><span class="sxs-lookup"><span data-stu-id="a5c72-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c72-109">構文</span><span class="sxs-lookup"><span data-stu-id="a5c72-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5c72-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a5c72-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a5c72-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5c72-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5c72-112">属性</span><span class="sxs-lookup"><span data-stu-id="a5c72-112">Attributes</span></span>  
  
|<span data-ttu-id="a5c72-113">属性</span><span class="sxs-lookup"><span data-stu-id="a5c72-113">Attribute</span></span>|<span data-ttu-id="a5c72-114">説明</span><span class="sxs-lookup"><span data-stu-id="a5c72-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="a5c72-115">アプリケーションが後で、SMTP サーバーによって処理するための電子メールを保存するディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="a5c72-115">The directory where applications save e-mail for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5c72-116">子要素</span><span class="sxs-lookup"><span data-stu-id="a5c72-116">Child Elements</span></span>  
 <span data-ttu-id="a5c72-117">なし。</span><span class="sxs-lookup"><span data-stu-id="a5c72-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5c72-118">親要素</span><span class="sxs-lookup"><span data-stu-id="a5c72-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a5c72-119">要素</span><span class="sxs-lookup"><span data-stu-id="a5c72-119">Element</span></span>|<span data-ttu-id="a5c72-120">説明</span><span class="sxs-lookup"><span data-stu-id="a5c72-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5c72-121">\<smtp > 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="a5c72-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="a5c72-122">簡易メール転送プロトコル (SMTP) 電子メールの送信オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="a5c72-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5c72-123">コメント</span><span class="sxs-lookup"><span data-stu-id="a5c72-123">Remarks</span></span>  
 <span data-ttu-id="a5c72-124">`specifiedPickupDirectory`属性はアプリケーションが SMTP サーバーで処理する電子メール メッセージを保存するディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="a5c72-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5c72-125">例</span><span class="sxs-lookup"><span data-stu-id="a5c72-125">Example</span></span>  
 <span data-ttu-id="a5c72-126">次の例では、メール ピックアップ ディレクトリとして c:\maildrop を指定します。</span><span class="sxs-lookup"><span data-stu-id="a5c72-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5c72-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5c72-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="a5c72-128">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="a5c72-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
