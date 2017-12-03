---
title: '&lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 88eb76a5657bd4a83bebb32ce30f73d32693be9b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="3841f-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="3841f-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="3841f-103">トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と WCF バインディング間の既定のプロトコル マッピングのセットを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="3841f-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="3841f-104">実行時に既定のエンドポイントを作成するときに、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] は構成されたマッピングを確認し、特定のベース アドレスに使用するバインディングを決定します。</span><span class="sxs-lookup"><span data-stu-id="3841f-104">When creating default endpoints at runtime, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="3841f-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3841f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3841f-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="3841f-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3841f-107">構文</span><span class="sxs-lookup"><span data-stu-id="3841f-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3841f-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3841f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3841f-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3841f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3841f-110">属性</span><span class="sxs-lookup"><span data-stu-id="3841f-110">Attributes</span></span>  
 <span data-ttu-id="3841f-111">なし。</span><span class="sxs-lookup"><span data-stu-id="3841f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3841f-112">子要素</span><span class="sxs-lookup"><span data-stu-id="3841f-112">Child Elements</span></span>  
  
|<span data-ttu-id="3841f-113">要素</span><span class="sxs-lookup"><span data-stu-id="3841f-113">Element</span></span>|<span data-ttu-id="3841f-114">説明</span><span class="sxs-lookup"><span data-stu-id="3841f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3841f-115">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="3841f-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="3841f-116">トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と WCF バインディング間の既定のプロトコル マッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3841f-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3841f-117">親要素</span><span class="sxs-lookup"><span data-stu-id="3841f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3841f-118">要素</span><span class="sxs-lookup"><span data-stu-id="3841f-118">Element</span></span>|<span data-ttu-id="3841f-119">説明</span><span class="sxs-lookup"><span data-stu-id="3841f-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3841f-120">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3841f-120">system.ServiceModel</span></span>|<span data-ttu-id="3841f-121">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="3841f-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3841f-122">例</span><span class="sxs-lookup"><span data-stu-id="3841f-122">Example</span></span>  
 <span data-ttu-id="3841f-123">次の構成例は、machine.config ファイル内の既定のプロトコル マッピングを示しています。</span><span class="sxs-lookup"><span data-stu-id="3841f-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="3841f-124">machine.config ファイルを変更することで、既定のマッピングをコンピューター レベルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="3841f-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="3841f-125">または、アプリケーションのスコープ内だけでオーバーライドする場合は、アプリケーション構成ファイルのこのセクションをオーバーライドし、各プロトコル スキームのマッピングを変更できます。</span><span class="sxs-lookup"><span data-stu-id="3841f-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3841f-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="3841f-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
