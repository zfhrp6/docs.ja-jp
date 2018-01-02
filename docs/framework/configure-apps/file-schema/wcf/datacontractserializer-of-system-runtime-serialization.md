---
title: "&lt;system.runtime.serialization&gt; の &lt;dataContractSerializer&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 836d00cb0c3de36e8fd918babb605cf629239357
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="6b625-102">&lt;system.runtime.serialization&gt; の &lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="6b625-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="6b625-103"><xref:System.Runtime.Serialization.DataContractSerializer> 用の設定データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b625-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6b625-104">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="6b625-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="6b625-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6b625-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b625-106">構文</span><span class="sxs-lookup"><span data-stu-id="6b625-106">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
            maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String">  
          <knownType type="String">  
             <parameter index="Integer"  
                        type="String" />  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b625-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6b625-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6b625-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b625-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b625-109">属性</span><span class="sxs-lookup"><span data-stu-id="6b625-109">Attributes</span></span>  
  
|<span data-ttu-id="6b625-110">要素</span><span class="sxs-lookup"><span data-stu-id="6b625-110">Element</span></span>|<span data-ttu-id="6b625-111">説明</span><span class="sxs-lookup"><span data-stu-id="6b625-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b625-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="6b625-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="6b625-113">エンドポイントがシリアル化または逆シリアル化されているときに、そのエンドポイントにより提供されるデータを無視するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="6b625-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="6b625-114">この属性は、`<dataContractSerializer>` 要素の下の `<behavior>` でのみ設定可能です。</span><span class="sxs-lookup"><span data-stu-id="6b625-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="6b625-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="6b625-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="6b625-116">シリアル化または逆シリアル化する項目の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="6b625-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="6b625-117">この属性は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="6b625-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b625-118">子要素</span><span class="sxs-lookup"><span data-stu-id="6b625-118">Child Elements</span></span>  
  
|<span data-ttu-id="6b625-119">要素</span><span class="sxs-lookup"><span data-stu-id="6b625-119">Element</span></span>|<span data-ttu-id="6b625-120">説明</span><span class="sxs-lookup"><span data-stu-id="6b625-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b625-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="6b625-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="6b625-122">逆シリアル化時に <xref:System.Runtime.Serialization.DataContractSerializer> が使用する既知の型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b625-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="6b625-123">データ コントラクトと既知の型の詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b625-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b625-124">親要素</span><span class="sxs-lookup"><span data-stu-id="6b625-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6b625-125">要素</span><span class="sxs-lookup"><span data-stu-id="6b625-125">Element</span></span>|<span data-ttu-id="6b625-126">説明</span><span class="sxs-lookup"><span data-stu-id="6b625-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b625-127">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="6b625-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="6b625-128"><xref:System.Runtime.Serialization> 名前空間セクションのルート要素を表し、<xref:System.Runtime.Serialization.DataContractSerializer> のオプションを設定するための要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="6b625-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b625-129">コメント</span><span class="sxs-lookup"><span data-stu-id="6b625-129">Remarks</span></span>  
 <span data-ttu-id="6b625-130">既知の型の詳細については、次を参照してください。<xref:System.Runtime.Serialization.DataContractSerializer>と[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b625-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b625-131">参照</span><span class="sxs-lookup"><span data-stu-id="6b625-131">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [<span data-ttu-id="6b625-132">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="6b625-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
