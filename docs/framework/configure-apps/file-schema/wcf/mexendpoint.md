---
title: '&lt;mexEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75886c08d3e358d4ed6d3d3048594ef28f06a7af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="b95dc-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="b95dc-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="b95dc-103">この構成要素は、固定 IMetadataExchange コントラクトが含まれた標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="b95dc-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="b95dc-104">IMetadataExchange はすべてのメタデータ交換エンドポイントでコントラクトとして指定されるため、独自のエンドポイントを定義せずにこの標準エンドポイントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b95dc-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="b95dc-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b95dc-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b95dc-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b95dc-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b95dc-107">構文</span><span class="sxs-lookup"><span data-stu-id="b95dc-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b95dc-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b95dc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b95dc-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b95dc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b95dc-110">属性</span><span class="sxs-lookup"><span data-stu-id="b95dc-110">Attributes</span></span>  
  
|<span data-ttu-id="b95dc-111">属性</span><span class="sxs-lookup"><span data-stu-id="b95dc-111">Attribute</span></span>|<span data-ttu-id="b95dc-112">説明</span><span class="sxs-lookup"><span data-stu-id="b95dc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b95dc-113">name</span><span class="sxs-lookup"><span data-stu-id="b95dc-113">name</span></span>|<span data-ttu-id="b95dc-114">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b95dc-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="b95dc-115">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="b95dc-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b95dc-116">子要素</span><span class="sxs-lookup"><span data-stu-id="b95dc-116">Child Elements</span></span>  
 <span data-ttu-id="b95dc-117">なし。</span><span class="sxs-lookup"><span data-stu-id="b95dc-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b95dc-118">親要素</span><span class="sxs-lookup"><span data-stu-id="b95dc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b95dc-119">要素</span><span class="sxs-lookup"><span data-stu-id="b95dc-119">Element</span></span>|<span data-ttu-id="b95dc-120">説明</span><span class="sxs-lookup"><span data-stu-id="b95dc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b95dc-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b95dc-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b95dc-122">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="b95dc-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
