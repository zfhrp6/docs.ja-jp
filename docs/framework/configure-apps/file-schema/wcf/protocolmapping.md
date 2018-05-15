---
title: '&lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 4afdaaa62c1ac3241eb7382d0995bed51bde73e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="298e6-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="298e6-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="298e6-103">トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と WCF バインディング間の既定のプロトコル マッピングのセットを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="298e6-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="298e6-104">を実行時に既定のエンドポイントを作成する場合、Windows Communication Foundation (WCF) は構成されたマッピングは確認し、ベース アドレスの特定に使用するバインディングを決定します。</span><span class="sxs-lookup"><span data-stu-id="298e6-104">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="298e6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="298e6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="298e6-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="298e6-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="298e6-107">構文</span><span class="sxs-lookup"><span data-stu-id="298e6-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="298e6-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="298e6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="298e6-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="298e6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="298e6-110">属性</span><span class="sxs-lookup"><span data-stu-id="298e6-110">Attributes</span></span>  
 <span data-ttu-id="298e6-111">なし。</span><span class="sxs-lookup"><span data-stu-id="298e6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="298e6-112">子要素</span><span class="sxs-lookup"><span data-stu-id="298e6-112">Child Elements</span></span>  
  
|<span data-ttu-id="298e6-113">要素</span><span class="sxs-lookup"><span data-stu-id="298e6-113">Element</span></span>|<span data-ttu-id="298e6-114">説明</span><span class="sxs-lookup"><span data-stu-id="298e6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="298e6-115">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="298e6-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="298e6-116">トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と WCF バインディング間の既定のプロトコル マッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="298e6-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="298e6-117">親要素</span><span class="sxs-lookup"><span data-stu-id="298e6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="298e6-118">要素</span><span class="sxs-lookup"><span data-stu-id="298e6-118">Element</span></span>|<span data-ttu-id="298e6-119">説明</span><span class="sxs-lookup"><span data-stu-id="298e6-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="298e6-120">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="298e6-120">system.ServiceModel</span></span>|<span data-ttu-id="298e6-121">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="298e6-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="298e6-122">例</span><span class="sxs-lookup"><span data-stu-id="298e6-122">Example</span></span>  
 <span data-ttu-id="298e6-123">次の構成例は、machine.config ファイル内の既定のプロトコル マッピングを示しています。</span><span class="sxs-lookup"><span data-stu-id="298e6-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="298e6-124">machine.config ファイルを変更することで、既定のマッピングをコンピューター レベルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="298e6-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="298e6-125">または、アプリケーションのスコープ内だけでオーバーライドする場合は、アプリケーション構成ファイルのこのセクションをオーバーライドし、各プロトコル スキームのマッピングを変更できます。</span><span class="sxs-lookup"><span data-stu-id="298e6-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="298e6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="298e6-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
