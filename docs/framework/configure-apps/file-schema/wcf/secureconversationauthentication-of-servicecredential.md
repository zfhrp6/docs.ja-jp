---
title: "&lt;serviceCredential&gt; の &lt;secureConversationAuthentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f80b0570055edbe15fa467ea83e11aba2b62a8fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="cdbb5-102">&lt;serviceCredential&gt; の &lt;secureConversationAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="cdbb5-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="cdbb5-103">安全な会話サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="cdbb5-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="cdbb5-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cdbb5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cdbb5-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="cdbb5-105">\<behaviors></span></span>  
<span data-ttu-id="cdbb5-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cdbb5-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cdbb5-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="cdbb5-107">\<behavior></span></span>  
<span data-ttu-id="cdbb5-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="cdbb5-108">\<serviceCredentials></span></span>  
<span data-ttu-id="cdbb5-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="cdbb5-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdbb5-110">構文</span><span class="sxs-lookup"><span data-stu-id="cdbb5-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdbb5-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cdbb5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cdbb5-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cdbb5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdbb5-113">属性</span><span class="sxs-lookup"><span data-stu-id="cdbb5-113">Attributes</span></span>  
  
|<span data-ttu-id="cdbb5-114">属性</span><span class="sxs-lookup"><span data-stu-id="cdbb5-114">Attribute</span></span>|<span data-ttu-id="cdbb5-115">説明</span><span class="sxs-lookup"><span data-stu-id="cdbb5-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="cdbb5-116">使用される <xref:System.ServiceModel.Security.SecurityStateEncoder> の型を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="cdbb5-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdbb5-117">子要素</span><span class="sxs-lookup"><span data-stu-id="cdbb5-117">Child Elements</span></span>  
 <span data-ttu-id="cdbb5-118">なし。</span><span class="sxs-lookup"><span data-stu-id="cdbb5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cdbb5-119">親要素</span><span class="sxs-lookup"><span data-stu-id="cdbb5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cdbb5-120">要素</span><span class="sxs-lookup"><span data-stu-id="cdbb5-120">Element</span></span>|<span data-ttu-id="cdbb5-121">説明</span><span class="sxs-lookup"><span data-stu-id="cdbb5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdbb5-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="cdbb5-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="cdbb5-123">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="cdbb5-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdbb5-124">コメント</span><span class="sxs-lookup"><span data-stu-id="cdbb5-124">Remarks</span></span>  
 <span data-ttu-id="cdbb5-125">この構成要素を使用して、セキュリティ コンテキスト トークン (SCT) クッキーのシリアル化のための既知のクレームの種類のリストと、クッキーの情報をエンコードしてセキュリティで保護するためのエンコーダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="cdbb5-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="cdbb5-126">SCT の詳細については、「<xref:System.ServiceModel.Security.SecureConversationServiceCredential>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdbb5-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbb5-127">参照</span><span class="sxs-lookup"><span data-stu-id="cdbb5-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
