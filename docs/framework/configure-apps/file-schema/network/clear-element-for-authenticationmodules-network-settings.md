---
title: "&lt;オフ&gt;authenticationModules (ネットワーク設定) の要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f056894148177e6b540fd45569140a996b6b888f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="eb26e-102">&lt;オフ&gt;authenticationModules (ネットワーク設定) の要素</span><span class="sxs-lookup"><span data-stu-id="eb26e-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="eb26e-103">アプリケーションからのすべての認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="eb26e-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="eb26e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="eb26e-104">\<configuration></span></span>  
<span data-ttu-id="eb26e-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="eb26e-105">\<system.net></span></span>  
<span data-ttu-id="eb26e-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="eb26e-106">\<authenticationModules></span></span>  
<span data-ttu-id="eb26e-107">\<オフ ></span><span class="sxs-lookup"><span data-stu-id="eb26e-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb26e-108">構文</span><span class="sxs-lookup"><span data-stu-id="eb26e-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb26e-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="eb26e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eb26e-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb26e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb26e-111">属性</span><span class="sxs-lookup"><span data-stu-id="eb26e-111">Attributes</span></span>  
 <span data-ttu-id="eb26e-112">なし。</span><span class="sxs-lookup"><span data-stu-id="eb26e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eb26e-113">子要素</span><span class="sxs-lookup"><span data-stu-id="eb26e-113">Child Elements</span></span>  
 <span data-ttu-id="eb26e-114">なし。</span><span class="sxs-lookup"><span data-stu-id="eb26e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb26e-115">親要素</span><span class="sxs-lookup"><span data-stu-id="eb26e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="eb26e-116">**要素**</span><span class="sxs-lookup"><span data-stu-id="eb26e-116">**Element**</span></span>|<span data-ttu-id="eb26e-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="eb26e-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eb26e-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="eb26e-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="eb26e-119">ネットワーク要求を認証するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb26e-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb26e-120">コメント</span><span class="sxs-lookup"><span data-stu-id="eb26e-120">Remarks</span></span>  
 <span data-ttu-id="eb26e-121">`clear`要素または構成階層の上位レベルにある構成ファイルで既に定義されているすべての認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="eb26e-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="eb26e-122">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="eb26e-122">Configuration Files</span></span>  
 <span data-ttu-id="eb26e-123">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb26e-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb26e-124">例</span><span class="sxs-lookup"><span data-stu-id="eb26e-124">Example</span></span>  
 <span data-ttu-id="eb26e-125">次の例では、すべての構成済みの認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="eb26e-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb26e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb26e-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="eb26e-127">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="eb26e-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
