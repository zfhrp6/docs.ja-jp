---
title: '&lt;dataContractSerializer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d38e3786c595c3fe6cc9ea54b68784c927901731
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="50519-102">&lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="50519-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="50519-103"><xref:System.Runtime.Serialization.DataContractSerializer> 用の設定データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="50519-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="50519-104">この要素は、2 つの異なる階層で使用されます。</span><span class="sxs-lookup"><span data-stu-id="50519-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="50519-105">1 つは以下の「スキーマの階層」に示したもので、もう 1 つは「解説」に記載しています。</span><span class="sxs-lookup"><span data-stu-id="50519-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="50519-106">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="50519-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="50519-107">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="50519-107">\<behaviors></span></span>  
<span data-ttu-id="50519-108">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="50519-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="50519-109">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="50519-109">\<behavior></span></span>  
<span data-ttu-id="50519-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="50519-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50519-111">構文</span><span class="sxs-lookup"><span data-stu-id="50519-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
   maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50519-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="50519-112">Attributes and Elements</span></span>  
 <span data-ttu-id="50519-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="50519-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50519-114">属性</span><span class="sxs-lookup"><span data-stu-id="50519-114">Attributes</span></span>  
  
|<span data-ttu-id="50519-115">要素</span><span class="sxs-lookup"><span data-stu-id="50519-115">Element</span></span>|<span data-ttu-id="50519-116">説明</span><span class="sxs-lookup"><span data-stu-id="50519-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50519-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="50519-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="50519-118">エンドポイントがシリアル化または逆シリアル化されているときに、そのエンドポイントにより提供されるデータを無視するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="50519-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="50519-119">この属性は、`<dataContractSerializer>` 要素の下の `<behavior>` でのみ設定可能です。</span><span class="sxs-lookup"><span data-stu-id="50519-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="50519-120">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="50519-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="50519-121">シリアル化または逆シリアル化する項目の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="50519-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="50519-122">この属性は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="50519-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50519-123">子要素</span><span class="sxs-lookup"><span data-stu-id="50519-123">Child Elements</span></span>  
 <span data-ttu-id="50519-124">なし。</span><span class="sxs-lookup"><span data-stu-id="50519-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50519-125">親要素</span><span class="sxs-lookup"><span data-stu-id="50519-125">Parent Elements</span></span>  
  
|<span data-ttu-id="50519-126">要素</span><span class="sxs-lookup"><span data-stu-id="50519-126">Element</span></span>|<span data-ttu-id="50519-127">説明</span><span class="sxs-lookup"><span data-stu-id="50519-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50519-128">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="50519-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="50519-129">サービスの動作設定のコレクション。</span><span class="sxs-lookup"><span data-stu-id="50519-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="50519-130">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="50519-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="50519-131"><xref:System.Runtime.Serialization> 名前空間セクションのルート要素を表し、<xref:System.Runtime.Serialization.DataContractSerializer> のオプションを設定するための要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="50519-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50519-132">コメント</span><span class="sxs-lookup"><span data-stu-id="50519-132">Remarks</span></span>  
 <span data-ttu-id="50519-133">このトピックの概要で説明したように、これは、2 番目の階層を\<X509Extension > 要素が発生します。</span><span class="sxs-lookup"><span data-stu-id="50519-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="50519-134">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="50519-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="50519-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="50519-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="50519-136">既知の型の詳細については、<xref:System.Runtime.Serialization.DataContractSerializer> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50519-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50519-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="50519-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="50519-138">データ コントラクトの既知の型</span><span class="sxs-lookup"><span data-stu-id="50519-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="50519-139">データ転送とシリアル化</span><span class="sxs-lookup"><span data-stu-id="50519-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
