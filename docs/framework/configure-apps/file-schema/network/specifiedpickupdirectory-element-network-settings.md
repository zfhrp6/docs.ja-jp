---
title: "&lt;specifiedPickupDirectory&gt;要素 (ネットワーク設定)"
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
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e68ce8cac4048ee2df89d0241cc50242e20391a2
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="b95db-102">&lt;specifiedPickupDirectory&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="b95db-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b95db-103">SMTP (Simple Mail Transport Protocol) サーバー用のローカル ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="b95db-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="b95db-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b95db-104">\<configuration></span></span>  
<span data-ttu-id="b95db-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b95db-105">\<system.net></span></span>  
<span data-ttu-id="b95db-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="b95db-106">\<mailSettings></span></span>  
<span data-ttu-id="b95db-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="b95db-107">\<smtp></span></span>  
<span data-ttu-id="b95db-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="b95db-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b95db-109">構文</span><span class="sxs-lookup"><span data-stu-id="b95db-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b95db-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b95db-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b95db-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b95db-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b95db-112">属性</span><span class="sxs-lookup"><span data-stu-id="b95db-112">Attributes</span></span>  
  
|<span data-ttu-id="b95db-113">属性</span><span class="sxs-lookup"><span data-stu-id="b95db-113">Attribute</span></span>|<span data-ttu-id="b95db-114">説明</span><span class="sxs-lookup"><span data-stu-id="b95db-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="b95db-115">アプリケーションが後で、SMTP サーバーで処理用の電子メールを保存するディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="b95db-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b95db-116">子要素</span><span class="sxs-lookup"><span data-stu-id="b95db-116">Child Elements</span></span>  
 <span data-ttu-id="b95db-117">なし。</span><span class="sxs-lookup"><span data-stu-id="b95db-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b95db-118">親要素</span><span class="sxs-lookup"><span data-stu-id="b95db-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b95db-119">要素</span><span class="sxs-lookup"><span data-stu-id="b95db-119">Element</span></span>|<span data-ttu-id="b95db-120">説明</span><span class="sxs-lookup"><span data-stu-id="b95db-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b95db-121">\<smtp > 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="b95db-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="b95db-122">簡易メール転送プロトコル (SMTP) 電子メールの送信オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="b95db-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b95db-123">コメント</span><span class="sxs-lookup"><span data-stu-id="b95db-123">Remarks</span></span>  
 <span data-ttu-id="b95db-124">`specifiedPickupDirectory`属性はアプリケーションが SMTP サーバーで処理する電子メール メッセージを保存するディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="b95db-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b95db-125">例</span><span class="sxs-lookup"><span data-stu-id="b95db-125">Example</span></span>  
 <span data-ttu-id="b95db-126">次の例では、メール ピックアップ ディレクトリとして c:\maildrop を指定します。</span><span class="sxs-lookup"><span data-stu-id="b95db-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b95db-127">参照</span><span class="sxs-lookup"><span data-stu-id="b95db-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="b95db-128">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="b95db-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
