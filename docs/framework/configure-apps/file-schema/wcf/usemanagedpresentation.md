---
title: '&lt;useManagedPresentation&gt;'
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 35af7f5e10594617807384c20ab706ad675d11ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755293"
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="249a1-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="249a1-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="249a1-103">WS-Trust の CardSpace プロファイルをサポートする CardSpace セキュリティ トークン サービスとの通信に使用するバインド要素。</span><span class="sxs-lookup"><span data-stu-id="249a1-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="249a1-104">この要素には属性がなく、空のスイッチとして表されます。</span><span class="sxs-lookup"><span data-stu-id="249a1-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="249a1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="249a1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="249a1-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="249a1-106">\<bindings></span></span>  
<span data-ttu-id="249a1-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="249a1-107">\<customBinding></span></span>  
<span data-ttu-id="249a1-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="249a1-108">\<binding></span></span>  
<span data-ttu-id="249a1-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="249a1-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="249a1-110">構文</span><span class="sxs-lookup"><span data-stu-id="249a1-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="249a1-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="249a1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="249a1-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="249a1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="249a1-113">属性</span><span class="sxs-lookup"><span data-stu-id="249a1-113">Attributes</span></span>  
 <span data-ttu-id="249a1-114">なし。</span><span class="sxs-lookup"><span data-stu-id="249a1-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="249a1-115">子要素</span><span class="sxs-lookup"><span data-stu-id="249a1-115">Child Elements</span></span>  
 <span data-ttu-id="249a1-116">なし</span><span class="sxs-lookup"><span data-stu-id="249a1-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="249a1-117">親要素</span><span class="sxs-lookup"><span data-stu-id="249a1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="249a1-118">要素</span><span class="sxs-lookup"><span data-stu-id="249a1-118">Element</span></span>|<span data-ttu-id="249a1-119">説明</span><span class="sxs-lookup"><span data-stu-id="249a1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="249a1-120">\<binding></span><span class="sxs-lookup"><span data-stu-id="249a1-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="249a1-121">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="249a1-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="249a1-122">コメント</span><span class="sxs-lookup"><span data-stu-id="249a1-122">Remarks</span></span>  
 <span data-ttu-id="249a1-123">この要素は、WS-Trust の CardSpace プロファイルをサポートするという事実をポリシーで明示するために、ID プロバイダーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="249a1-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="249a1-124">このようなポリシー アサーションを公開する ID プロバイダーは、その CardSpace プロファイルに基づくトークンを発行できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="249a1-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="249a1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="249a1-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="249a1-126">バインディング</span><span class="sxs-lookup"><span data-stu-id="249a1-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="249a1-127">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="249a1-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="249a1-128">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="249a1-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="249a1-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="249a1-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
