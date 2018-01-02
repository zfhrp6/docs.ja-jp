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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3064727eeda30c05f38558f4f0977c71e5abb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="b2a1d-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="b2a1d-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="b2a1d-103">すべての永続型を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2a1d-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="b2a1d-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b2a1d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b2a1d-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="b2a1d-105">\<comContracts></span></span>  
<span data-ttu-id="b2a1d-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="b2a1d-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a1d-107">構文</span><span class="sxs-lookup"><span data-stu-id="b2a1d-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="b2a1d-108">型</span><span class="sxs-lookup"><span data-stu-id="b2a1d-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2a1d-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b2a1d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b2a1d-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2a1d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2a1d-111">属性</span><span class="sxs-lookup"><span data-stu-id="b2a1d-111">Attributes</span></span>  
  
|<span data-ttu-id="b2a1d-112">属性</span><span class="sxs-lookup"><span data-stu-id="b2a1d-112">Attribute</span></span>|<span data-ttu-id="b2a1d-113">説明</span><span class="sxs-lookup"><span data-stu-id="b2a1d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2a1d-114">id</span><span class="sxs-lookup"><span data-stu-id="b2a1d-114">id</span></span>|<span data-ttu-id="b2a1d-115">永続型の一意の ID を指定する文字列を含む必須属性。</span><span class="sxs-lookup"><span data-stu-id="b2a1d-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="b2a1d-116">name</span><span class="sxs-lookup"><span data-stu-id="b2a1d-116">name</span></span>|<span data-ttu-id="b2a1d-117">永続型の名前を指定する文字列を含む省略可能な属性。</span><span class="sxs-lookup"><span data-stu-id="b2a1d-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2a1d-118">子要素</span><span class="sxs-lookup"><span data-stu-id="b2a1d-118">Child Elements</span></span>  
 <span data-ttu-id="b2a1d-119">なし</span><span class="sxs-lookup"><span data-stu-id="b2a1d-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2a1d-120">親要素</span><span class="sxs-lookup"><span data-stu-id="b2a1d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b2a1d-121">要素</span><span class="sxs-lookup"><span data-stu-id="b2a1d-121">Element</span></span>|<span data-ttu-id="b2a1d-122">説明</span><span class="sxs-lookup"><span data-stu-id="b2a1d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2a1d-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="b2a1d-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="b2a1d-124">`persistableType` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="b2a1d-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2a1d-125">参照</span><span class="sxs-lookup"><span data-stu-id="b2a1d-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="b2a1d-126">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="b2a1d-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="b2a1d-127">COM+ アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="b2a1d-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="b2a1d-128">方法 : COM+ サービス設定を構成する</span><span class="sxs-lookup"><span data-stu-id="b2a1d-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
