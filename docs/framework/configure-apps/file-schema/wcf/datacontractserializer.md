---
title: dataContractSerializer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4044e81b7c33c7a755678e79586dd4f37cf54ed5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="datacontractserializer"></a><span data-ttu-id="f2f31-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="f2f31-102">dataContractSerializer</span></span>
<span data-ttu-id="f2f31-103"><xref:System.Runtime.Serialization.DataContractSerializer> 用の設定データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2f31-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f2f31-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f2f31-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f2f31-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="f2f31-105">\<behaviors></span></span>  
<span data-ttu-id="f2f31-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f2f31-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f2f31-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="f2f31-107">\<behavior></span></span>  
<span data-ttu-id="f2f31-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="f2f31-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f31-109">構文</span><span class="sxs-lookup"><span data-stu-id="f2f31-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2f31-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f2f31-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f2f31-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2f31-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2f31-112">属性</span><span class="sxs-lookup"><span data-stu-id="f2f31-112">Attributes</span></span>  
  
|<span data-ttu-id="f2f31-113">要素</span><span class="sxs-lookup"><span data-stu-id="f2f31-113">Element</span></span>|<span data-ttu-id="f2f31-114">説明</span><span class="sxs-lookup"><span data-stu-id="f2f31-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2f31-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="f2f31-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="f2f31-116">エンドポイントがシリアル化または逆シリアル化されているときに、そのエンドポイントにより提供されるデータを無視するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="f2f31-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="f2f31-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="f2f31-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="f2f31-118">シリアル化または逆シリアル化する項目の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="f2f31-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2f31-119">子要素</span><span class="sxs-lookup"><span data-stu-id="f2f31-119">Child Elements</span></span>  
 <span data-ttu-id="f2f31-120">なし。</span><span class="sxs-lookup"><span data-stu-id="f2f31-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2f31-121">親要素</span><span class="sxs-lookup"><span data-stu-id="f2f31-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f2f31-122">要素</span><span class="sxs-lookup"><span data-stu-id="f2f31-122">Element</span></span>|<span data-ttu-id="f2f31-123">説明</span><span class="sxs-lookup"><span data-stu-id="f2f31-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2f31-124">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="f2f31-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f2f31-125">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2f31-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2f31-126">コメント</span><span class="sxs-lookup"><span data-stu-id="f2f31-126">Remarks</span></span>  
 <span data-ttu-id="f2f31-127">既知の型の詳細については、<xref:System.Runtime.Serialization.DataContractSerializer> のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2f31-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f2f31-128">`<dataContractSerializer>` 動作要素が存在する場合は、構成ファイル内で `<enableWebScript>` 動作要素よりも前に出現する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2f31-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="f2f31-129">それ以外の場合は、動作結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="f2f31-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f31-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2f31-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="f2f31-131">データ コントラクトの既知の型</span><span class="sxs-lookup"><span data-stu-id="f2f31-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="f2f31-132">データ転送とシリアル化</span><span class="sxs-lookup"><span data-stu-id="f2f31-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
