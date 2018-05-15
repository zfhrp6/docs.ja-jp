---
title: '&lt;knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: b2445f12f1eaac03b3f3ab66f3d13a5f465a1133
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltknowntypegt"></a><span data-ttu-id="070e5-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="070e5-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="070e5-103">逆シリアル化中に <xref:System.Runtime.Serialization.DataContractSerializer> によって使用される型を指定します。</span><span class="sxs-lookup"><span data-stu-id="070e5-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="070e5-104">この要素には、"宣言型" のフィールドまたはプロパティによって返される "既知の型" を指定します。</span><span class="sxs-lookup"><span data-stu-id="070e5-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="070e5-105">詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="070e5-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="070e5-106">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="070e5-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="070e5-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="070e5-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="070e5-108">\<declaredTypes > 要素</span><span class="sxs-lookup"><span data-stu-id="070e5-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="070e5-109">\<追加 > の\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="070e5-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="070e5-110">\<knownType > 要素</span><span class="sxs-lookup"><span data-stu-id="070e5-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="070e5-111">構文</span><span class="sxs-lookup"><span data-stu-id="070e5-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="070e5-112">型</span><span class="sxs-lookup"><span data-stu-id="070e5-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="070e5-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="070e5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="070e5-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="070e5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="070e5-115">属性</span><span class="sxs-lookup"><span data-stu-id="070e5-115">Attributes</span></span>  
  
|<span data-ttu-id="070e5-116">属性</span><span class="sxs-lookup"><span data-stu-id="070e5-116">Attribute</span></span>|<span data-ttu-id="070e5-117">説明</span><span class="sxs-lookup"><span data-stu-id="070e5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="070e5-118">型</span><span class="sxs-lookup"><span data-stu-id="070e5-118">type</span></span>|<span data-ttu-id="070e5-119">型 (名前空間を含む)、アセンブリ名、バージョン、カルチャ、および公開キー トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="070e5-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="070e5-120">子要素</span><span class="sxs-lookup"><span data-stu-id="070e5-120">Child Elements</span></span>  
  
|<span data-ttu-id="070e5-121">要素</span><span class="sxs-lookup"><span data-stu-id="070e5-121">Element</span></span>|<span data-ttu-id="070e5-122">説明</span><span class="sxs-lookup"><span data-stu-id="070e5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="070e5-123">\<パラメーター ></span><span class="sxs-lookup"><span data-stu-id="070e5-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="070e5-124">宣言型がジェネリック型である場合に、パラメーター インデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="070e5-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="070e5-125">親要素</span><span class="sxs-lookup"><span data-stu-id="070e5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="070e5-126">要素</span><span class="sxs-lookup"><span data-stu-id="070e5-126">Element</span></span>|<span data-ttu-id="070e5-127">説明</span><span class="sxs-lookup"><span data-stu-id="070e5-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="070e5-128">\<add></span><span class="sxs-lookup"><span data-stu-id="070e5-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="070e5-129">宣言されたタイプのコレクションに、宣言されたタイプを追加します。</span><span class="sxs-lookup"><span data-stu-id="070e5-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="070e5-130">コメント</span><span class="sxs-lookup"><span data-stu-id="070e5-130">Remarks</span></span>  
 <span data-ttu-id="070e5-131">既知の型の詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)と<xref:System.Runtime.Serialization.DataContractSerializer>です。</span><span class="sxs-lookup"><span data-stu-id="070e5-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="070e5-132">参照してください、 [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)この要素の使用例についてはします。</span><span class="sxs-lookup"><span data-stu-id="070e5-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="070e5-133">例</span><span class="sxs-lookup"><span data-stu-id="070e5-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="070e5-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="070e5-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="070e5-135">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="070e5-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="070e5-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="070e5-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="070e5-137">\<add></span><span class="sxs-lookup"><span data-stu-id="070e5-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
