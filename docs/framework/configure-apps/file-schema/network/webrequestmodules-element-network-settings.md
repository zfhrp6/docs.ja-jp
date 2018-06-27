---
title: '&lt;webRequestModules&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7454099d8af0f2d656296be55677c648cc0c36c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742693"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a><span data-ttu-id="040ea-102">&lt;webRequestModules&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="040ea-102">&lt;webRequestModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="040ea-103">使用してネットワークのホストから情報を要求するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="040ea-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="040ea-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="040ea-104">\<configuration></span></span>  
<span data-ttu-id="040ea-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="040ea-105">\<system.net></span></span>  
<span data-ttu-id="040ea-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="040ea-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="040ea-107">構文</span><span class="sxs-lookup"><span data-stu-id="040ea-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="040ea-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="040ea-108">Attributes and Elements</span></span>  
 <span data-ttu-id="040ea-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="040ea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="040ea-110">属性</span><span class="sxs-lookup"><span data-stu-id="040ea-110">Attributes</span></span>  
 <span data-ttu-id="040ea-111">なし。</span><span class="sxs-lookup"><span data-stu-id="040ea-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="040ea-112">子要素</span><span class="sxs-lookup"><span data-stu-id="040ea-112">Child Elements</span></span>  
  
|<span data-ttu-id="040ea-113">**要素**</span><span class="sxs-lookup"><span data-stu-id="040ea-113">**Element**</span></span>|<span data-ttu-id="040ea-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="040ea-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="040ea-115">add</span><span class="sxs-lookup"><span data-stu-id="040ea-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="040ea-116">アプリケーションにカスタム Web 要求のモジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="040ea-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="040ea-117">clear</span><span class="sxs-lookup"><span data-stu-id="040ea-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="040ea-118">登録されているすべての Web 要求のモジュールをアプリケーションから削除します。</span><span class="sxs-lookup"><span data-stu-id="040ea-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="040ea-119">remove</span><span class="sxs-lookup"><span data-stu-id="040ea-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="040ea-120">アプリケーションからカスタム Web 要求のモジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="040ea-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="040ea-121">親要素</span><span class="sxs-lookup"><span data-stu-id="040ea-121">Parent Elements</span></span>  
  
|<span data-ttu-id="040ea-122">**要素**</span><span class="sxs-lookup"><span data-stu-id="040ea-122">**Element**</span></span>|<span data-ttu-id="040ea-123">**説明**</span><span class="sxs-lookup"><span data-stu-id="040ea-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="040ea-124">system.net</span><span class="sxs-lookup"><span data-stu-id="040ea-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="040ea-125">.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="040ea-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="040ea-126">コメント</span><span class="sxs-lookup"><span data-stu-id="040ea-126">Remarks</span></span>  
 <span data-ttu-id="040ea-127">`webRequestModules`要素の子孫を登録する、<xref:System.Net.WebRequest>ネットワーク ホストへの情報要求を処理するクラス。</span><span class="sxs-lookup"><span data-stu-id="040ea-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="040ea-128">Web 要求のモジュールを実装する必要があります、<xref:System.Net.IWebRequestCreate>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="040ea-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="040ea-129">.NET Framework には、http://、 https://、 および file://  で始まる Uri の Web 要求のモジュールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="040ea-129">The .NET Framework includes Web request modules for URIs that begin with http://, https://, and file://.</span></span> <span data-ttu-id="040ea-130">既定のモジュールは、構成ファイルでカスタム モジュールを登録することによってのみ上書きできます。</span><span class="sxs-lookup"><span data-stu-id="040ea-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="040ea-131">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="040ea-131">Configuration Files</span></span>  
 <span data-ttu-id="040ea-132">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="040ea-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="040ea-133">例</span><span class="sxs-lookup"><span data-stu-id="040ea-133">Example</span></span>  
 <span data-ttu-id="040ea-134">次の例では、既定の HTTP モジュールを登録します。</span><span class="sxs-lookup"><span data-stu-id="040ea-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="040ea-135">指定したモジュールの正しい値を持つバージョンおよび PublicKeyToken の値を置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="040ea-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="040ea-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="040ea-136">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [<span data-ttu-id="040ea-137">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="040ea-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
