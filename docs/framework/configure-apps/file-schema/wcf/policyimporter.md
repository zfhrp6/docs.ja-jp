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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2226b4f55025c9dec3fdeb4f9b4f51016ffd3e8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="8341c-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="8341c-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="8341c-103">バインディングに関するカスタム ポリシー アサーションのインポートを制御するポリシー インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="8341c-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="8341c-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8341c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8341c-105">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="8341c-105">\<client></span></span>  
<span data-ttu-id="8341c-106">\<メタデータ ></span><span class="sxs-lookup"><span data-stu-id="8341c-106">\<metadata></span></span>  
<span data-ttu-id="8341c-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="8341c-107">\<policyImporters></span></span>  
<span data-ttu-id="8341c-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="8341c-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8341c-109">構文</span><span class="sxs-lookup"><span data-stu-id="8341c-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8341c-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8341c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8341c-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8341c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8341c-112">属性</span><span class="sxs-lookup"><span data-stu-id="8341c-112">Attributes</span></span>  
  
|<span data-ttu-id="8341c-113">属性</span><span class="sxs-lookup"><span data-stu-id="8341c-113">Attribute</span></span>|<span data-ttu-id="8341c-114">説明</span><span class="sxs-lookup"><span data-stu-id="8341c-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="8341c-115">この要素の型です。</span><span class="sxs-lookup"><span data-stu-id="8341c-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8341c-116">子要素</span><span class="sxs-lookup"><span data-stu-id="8341c-116">Child Elements</span></span>  
 <span data-ttu-id="8341c-117">なし</span><span class="sxs-lookup"><span data-stu-id="8341c-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8341c-118">親要素</span><span class="sxs-lookup"><span data-stu-id="8341c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8341c-119">要素</span><span class="sxs-lookup"><span data-stu-id="8341c-119">Element</span></span>|<span data-ttu-id="8341c-120">説明</span><span class="sxs-lookup"><span data-stu-id="8341c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8341c-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="8341c-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="8341c-122">バインディングに関するカスタム ポリシー アサーションのインポートを制御するすべてのポリシー インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="8341c-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8341c-123">コメント</span><span class="sxs-lookup"><span data-stu-id="8341c-123">Remarks</span></span>  
 <span data-ttu-id="8341c-124">ポリシー インポーターは、バインディング機能についてのカスタム ポリシー アサーションの検索、およびアサーションで必要となる機能を実装するカスタム バインディング要素の結び付けに使用されます。</span><span class="sxs-lookup"><span data-stu-id="8341c-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8341c-125">参照</span><span class="sxs-lookup"><span data-stu-id="8341c-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="8341c-126">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="8341c-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="8341c-127">クライアント</span><span class="sxs-lookup"><span data-stu-id="8341c-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
