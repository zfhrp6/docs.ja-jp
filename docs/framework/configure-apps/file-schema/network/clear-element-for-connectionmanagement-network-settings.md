---
title: '&lt;オフ&gt;connectionManagement (ネットワーク設定) の要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5bcd17cfe1f3bd7531453b62552a4907df5b96bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="36490-102">&lt;オフ&gt;connectionManagement (ネットワーク設定) の要素</span><span class="sxs-lookup"><span data-stu-id="36490-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="36490-103">接続の管理の一覧をクリアします。</span><span class="sxs-lookup"><span data-stu-id="36490-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="36490-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="36490-104">\<configuration></span></span>  
<span data-ttu-id="36490-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="36490-105">\<system.net></span></span>  
<span data-ttu-id="36490-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="36490-106">\<connectionManagement></span></span>  
<span data-ttu-id="36490-107">\<オフ ></span><span class="sxs-lookup"><span data-stu-id="36490-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36490-108">構文</span><span class="sxs-lookup"><span data-stu-id="36490-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36490-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="36490-109">Attributes and Elements</span></span>  
 <span data-ttu-id="36490-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="36490-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36490-111">属性</span><span class="sxs-lookup"><span data-stu-id="36490-111">Attributes</span></span>  
 <span data-ttu-id="36490-112">なし。</span><span class="sxs-lookup"><span data-stu-id="36490-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36490-113">子要素</span><span class="sxs-lookup"><span data-stu-id="36490-113">Child Elements</span></span>  
 <span data-ttu-id="36490-114">なし。</span><span class="sxs-lookup"><span data-stu-id="36490-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36490-115">親要素</span><span class="sxs-lookup"><span data-stu-id="36490-115">Parent Elements</span></span>  
  
|<span data-ttu-id="36490-116">**要素**</span><span class="sxs-lookup"><span data-stu-id="36490-116">**Element**</span></span>|<span data-ttu-id="36490-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="36490-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="36490-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="36490-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="36490-119">ネットワーク ホストへの接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="36490-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36490-120">コメント</span><span class="sxs-lookup"><span data-stu-id="36490-120">Remarks</span></span>  
 <span data-ttu-id="36490-121">`clear`要素の接続管理リストからすべてのエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="36490-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="36490-122">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="36490-122">Configuration Files</span></span>  
 <span data-ttu-id="36490-123">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="36490-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36490-124">例</span><span class="sxs-lookup"><span data-stu-id="36490-124">Example</span></span>  
 <span data-ttu-id="36490-125">次の例では、接続管理リストから削除し、サーバー www.contoso.com とその他のすべてのネットワーク ホストの接続管理エントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="36490-125">The following example clears the connection management list and then adds new connection management entries for the server www.contoso.com and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36490-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="36490-126">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="36490-127">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="36490-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
