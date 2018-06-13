---
title: '&lt;rsa&gt;'
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dbeb08e6475d4825ad442b0b264e9003bb6fc53d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749931"
---
# <a name="ltrsagt"></a><span data-ttu-id="85762-102">&lt;rsa&gt;</span><span class="sxs-lookup"><span data-stu-id="85762-102">&lt;rsa&gt;</span></span>
<span data-ttu-id="85762-103">この ID のエンドポイントに接続するセキュリティで保護された WCF クライアントは、サーバーから提示されたクレームに、この ID を構築するために使用された RSA 公開キーを含むクレームが含まれていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="85762-103">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="85762-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="85762-104">\<identity></span></span>  
<span data-ttu-id="85762-105">\<rsa ></span><span class="sxs-lookup"><span data-stu-id="85762-105">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85762-106">構文</span><span class="sxs-lookup"><span data-stu-id="85762-106">Syntax</span></span>  
  
```xml  
<rsa value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85762-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="85762-107">Attributes and Elements</span></span>  
 <span data-ttu-id="85762-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="85762-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85762-109">属性</span><span class="sxs-lookup"><span data-stu-id="85762-109">Attributes</span></span>  
  
|<span data-ttu-id="85762-110">属性</span><span class="sxs-lookup"><span data-stu-id="85762-110">Attribute</span></span>|<span data-ttu-id="85762-111">説明</span><span class="sxs-lookup"><span data-stu-id="85762-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85762-112">value</span><span class="sxs-lookup"><span data-stu-id="85762-112">value</span></span>|<span data-ttu-id="85762-113">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="85762-113">Optional String.</span></span> <span data-ttu-id="85762-114">クライアントで比較される RSA 公開キー値。</span><span class="sxs-lookup"><span data-stu-id="85762-114">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85762-115">子要素</span><span class="sxs-lookup"><span data-stu-id="85762-115">Child Elements</span></span>  
 <span data-ttu-id="85762-116">なし</span><span class="sxs-lookup"><span data-stu-id="85762-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85762-117">親要素</span><span class="sxs-lookup"><span data-stu-id="85762-117">Parent Elements</span></span>  
  
|<span data-ttu-id="85762-118">要素</span><span class="sxs-lookup"><span data-stu-id="85762-118">Element</span></span>|<span data-ttu-id="85762-119">説明</span><span class="sxs-lookup"><span data-stu-id="85762-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85762-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="85762-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="85762-121">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="85762-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85762-122">コメント</span><span class="sxs-lookup"><span data-stu-id="85762-122">Remarks</span></span>  
 <span data-ttu-id="85762-123">RSA チェックを行うと、その RSA キーまたは生成された独自の RSA キー値に基づいて、単一の証明書の認証を明確に制限できます。</span><span class="sxs-lookup"><span data-stu-id="85762-123">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="85762-124">これにより、RSA キーが変更された場合に既存のクライアントで使用できなくなるサービスを犠牲にして、特定の RSA キーをより厳しく認証できます。</span><span class="sxs-lookup"><span data-stu-id="85762-124">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="85762-125">詳細については、クライアントにサービスを検証する id を使用して、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。</span><span class="sxs-lookup"><span data-stu-id="85762-125">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85762-126">例</span><span class="sxs-lookup"><span data-stu-id="85762-126">Example</span></span>  
 <span data-ttu-id="85762-127">次の構成コードは、サーバーの認証に使用される X.509 証明書の公開キー値を指定します。</span><span class="sxs-lookup"><span data-stu-id="85762-127">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <rsa value = "0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"/>  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85762-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="85762-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [<span data-ttu-id="85762-129">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="85762-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="85762-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="85762-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
