---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b974767aa86801bff234e200e1fce021bfc422c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755605"
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="0407a-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="0407a-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="0407a-103">カスタム クッキー ハンドラーの種類を設定します。</span><span class="sxs-lookup"><span data-stu-id="0407a-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="0407a-104">この要素が存在するのみ場合、`mode`の属性、`<cookieHandler>`要素は、"Custom"です。</span><span class="sxs-lookup"><span data-stu-id="0407a-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="0407a-105">カスタム型から派生する必要があります、<xref:System.IdentityModel.Services.CookieHandler>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0407a-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="0407a-106">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="0407a-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="0407a-107">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0407a-107">\<federationConfiguration></span></span>  
<span data-ttu-id="0407a-108">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="0407a-108">\<cookieHandler></span></span>  
<span data-ttu-id="0407a-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="0407a-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0407a-110">構文</span><span class="sxs-lookup"><span data-stu-id="0407a-110">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0407a-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0407a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0407a-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0407a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0407a-113">属性</span><span class="sxs-lookup"><span data-stu-id="0407a-113">Attributes</span></span>  
  
|<span data-ttu-id="0407a-114">属性</span><span class="sxs-lookup"><span data-stu-id="0407a-114">Attribute</span></span>|<span data-ttu-id="0407a-115">説明</span><span class="sxs-lookup"><span data-stu-id="0407a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0407a-116">型</span><span class="sxs-lookup"><span data-stu-id="0407a-116">type</span></span>|<span data-ttu-id="0407a-117">派生するカスタム型を指定します、<xref:System.IdentityModel.Services.CookieHandler>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0407a-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="0407a-118">指定する方法について、`type`属性は、「[カスタム型の参照](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="0407a-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0407a-119">子要素</span><span class="sxs-lookup"><span data-stu-id="0407a-119">Child Elements</span></span>  
 <span data-ttu-id="0407a-120">なし</span><span class="sxs-lookup"><span data-stu-id="0407a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0407a-121">親要素</span><span class="sxs-lookup"><span data-stu-id="0407a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0407a-122">要素</span><span class="sxs-lookup"><span data-stu-id="0407a-122">Element</span></span>|<span data-ttu-id="0407a-123">説明</span><span class="sxs-lookup"><span data-stu-id="0407a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0407a-124">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="0407a-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="0407a-125">構成、<xref:System.IdentityModel.Services.CookieHandler>を<xref:System.IdentityModel.Services.SessionAuthenticationModule>読み取りし、書き込みの cookie を使用します。</span><span class="sxs-lookup"><span data-stu-id="0407a-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0407a-126">コメント</span><span class="sxs-lookup"><span data-stu-id="0407a-126">Remarks</span></span>  
 <span data-ttu-id="0407a-127">設定して、カスタム クッキー ハンドラーを指定する場合、`mode`の属性、`<cookieHandler>`要素"Custom"にする必要がありますを指定するカスタム クッキー ハンドラーの型を含めることによって、`<customCookieHandler>`クッキー ハンドラー型を参照する子要素です。</span><span class="sxs-lookup"><span data-stu-id="0407a-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="0407a-128">この要素にすることはできない時に指定された、`mode`属性が"Chunked"または"Default"に設定します。</span><span class="sxs-lookup"><span data-stu-id="0407a-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="0407a-129">カスタム クッキー ハンドラーがから派生する必要があります、<xref:System.IdentityModel.Services.CookieHandler>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0407a-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="0407a-130">`<customCookieHandler>`要素として表されます、<xref:System.IdentityModel.Configuration.CustomTypeElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0407a-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0407a-131">例</span><span class="sxs-lookup"><span data-stu-id="0407a-131">Example</span></span>  
 <span data-ttu-id="0407a-132">次の例の構成の種類のカスタム クッキー ハンドラーを使用して、SAM`MyNamespace.MyCustomCookieHandler`です。</span><span class="sxs-lookup"><span data-stu-id="0407a-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0407a-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="0407a-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>
