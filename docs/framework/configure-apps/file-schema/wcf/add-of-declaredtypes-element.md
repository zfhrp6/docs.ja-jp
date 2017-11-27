---
title: "&lt;declaredTypes&gt; 要素の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 699d18b4c49d2915724309d96d4ad501b98601eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a><span data-ttu-id="0f47b-102">&lt;declaredTypes&gt; 要素の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="0f47b-102">&lt;add&gt; of &lt;declaredTypes&gt; Element</span></span>
<span data-ttu-id="0f47b-103">逆シリアル化中に、<xref:System.Runtime.Serialization.DataContractSerializer> で使用される型を追加します。</span><span class="sxs-lookup"><span data-stu-id="0f47b-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="0f47b-104">各宣言型は、宣言型のフィールドまたはプロパティとして返される既知の型を含みます。</span><span class="sxs-lookup"><span data-stu-id="0f47b-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="0f47b-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="0f47b-105">system.runtime.serialization</span></span>  
<span data-ttu-id="0f47b-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="0f47b-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="0f47b-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="0f47b-107">\<declaredTypes></span></span>  
<span data-ttu-id="0f47b-108">\<追加 > の\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="0f47b-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f47b-109">構文</span><span class="sxs-lookup"><span data-stu-id="0f47b-109">Syntax</span></span>  
  
```xml  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f47b-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0f47b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0f47b-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0f47b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f47b-112">属性</span><span class="sxs-lookup"><span data-stu-id="0f47b-112">Attributes</span></span>  
  
|<span data-ttu-id="0f47b-113">属性</span><span class="sxs-lookup"><span data-stu-id="0f47b-113">Attribute</span></span>|<span data-ttu-id="0f47b-114">説明</span><span class="sxs-lookup"><span data-stu-id="0f47b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f47b-115">型</span><span class="sxs-lookup"><span data-stu-id="0f47b-115">type</span></span>|<span data-ttu-id="0f47b-116">必須の文字列属性です。</span><span class="sxs-lookup"><span data-stu-id="0f47b-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="0f47b-117">型名 (名前空間を含む)、アセンブリ名、バージョン番号、カルチャ、および公開キー トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="0f47b-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f47b-118">子要素</span><span class="sxs-lookup"><span data-stu-id="0f47b-118">Child Elements</span></span>  
  
|<span data-ttu-id="0f47b-119">要素</span><span class="sxs-lookup"><span data-stu-id="0f47b-119">Element</span></span>|<span data-ttu-id="0f47b-120">説明</span><span class="sxs-lookup"><span data-stu-id="0f47b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f47b-121">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="0f47b-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="0f47b-122">追加される宣言型の既知の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f47b-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="0f47b-123">宣言型がジェネリック型の場合は、既知の型を返すために使用されるジェネリック パラメーターを指定するために、`<knownType>` にパラメーター要素も追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f47b-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f47b-124">親要素</span><span class="sxs-lookup"><span data-stu-id="0f47b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0f47b-125">要素</span><span class="sxs-lookup"><span data-stu-id="0f47b-125">Element</span></span>|<span data-ttu-id="0f47b-126">説明</span><span class="sxs-lookup"><span data-stu-id="0f47b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f47b-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="0f47b-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="0f47b-128"><xref:System.Runtime.Serialization.DataContractSerializer> による逆シリアル化中に既知のタイプを必要とするタイプが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0f47b-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f47b-129">コメント</span><span class="sxs-lookup"><span data-stu-id="0f47b-129">Remarks</span></span>  
 <span data-ttu-id="0f47b-130">既知の型の詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)と<xref:System.Runtime.Serialization.DataContractSerializer>です。</span><span class="sxs-lookup"><span data-stu-id="0f47b-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="0f47b-131">参照してください、 [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)この要素の使用例についてはします。</span><span class="sxs-lookup"><span data-stu-id="0f47b-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f47b-132"><xref:System.Object> 型を `<declaredType>` として追加すると、<xref:System.Configuration.ConfigurationErrorsException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0f47b-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="0f47b-133">これは、構成で <xref:System.Object> 型を宣言型として使用できないためです。</span><span class="sxs-lookup"><span data-stu-id="0f47b-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f47b-134">例</span><span class="sxs-lookup"><span data-stu-id="0f47b-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f47b-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f47b-135">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="0f47b-136">データ コントラクトの既知の型</span><span class="sxs-lookup"><span data-stu-id="0f47b-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="0f47b-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="0f47b-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="0f47b-138">\<追加 > の\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="0f47b-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
