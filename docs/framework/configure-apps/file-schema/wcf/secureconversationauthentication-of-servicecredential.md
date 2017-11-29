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
ms.openlocfilehash: 0fb9ff476812b6b889750e8eb7b80efce801f041
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="90638-102">&lt;serviceCredential&gt; の &lt;secureConversationAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="90638-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="90638-103">安全な会話サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="90638-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="90638-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="90638-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="90638-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="90638-105">\<behaviors></span></span>  
<span data-ttu-id="90638-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="90638-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="90638-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="90638-107">\<behavior></span></span>  
<span data-ttu-id="90638-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="90638-108">\<serviceCredentials></span></span>  
<span data-ttu-id="90638-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="90638-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90638-110">構文</span><span class="sxs-lookup"><span data-stu-id="90638-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90638-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="90638-111">Attributes and Elements</span></span>  
 <span data-ttu-id="90638-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="90638-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90638-113">属性</span><span class="sxs-lookup"><span data-stu-id="90638-113">Attributes</span></span>  
  
|<span data-ttu-id="90638-114">属性</span><span class="sxs-lookup"><span data-stu-id="90638-114">Attribute</span></span>|<span data-ttu-id="90638-115">説明</span><span class="sxs-lookup"><span data-stu-id="90638-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="90638-116">使用される <xref:System.ServiceModel.Security.SecurityStateEncoder> の型を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="90638-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90638-117">子要素</span><span class="sxs-lookup"><span data-stu-id="90638-117">Child Elements</span></span>  
 <span data-ttu-id="90638-118">なし。</span><span class="sxs-lookup"><span data-stu-id="90638-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90638-119">親要素</span><span class="sxs-lookup"><span data-stu-id="90638-119">Parent Elements</span></span>  
  
|<span data-ttu-id="90638-120">要素</span><span class="sxs-lookup"><span data-stu-id="90638-120">Element</span></span>|<span data-ttu-id="90638-121">説明</span><span class="sxs-lookup"><span data-stu-id="90638-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90638-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="90638-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="90638-123">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="90638-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90638-124">コメント</span><span class="sxs-lookup"><span data-stu-id="90638-124">Remarks</span></span>  
 <span data-ttu-id="90638-125">この構成要素を使用して、セキュリティ コンテキスト トークン (SCT) クッキーのシリアル化のための既知のクレームの種類のリストと、クッキーの情報をエンコードしてセキュリティで保護するためのエンコーダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="90638-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="90638-126">SCT の詳細については、「<xref:System.ServiceModel.Security.SecureConversationServiceCredential>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90638-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90638-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="90638-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
