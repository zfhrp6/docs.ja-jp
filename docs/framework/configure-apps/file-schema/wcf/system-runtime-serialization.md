---
title: '&lt;system.runtime.serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a6eb2b152f2ab11bbe0e08ff1ad22f94d45057e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="14d96-102">&lt;system.runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="14d96-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="14d96-103"><xref:System.Runtime.Serialization> 名前空間セクションのルート要素を表し、<xref:System.Runtime.Serialization.DataContractSerializer> のオプションを設定するための要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="14d96-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="14d96-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="14d96-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d96-105">構文</span><span class="sxs-lookup"><span data-stu-id="14d96-105">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
             <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14d96-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="14d96-106">Attributes and Elements</span></span>  
 <span data-ttu-id="14d96-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="14d96-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14d96-108">属性</span><span class="sxs-lookup"><span data-stu-id="14d96-108">Attributes</span></span>  
 <span data-ttu-id="14d96-109">なし。</span><span class="sxs-lookup"><span data-stu-id="14d96-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14d96-110">子要素</span><span class="sxs-lookup"><span data-stu-id="14d96-110">Child Elements</span></span>  
  
|<span data-ttu-id="14d96-111">要素</span><span class="sxs-lookup"><span data-stu-id="14d96-111">Element</span></span>|<span data-ttu-id="14d96-112">説明</span><span class="sxs-lookup"><span data-stu-id="14d96-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14d96-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="14d96-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="14d96-114">逆シリアル化時に使用される既知の型の追加を可能にします。</span><span class="sxs-lookup"><span data-stu-id="14d96-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14d96-115">親要素</span><span class="sxs-lookup"><span data-stu-id="14d96-115">Parent Elements</span></span>  
  
|<span data-ttu-id="14d96-116">要素</span><span class="sxs-lookup"><span data-stu-id="14d96-116">Element</span></span>|<span data-ttu-id="14d96-117">説明</span><span class="sxs-lookup"><span data-stu-id="14d96-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14d96-118">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="14d96-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="14d96-119">構成の最上位の要素。</span><span class="sxs-lookup"><span data-stu-id="14d96-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14d96-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="14d96-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="14d96-121">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="14d96-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="14d96-122">データ コントラクトの既知の型</span><span class="sxs-lookup"><span data-stu-id="14d96-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
