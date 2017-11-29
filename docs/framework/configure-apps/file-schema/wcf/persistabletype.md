---
title: '&lt;persistableType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c77bdf8ef02edf682ded95ab16b4d56dbf60b4ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="641d5-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="641d5-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="641d5-103">すべての永続型を指定します。</span><span class="sxs-lookup"><span data-stu-id="641d5-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="641d5-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="641d5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="641d5-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="641d5-105">\<comContracts></span></span>  
<span data-ttu-id="641d5-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="641d5-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="641d5-107">構文</span><span class="sxs-lookup"><span data-stu-id="641d5-107">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="type"></a><span data-ttu-id="641d5-108">型</span><span class="sxs-lookup"><span data-stu-id="641d5-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="641d5-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="641d5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="641d5-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="641d5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="641d5-111">属性</span><span class="sxs-lookup"><span data-stu-id="641d5-111">Attributes</span></span>  
  
|<span data-ttu-id="641d5-112">属性</span><span class="sxs-lookup"><span data-stu-id="641d5-112">Attribute</span></span>|<span data-ttu-id="641d5-113">説明</span><span class="sxs-lookup"><span data-stu-id="641d5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="641d5-114">id</span><span class="sxs-lookup"><span data-stu-id="641d5-114">id</span></span>|<span data-ttu-id="641d5-115">永続型の一意の ID を指定する文字列を含む必須属性。</span><span class="sxs-lookup"><span data-stu-id="641d5-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="641d5-116">name</span><span class="sxs-lookup"><span data-stu-id="641d5-116">name</span></span>|<span data-ttu-id="641d5-117">永続型の名前を指定する文字列を含む省略可能な属性。</span><span class="sxs-lookup"><span data-stu-id="641d5-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="641d5-118">子要素</span><span class="sxs-lookup"><span data-stu-id="641d5-118">Child Elements</span></span>  
 <span data-ttu-id="641d5-119">なし</span><span class="sxs-lookup"><span data-stu-id="641d5-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="641d5-120">親要素</span><span class="sxs-lookup"><span data-stu-id="641d5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="641d5-121">要素</span><span class="sxs-lookup"><span data-stu-id="641d5-121">Element</span></span>|<span data-ttu-id="641d5-122">説明</span><span class="sxs-lookup"><span data-stu-id="641d5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="641d5-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="641d5-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="641d5-124">`persistableType` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="641d5-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="641d5-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="641d5-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="641d5-126">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="641d5-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="641d5-127">COM + アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="641d5-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="641d5-128">方法: COM + サービス設定の構成</span><span class="sxs-lookup"><span data-stu-id="641d5-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
