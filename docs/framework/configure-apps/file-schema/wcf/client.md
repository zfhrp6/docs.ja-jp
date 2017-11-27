---
title: "&lt;クライアント&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67f91f4462fc8c11b1769d5805a4ad1407385a50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientgt"></a><span data-ttu-id="f4416-102">&lt;クライアント&gt;</span><span class="sxs-lookup"><span data-stu-id="f4416-102">&lt;client&gt;</span></span>
<span data-ttu-id="f4416-103">`client` 要素は、クライアントが接続可能なエンドポイントの一覧を定義します。</span><span class="sxs-lookup"><span data-stu-id="f4416-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="f4416-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f4416-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f4416-105">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="f4416-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4416-106">構文</span><span class="sxs-lookup"><span data-stu-id="f4416-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <endpoint>  
        </endpoint>  
                <metadata>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4416-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f4416-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f4416-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4416-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4416-109">属性</span><span class="sxs-lookup"><span data-stu-id="f4416-109">Attributes</span></span>  
 <span data-ttu-id="f4416-110">なし</span><span class="sxs-lookup"><span data-stu-id="f4416-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4416-111">子要素</span><span class="sxs-lookup"><span data-stu-id="f4416-111">Child Elements</span></span>  
  
|<span data-ttu-id="f4416-112">要素</span><span class="sxs-lookup"><span data-stu-id="f4416-112">Element</span></span>|<span data-ttu-id="f4416-113">説明</span><span class="sxs-lookup"><span data-stu-id="f4416-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4416-114">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="f4416-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="f4416-115">このクライアントが接続可能なエンドポイントを指定するエンドポイント要素のコレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="f4416-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="f4416-116">\<メタデータ ></span><span class="sxs-lookup"><span data-stu-id="f4416-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="f4416-117">メタデータを処理するための設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="f4416-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4416-118">親要素</span><span class="sxs-lookup"><span data-stu-id="f4416-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f4416-119">要素</span><span class="sxs-lookup"><span data-stu-id="f4416-119">Element</span></span>|<span data-ttu-id="f4416-120">説明</span><span class="sxs-lookup"><span data-stu-id="f4416-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4416-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f4416-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="f4416-122">すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="f4416-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4416-123">コメント</span><span class="sxs-lookup"><span data-stu-id="f4416-123">Remarks</span></span>  
 <span data-ttu-id="f4416-124">`client` セクションは、クライアントが接続可能なエンドポイントの一覧を定義します。</span><span class="sxs-lookup"><span data-stu-id="f4416-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="f4416-125">クライアント セクションに示される各エンドポイントは、独自のバインディング、動作、およびコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="f4416-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="f4416-126">各エンドポイントは、`name` 属性と `contract` 属性の組み合わせで一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="f4416-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="f4416-127">クライアント コードは、クライアントが実装するサービスのエンドポイントに接続するための `name` を指定します。</span><span class="sxs-lookup"><span data-stu-id="f4416-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="f4416-128">`name` 属性が省略されている場合、クライアントが実装するコントラクトのエンドポイントが既定のエンドポイントとして機能します。</span><span class="sxs-lookup"><span data-stu-id="f4416-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="f4416-129">さらに、このセクションはメタデータを処理するための設定も指定します。</span><span class="sxs-lookup"><span data-stu-id="f4416-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4416-130">例</span><span class="sxs-lookup"><span data-stu-id="f4416-130">Example</span></span>  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4416-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4416-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="f4416-132">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="f4416-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="f4416-133">クライアント</span><span class="sxs-lookup"><span data-stu-id="f4416-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
