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
ms.openlocfilehash: 8ccc11dd714c1074b2710280e02a8b5ad47b843b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltparametergt"></a><span data-ttu-id="1daea-102">&lt;パラメーター&gt;</span><span class="sxs-lookup"><span data-stu-id="1daea-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="1daea-103">宣言された型がジェネリック型である場合、ジェネリック パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="1daea-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="1daea-104">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="1daea-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="1daea-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="1daea-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="1daea-106">\<declaredTypes > 要素</span><span class="sxs-lookup"><span data-stu-id="1daea-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="1daea-107">\<追加 > 要素を\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="1daea-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="1daea-108">\<knownType > 要素</span><span class="sxs-lookup"><span data-stu-id="1daea-108">\<knownType> Element</span></span>  
<span data-ttu-id="1daea-109">\<パラメーター > 要素</span><span class="sxs-lookup"><span data-stu-id="1daea-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1daea-110">構文</span><span class="sxs-lookup"><span data-stu-id="1daea-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1daea-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1daea-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1daea-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1daea-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1daea-113">属性</span><span class="sxs-lookup"><span data-stu-id="1daea-113">Attributes</span></span>  
  
|<span data-ttu-id="1daea-114">属性</span><span class="sxs-lookup"><span data-stu-id="1daea-114">Attribute</span></span>|<span data-ttu-id="1daea-115">説明</span><span class="sxs-lookup"><span data-stu-id="1daea-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1daea-116">インデックス</span><span class="sxs-lookup"><span data-stu-id="1daea-116">index</span></span>|<span data-ttu-id="1daea-117">宣言された型がジェネリック型である場合、既知の型を返すジェネリック パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="1daea-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="1daea-118">型</span><span class="sxs-lookup"><span data-stu-id="1daea-118">type</span></span>|<span data-ttu-id="1daea-119">シリアル化と逆シリアル化で使用される既知の型を説明する文字列。</span><span class="sxs-lookup"><span data-stu-id="1daea-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="1daea-120">index 属性</span><span class="sxs-lookup"><span data-stu-id="1daea-120">index Attribute</span></span>  
  
|<span data-ttu-id="1daea-121">値</span><span class="sxs-lookup"><span data-stu-id="1daea-121">Value</span></span>|<span data-ttu-id="1daea-122">説明</span><span class="sxs-lookup"><span data-stu-id="1daea-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1daea-123">"0"</span><span class="sxs-lookup"><span data-stu-id="1daea-123">"0"</span></span>|<span data-ttu-id="1daea-124">ジェネリック型の最初のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="1daea-124">The first parameter in the generic type.</span></span> <span data-ttu-id="1daea-125">たとえば、<xref:System.Collections.Generic.List%601> にはパラメーターが 1 つだけあります。</span><span class="sxs-lookup"><span data-stu-id="1daea-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="1daea-126">宣言型として使用される場合、index は "0" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1daea-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="1daea-127">"1"</span><span class="sxs-lookup"><span data-stu-id="1daea-127">"1"</span></span>|<span data-ttu-id="1daea-128">ジェネリック型の 2 番目のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="1daea-128">The second parameter in a generic type.</span></span> <span data-ttu-id="1daea-129">たとえば、<xref:System.Collections.Generic.Dictionary%602> には 2 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="1daea-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="1daea-130">2 番目のパラメーターによって既知の型が返される場合は、index 属性を "1" に設定します。</span><span class="sxs-lookup"><span data-stu-id="1daea-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1daea-131">子要素</span><span class="sxs-lookup"><span data-stu-id="1daea-131">Child Elements</span></span>  
 <span data-ttu-id="1daea-132">なし。</span><span class="sxs-lookup"><span data-stu-id="1daea-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1daea-133">親要素</span><span class="sxs-lookup"><span data-stu-id="1daea-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1daea-134">要素</span><span class="sxs-lookup"><span data-stu-id="1daea-134">Element</span></span>|<span data-ttu-id="1daea-135">説明</span><span class="sxs-lookup"><span data-stu-id="1daea-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1daea-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="1daea-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="1daea-137">宣言型のフィールドまたはプロパティによって返される既知の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="1daea-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1daea-138">コメント</span><span class="sxs-lookup"><span data-stu-id="1daea-138">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="1daea-139">既知の型を参照してください[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)と<xref:System.Runtime.Serialization.DataContractSerializer>です。</span><span class="sxs-lookup"><span data-stu-id="1daea-139"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="1daea-140">参照してください、 [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)この要素の使用例についてはします。</span><span class="sxs-lookup"><span data-stu-id="1daea-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="1daea-141">この構成要素に、両方の属性を同時に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="1daea-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="1daea-142">両方の属性が設定された場合、<xref:System.Configuration.ConfigurationErrorsException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="1daea-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1daea-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="1daea-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="1daea-144">データ コントラクトの既知の型</span><span class="sxs-lookup"><span data-stu-id="1daea-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="1daea-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="1daea-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="1daea-146">\<add></span><span class="sxs-lookup"><span data-stu-id="1daea-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
