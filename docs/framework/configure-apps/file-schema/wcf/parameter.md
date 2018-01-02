---
title: "&lt;パラメーター&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdbb47fcb65273d03d226e13730849170d4345c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltparametergt"></a><span data-ttu-id="c1ffc-102">&lt;パラメーター&gt;</span><span class="sxs-lookup"><span data-stu-id="c1ffc-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="c1ffc-103">宣言された型がジェネリック型である場合、ジェネリック パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="c1ffc-104">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="c1ffc-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="c1ffc-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c1ffc-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="c1ffc-106">\<declaredTypes > 要素</span><span class="sxs-lookup"><span data-stu-id="c1ffc-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="c1ffc-107">\<追加 > 要素を\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="c1ffc-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="c1ffc-108">\<knownType > 要素</span><span class="sxs-lookup"><span data-stu-id="c1ffc-108">\<knownType> Element</span></span>  
<span data-ttu-id="c1ffc-109">\<パラメーター > 要素</span><span class="sxs-lookup"><span data-stu-id="c1ffc-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ffc-110">構文</span><span class="sxs-lookup"><span data-stu-id="c1ffc-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1ffc-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c1ffc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c1ffc-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1ffc-113">属性</span><span class="sxs-lookup"><span data-stu-id="c1ffc-113">Attributes</span></span>  
  
|<span data-ttu-id="c1ffc-114">属性</span><span class="sxs-lookup"><span data-stu-id="c1ffc-114">Attribute</span></span>|<span data-ttu-id="c1ffc-115">説明</span><span class="sxs-lookup"><span data-stu-id="c1ffc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1ffc-116">インデックス</span><span class="sxs-lookup"><span data-stu-id="c1ffc-116">index</span></span>|<span data-ttu-id="c1ffc-117">宣言された型がジェネリック型である場合、既知の型を返すジェネリック パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="c1ffc-118">型</span><span class="sxs-lookup"><span data-stu-id="c1ffc-118">type</span></span>|<span data-ttu-id="c1ffc-119">シリアル化と逆シリアル化で使用される既知の型を説明する文字列。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="c1ffc-120">index 属性</span><span class="sxs-lookup"><span data-stu-id="c1ffc-120">index Attribute</span></span>  
  
|<span data-ttu-id="c1ffc-121">値</span><span class="sxs-lookup"><span data-stu-id="c1ffc-121">Value</span></span>|<span data-ttu-id="c1ffc-122">説明</span><span class="sxs-lookup"><span data-stu-id="c1ffc-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1ffc-123">"0"</span><span class="sxs-lookup"><span data-stu-id="c1ffc-123">"0"</span></span>|<span data-ttu-id="c1ffc-124">ジェネリック型の最初のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-124">The first parameter in the generic type.</span></span> <span data-ttu-id="c1ffc-125">たとえば、<xref:System.Collections.Generic.List%601> にはパラメーターが 1 つだけあります。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="c1ffc-126">宣言型として使用される場合、index は "0" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="c1ffc-127">"1"</span><span class="sxs-lookup"><span data-stu-id="c1ffc-127">"1"</span></span>|<span data-ttu-id="c1ffc-128">ジェネリック型の 2 番目のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-128">The second parameter in a generic type.</span></span> <span data-ttu-id="c1ffc-129">たとえば、<xref:System.Collections.Generic.Dictionary%602> には 2 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="c1ffc-130">2 番目のパラメーターによって既知の型が返される場合は、index 属性を "1" に設定します。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1ffc-131">子要素</span><span class="sxs-lookup"><span data-stu-id="c1ffc-131">Child Elements</span></span>  
 <span data-ttu-id="c1ffc-132">なし。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1ffc-133">親要素</span><span class="sxs-lookup"><span data-stu-id="c1ffc-133">Parent Elements</span></span>  
  
|<span data-ttu-id="c1ffc-134">要素</span><span class="sxs-lookup"><span data-stu-id="c1ffc-134">Element</span></span>|<span data-ttu-id="c1ffc-135">説明</span><span class="sxs-lookup"><span data-stu-id="c1ffc-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1ffc-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="c1ffc-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="c1ffc-137">宣言型のフィールドまたはプロパティによって返される既知の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1ffc-138">コメント</span><span class="sxs-lookup"><span data-stu-id="c1ffc-138">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="c1ffc-139">既知の型を参照してください[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)と<xref:System.Runtime.Serialization.DataContractSerializer>です。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-139"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="c1ffc-140">参照してください、 [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)この要素の使用例についてはします。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="c1ffc-141">この構成要素に、両方の属性を同時に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="c1ffc-142">両方の属性が設定された場合、<xref:System.Configuration.ConfigurationErrorsException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="c1ffc-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ffc-143">参照</span><span class="sxs-lookup"><span data-stu-id="c1ffc-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="c1ffc-144">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="c1ffc-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="c1ffc-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c1ffc-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="c1ffc-146">\<add></span><span class="sxs-lookup"><span data-stu-id="c1ffc-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
