---
title: '&lt;knownType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bedebb98e5fc48292c503eef30cee30c8d29c41c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltknowntypegt"></a><span data-ttu-id="4047f-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="4047f-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="4047f-103">逆シリアル化中に <xref:System.Runtime.Serialization.DataContractSerializer> によって使用される型を指定します。</span><span class="sxs-lookup"><span data-stu-id="4047f-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="4047f-104">この要素には、"宣言型" のフィールドまたはプロパティによって返される "既知の型" を指定します。</span><span class="sxs-lookup"><span data-stu-id="4047f-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="4047f-105">詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="4047f-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="4047f-106">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="4047f-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="4047f-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="4047f-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="4047f-108">\<declaredTypes > 要素</span><span class="sxs-lookup"><span data-stu-id="4047f-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="4047f-109">\<追加 > の\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="4047f-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="4047f-110">\<knownType > 要素</span><span class="sxs-lookup"><span data-stu-id="4047f-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4047f-111">構文</span><span class="sxs-lookup"><span data-stu-id="4047f-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="4047f-112">型</span><span class="sxs-lookup"><span data-stu-id="4047f-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4047f-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4047f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4047f-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4047f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4047f-115">属性</span><span class="sxs-lookup"><span data-stu-id="4047f-115">Attributes</span></span>  
  
|<span data-ttu-id="4047f-116">属性</span><span class="sxs-lookup"><span data-stu-id="4047f-116">Attribute</span></span>|<span data-ttu-id="4047f-117">説明</span><span class="sxs-lookup"><span data-stu-id="4047f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4047f-118">型</span><span class="sxs-lookup"><span data-stu-id="4047f-118">type</span></span>|<span data-ttu-id="4047f-119">型 (名前空間を含む)、アセンブリ名、バージョン、カルチャ、および公開キー トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="4047f-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4047f-120">子要素</span><span class="sxs-lookup"><span data-stu-id="4047f-120">Child Elements</span></span>  
  
|<span data-ttu-id="4047f-121">要素</span><span class="sxs-lookup"><span data-stu-id="4047f-121">Element</span></span>|<span data-ttu-id="4047f-122">説明</span><span class="sxs-lookup"><span data-stu-id="4047f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4047f-123">\<パラメーター ></span><span class="sxs-lookup"><span data-stu-id="4047f-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="4047f-124">宣言型がジェネリック型である場合に、パラメーター インデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4047f-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4047f-125">親要素</span><span class="sxs-lookup"><span data-stu-id="4047f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4047f-126">要素</span><span class="sxs-lookup"><span data-stu-id="4047f-126">Element</span></span>|<span data-ttu-id="4047f-127">説明</span><span class="sxs-lookup"><span data-stu-id="4047f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4047f-128">\<add></span><span class="sxs-lookup"><span data-stu-id="4047f-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="4047f-129">宣言されたタイプのコレクションに、宣言されたタイプを追加します。</span><span class="sxs-lookup"><span data-stu-id="4047f-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4047f-130">コメント</span><span class="sxs-lookup"><span data-stu-id="4047f-130">Remarks</span></span>  
 <span data-ttu-id="4047f-131">既知の型の詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)と<xref:System.Runtime.Serialization.DataContractSerializer>です。</span><span class="sxs-lookup"><span data-stu-id="4047f-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="4047f-132">参照してください、 [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)この要素の使用例についてはします。</span><span class="sxs-lookup"><span data-stu-id="4047f-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4047f-133">例</span><span class="sxs-lookup"><span data-stu-id="4047f-133">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4047f-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="4047f-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="4047f-135">データ コントラクトの既知の型</span><span class="sxs-lookup"><span data-stu-id="4047f-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="4047f-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="4047f-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="4047f-137">\<add></span><span class="sxs-lookup"><span data-stu-id="4047f-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
