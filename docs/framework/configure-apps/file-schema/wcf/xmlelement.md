---
title: '&lt;xmlElement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 702b5ea1331aa0ac284d62809367a90e200a8ba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="9757b-102">&lt;xmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="9757b-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="9757b-103">トークンの要求時にセキュリティ トークン サービスへのメッセージ本文で送信される XML 要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="9757b-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="9757b-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9757b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9757b-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9757b-105">\<bindings></span></span>  
<span data-ttu-id="9757b-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="9757b-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="9757b-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9757b-107">\<binding></span></span>  
<span data-ttu-id="9757b-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="9757b-108">\<security></span></span>  
<span data-ttu-id="9757b-109">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="9757b-109">\<message></span></span>  
<span data-ttu-id="9757b-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="9757b-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9757b-111">構文</span><span class="sxs-lookup"><span data-stu-id="9757b-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9757b-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9757b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9757b-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9757b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9757b-114">属性</span><span class="sxs-lookup"><span data-stu-id="9757b-114">Attributes</span></span>  
  
|<span data-ttu-id="9757b-115">属性</span><span class="sxs-lookup"><span data-stu-id="9757b-115">Attribute</span></span>|<span data-ttu-id="9757b-116">説明</span><span class="sxs-lookup"><span data-stu-id="9757b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9757b-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="9757b-117">xmlElement</span></span>|<span data-ttu-id="9757b-118">トークンの要求時にセキュリティ トークン サービスへのメッセージ本文で送信される XML 要素を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="9757b-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9757b-119">子要素</span><span class="sxs-lookup"><span data-stu-id="9757b-119">Child Elements</span></span>  
 <span data-ttu-id="9757b-120">なし。</span><span class="sxs-lookup"><span data-stu-id="9757b-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9757b-121">親要素</span><span class="sxs-lookup"><span data-stu-id="9757b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9757b-122">要素</span><span class="sxs-lookup"><span data-stu-id="9757b-122">Element</span></span>|<span data-ttu-id="9757b-123">説明</span><span class="sxs-lookup"><span data-stu-id="9757b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9757b-124">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="9757b-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="9757b-125">トークン要求パラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="9757b-125">A collection of token request parameters.</span></span> <span data-ttu-id="9757b-126">各パラメーターは、XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="9757b-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9757b-127">参照</span><span class="sxs-lookup"><span data-stu-id="9757b-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="9757b-128">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="9757b-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="9757b-129">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="9757b-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="9757b-130">カスタム バインドを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="9757b-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="9757b-131">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="9757b-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="9757b-132">バインディング</span><span class="sxs-lookup"><span data-stu-id="9757b-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
