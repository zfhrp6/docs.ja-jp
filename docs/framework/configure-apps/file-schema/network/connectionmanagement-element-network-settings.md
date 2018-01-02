---
title: "&lt;connectionManagement&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 700d06d22c76762c80ea877006a8ac3789052b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="490ed-102">&lt;connectionManagement&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="490ed-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="490ed-103">ネットワーク ホストへの接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="490ed-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="490ed-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="490ed-104">\<configuration></span></span>  
<span data-ttu-id="490ed-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="490ed-105">\<system.net></span></span>  
<span data-ttu-id="490ed-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="490ed-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="490ed-107">構文</span><span class="sxs-lookup"><span data-stu-id="490ed-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="490ed-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="490ed-108">Attributes and Elements</span></span>  
 <span data-ttu-id="490ed-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="490ed-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="490ed-110">属性</span><span class="sxs-lookup"><span data-stu-id="490ed-110">Attributes</span></span>  
 <span data-ttu-id="490ed-111">なし。</span><span class="sxs-lookup"><span data-stu-id="490ed-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="490ed-112">子要素</span><span class="sxs-lookup"><span data-stu-id="490ed-112">Child Elements</span></span>  
  
|<span data-ttu-id="490ed-113">**要素**</span><span class="sxs-lookup"><span data-stu-id="490ed-113">**Element**</span></span>|<span data-ttu-id="490ed-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="490ed-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="490ed-115">add</span><span class="sxs-lookup"><span data-stu-id="490ed-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="490ed-116">IP アドレスまたは DNS 名を接続管理リストに追加します。</span><span class="sxs-lookup"><span data-stu-id="490ed-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="490ed-117">clear</span><span class="sxs-lookup"><span data-stu-id="490ed-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="490ed-118">接続の管理の一覧をクリアします。</span><span class="sxs-lookup"><span data-stu-id="490ed-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="490ed-119">remove</span><span class="sxs-lookup"><span data-stu-id="490ed-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="490ed-120">接続管理リストから IP アドレスまたは DNS 名を削除します。</span><span class="sxs-lookup"><span data-stu-id="490ed-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="490ed-121">親要素</span><span class="sxs-lookup"><span data-stu-id="490ed-121">Parent Elements</span></span>  
  
|<span data-ttu-id="490ed-122">**要素**</span><span class="sxs-lookup"><span data-stu-id="490ed-122">**Element**</span></span>|<span data-ttu-id="490ed-123">**説明**</span><span class="sxs-lookup"><span data-stu-id="490ed-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="490ed-124">system.net</span><span class="sxs-lookup"><span data-stu-id="490ed-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="490ed-125">.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="490ed-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="490ed-126">コメント</span><span class="sxs-lookup"><span data-stu-id="490ed-126">Remarks</span></span>  
 <span data-ttu-id="490ed-127">`connectionManagement`要素は、サーバーまたはサーバーのグループを接続の最大数を定義します。</span><span class="sxs-lookup"><span data-stu-id="490ed-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="490ed-128">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="490ed-128">Configuration Files</span></span>  
 <span data-ttu-id="490ed-129">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="490ed-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="490ed-130">例</span><span class="sxs-lookup"><span data-stu-id="490ed-130">Example</span></span>  
 <span data-ttu-id="490ed-131">次の例では、サーバー www.contoso.com への 4 つの接続とその他のすべてのサーバーに 2 つの接続を使用するアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="490ed-131">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="490ed-132">参照</span><span class="sxs-lookup"><span data-stu-id="490ed-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="490ed-133">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="490ed-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
