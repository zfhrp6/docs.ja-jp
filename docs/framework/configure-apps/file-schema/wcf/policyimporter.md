---
title: '&lt;policyImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 99bb7c6be02bad85792dfce9de1f6ef8ba1dcd17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="7efb4-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="7efb4-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="7efb4-103">バインディングに関するカスタム ポリシー アサーションのインポートを制御するポリシー インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="7efb4-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="7efb4-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7efb4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7efb4-105">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="7efb4-105">\<client></span></span>  
<span data-ttu-id="7efb4-106">\<メタデータ ></span><span class="sxs-lookup"><span data-stu-id="7efb4-106">\<metadata></span></span>  
<span data-ttu-id="7efb4-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="7efb4-107">\<policyImporters></span></span>  
<span data-ttu-id="7efb4-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="7efb4-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7efb4-109">構文</span><span class="sxs-lookup"><span data-stu-id="7efb4-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7efb4-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7efb4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7efb4-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7efb4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7efb4-112">属性</span><span class="sxs-lookup"><span data-stu-id="7efb4-112">Attributes</span></span>  
  
|<span data-ttu-id="7efb4-113">属性</span><span class="sxs-lookup"><span data-stu-id="7efb4-113">Attribute</span></span>|<span data-ttu-id="7efb4-114">説明</span><span class="sxs-lookup"><span data-stu-id="7efb4-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="7efb4-115">この要素の型です。</span><span class="sxs-lookup"><span data-stu-id="7efb4-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7efb4-116">子要素</span><span class="sxs-lookup"><span data-stu-id="7efb4-116">Child Elements</span></span>  
 <span data-ttu-id="7efb4-117">なし</span><span class="sxs-lookup"><span data-stu-id="7efb4-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7efb4-118">親要素</span><span class="sxs-lookup"><span data-stu-id="7efb4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7efb4-119">要素</span><span class="sxs-lookup"><span data-stu-id="7efb4-119">Element</span></span>|<span data-ttu-id="7efb4-120">説明</span><span class="sxs-lookup"><span data-stu-id="7efb4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7efb4-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="7efb4-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="7efb4-122">バインディングに関するカスタム ポリシー アサーションのインポートを制御するすべてのポリシー インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="7efb4-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7efb4-123">コメント</span><span class="sxs-lookup"><span data-stu-id="7efb4-123">Remarks</span></span>  
 <span data-ttu-id="7efb4-124">ポリシー インポーターは、バインディング機能についてのカスタム ポリシー アサーションの検索、およびアサーションで必要となる機能を実装するカスタム バインディング要素の結び付けに使用されます。</span><span class="sxs-lookup"><span data-stu-id="7efb4-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7efb4-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="7efb4-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="7efb4-126">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="7efb4-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="7efb4-127">クライアント</span><span class="sxs-lookup"><span data-stu-id="7efb4-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
