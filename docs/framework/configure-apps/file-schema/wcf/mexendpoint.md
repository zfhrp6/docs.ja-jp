---
title: '&lt;mexEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: aceff3e373d9a5f7e57c28d85870af19ae8ef3e1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="1040e-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="1040e-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="1040e-103">この構成要素は、固定 IMetadataExchange コントラクトが含まれた標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="1040e-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="1040e-104">IMetadataExchange はすべてのメタデータ交換エンドポイントでコントラクトとして指定されるため、独自のエンドポイントを定義せずにこの標準エンドポイントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1040e-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="1040e-105">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1040e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1040e-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1040e-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1040e-107">構文</span><span class="sxs-lookup"><span data-stu-id="1040e-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1040e-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1040e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1040e-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1040e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1040e-110">属性</span><span class="sxs-lookup"><span data-stu-id="1040e-110">Attributes</span></span>  
  
|<span data-ttu-id="1040e-111">属性</span><span class="sxs-lookup"><span data-stu-id="1040e-111">Attribute</span></span>|<span data-ttu-id="1040e-112">説明</span><span class="sxs-lookup"><span data-stu-id="1040e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1040e-113">name</span><span class="sxs-lookup"><span data-stu-id="1040e-113">name</span></span>|<span data-ttu-id="1040e-114">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="1040e-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1040e-115">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="1040e-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1040e-116">子要素</span><span class="sxs-lookup"><span data-stu-id="1040e-116">Child Elements</span></span>  
 <span data-ttu-id="1040e-117">なし。</span><span class="sxs-lookup"><span data-stu-id="1040e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1040e-118">親要素</span><span class="sxs-lookup"><span data-stu-id="1040e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1040e-119">要素</span><span class="sxs-lookup"><span data-stu-id="1040e-119">Element</span></span>|<span data-ttu-id="1040e-120">説明</span><span class="sxs-lookup"><span data-stu-id="1040e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1040e-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1040e-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1040e-122">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="1040e-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
