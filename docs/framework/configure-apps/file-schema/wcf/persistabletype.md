---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 23724957398ed1ade2c81a3932e9773d7cf4c642
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747074"
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="578ed-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="578ed-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="578ed-103">すべての永続型を指定します。</span><span class="sxs-lookup"><span data-stu-id="578ed-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="578ed-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="578ed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="578ed-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="578ed-105">\<comContracts></span></span>  
<span data-ttu-id="578ed-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="578ed-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="578ed-107">構文</span><span class="sxs-lookup"><span data-stu-id="578ed-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="578ed-108">型</span><span class="sxs-lookup"><span data-stu-id="578ed-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="578ed-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="578ed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="578ed-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="578ed-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="578ed-111">属性</span><span class="sxs-lookup"><span data-stu-id="578ed-111">Attributes</span></span>  
  
|<span data-ttu-id="578ed-112">属性</span><span class="sxs-lookup"><span data-stu-id="578ed-112">Attribute</span></span>|<span data-ttu-id="578ed-113">説明</span><span class="sxs-lookup"><span data-stu-id="578ed-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="578ed-114">id</span><span class="sxs-lookup"><span data-stu-id="578ed-114">id</span></span>|<span data-ttu-id="578ed-115">永続型の一意の ID を指定する文字列を含む必須属性。</span><span class="sxs-lookup"><span data-stu-id="578ed-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="578ed-116">name</span><span class="sxs-lookup"><span data-stu-id="578ed-116">name</span></span>|<span data-ttu-id="578ed-117">永続型の名前を指定する文字列を含む省略可能な属性。</span><span class="sxs-lookup"><span data-stu-id="578ed-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="578ed-118">子要素</span><span class="sxs-lookup"><span data-stu-id="578ed-118">Child Elements</span></span>  
 <span data-ttu-id="578ed-119">なし</span><span class="sxs-lookup"><span data-stu-id="578ed-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="578ed-120">親要素</span><span class="sxs-lookup"><span data-stu-id="578ed-120">Parent Elements</span></span>  
  
|<span data-ttu-id="578ed-121">要素</span><span class="sxs-lookup"><span data-stu-id="578ed-121">Element</span></span>|<span data-ttu-id="578ed-122">説明</span><span class="sxs-lookup"><span data-stu-id="578ed-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="578ed-123">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="578ed-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="578ed-124">`persistableType` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="578ed-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="578ed-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="578ed-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="578ed-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="578ed-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="578ed-127">COM+ アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="578ed-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="578ed-128">方法 : COM+ サービス設定を構成する</span><span class="sxs-lookup"><span data-stu-id="578ed-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
