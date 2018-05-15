---
title: '&lt;XmlElement&gt;'
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 70ff9b93bcd59331c5fa5e66bb51dc4cd1e043ff
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="c65a8-102">&lt;XmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="c65a8-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="c65a8-103">トークンの要求時にセキュリティ トークン サービスへのメッセージ本文で送信される XML 要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="c65a8-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="c65a8-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c65a8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c65a8-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c65a8-105">\<bindings></span></span>  
<span data-ttu-id="c65a8-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="c65a8-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="c65a8-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="c65a8-107">\<binding></span></span>  
<span data-ttu-id="c65a8-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="c65a8-108">\<security></span></span>  
<span data-ttu-id="c65a8-109">\<message></span><span class="sxs-lookup"><span data-stu-id="c65a8-109">\<message></span></span>  
<span data-ttu-id="c65a8-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="c65a8-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65a8-111">構文</span><span class="sxs-lookup"><span data-stu-id="c65a8-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c65a8-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c65a8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c65a8-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c65a8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c65a8-114">属性</span><span class="sxs-lookup"><span data-stu-id="c65a8-114">Attributes</span></span>  
  
|<span data-ttu-id="c65a8-115">属性</span><span class="sxs-lookup"><span data-stu-id="c65a8-115">Attribute</span></span>|<span data-ttu-id="c65a8-116">説明</span><span class="sxs-lookup"><span data-stu-id="c65a8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c65a8-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="c65a8-117">xmlElement</span></span>|<span data-ttu-id="c65a8-118">トークンの要求時にセキュリティ トークン サービスへのメッセージ本文で送信される XML 要素を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="c65a8-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c65a8-119">子要素</span><span class="sxs-lookup"><span data-stu-id="c65a8-119">Child Elements</span></span>  
 <span data-ttu-id="c65a8-120">なし。</span><span class="sxs-lookup"><span data-stu-id="c65a8-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c65a8-121">親要素</span><span class="sxs-lookup"><span data-stu-id="c65a8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c65a8-122">要素</span><span class="sxs-lookup"><span data-stu-id="c65a8-122">Element</span></span>|<span data-ttu-id="c65a8-123">説明</span><span class="sxs-lookup"><span data-stu-id="c65a8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c65a8-124">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="c65a8-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="c65a8-125">トークン要求パラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="c65a8-125">A collection of token request parameters.</span></span> <span data-ttu-id="c65a8-126">各パラメーターは、XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="c65a8-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c65a8-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c65a8-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="c65a8-128">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="c65a8-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="c65a8-129">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="c65a8-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="c65a8-130">カスタム バインドを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="c65a8-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="c65a8-131">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="c65a8-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="c65a8-132">バインディング</span><span class="sxs-lookup"><span data-stu-id="c65a8-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
