---
title: "&lt;ヘッダー&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bcc81c0dd0628a6c5cab93841665b416f18a5bff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltheadersgt"></a><span data-ttu-id="00751-102">&lt;ヘッダー&gt;</span><span class="sxs-lookup"><span data-stu-id="00751-102">&lt;headers&gt;</span></span>
<span data-ttu-id="00751-103">エンドポイントは、基本となる URI だけでなく、1 つ以上の SOAP ヘッダーによってアドレス指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="00751-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="00751-104">これが役に立つのは、エンドポイントのクライアントに中継局を指す SOAP ヘッダーを含める必要がある、SOAP 中継局のシナリオの場合です。</span><span class="sxs-lookup"><span data-stu-id="00751-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="00751-105">この構成要素を使用して、カスタムのアドレス ヘッダーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="00751-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="00751-106">エンドポイント ヘッダー コレクション内のエントリは、ユーザー定義の XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="00751-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="00751-107">各要素は、正しい形式の XML である必要があります。</span><span class="sxs-lookup"><span data-stu-id="00751-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="00751-108">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="00751-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="00751-109">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="00751-109">\<client></span></span>  
<span data-ttu-id="00751-110">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="00751-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00751-111">構文</span><span class="sxs-lookup"><span data-stu-id="00751-111">Syntax</span></span>  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00751-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="00751-112">Attributes and Elements</span></span>  
 <span data-ttu-id="00751-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="00751-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00751-114">属性</span><span class="sxs-lookup"><span data-stu-id="00751-114">Attributes</span></span>  
 <span data-ttu-id="00751-115">なし。</span><span class="sxs-lookup"><span data-stu-id="00751-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="00751-116">子要素</span><span class="sxs-lookup"><span data-stu-id="00751-116">Child Elements</span></span>  
  
|<span data-ttu-id="00751-117">要素</span><span class="sxs-lookup"><span data-stu-id="00751-117">Element</span></span>|<span data-ttu-id="00751-118">説明</span><span class="sxs-lookup"><span data-stu-id="00751-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00751-119">Region</span><span class="sxs-lookup"><span data-stu-id="00751-119">Region</span></span>||  
|<span data-ttu-id="00751-120">メンバー</span><span class="sxs-lookup"><span data-stu-id="00751-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="00751-121">親要素</span><span class="sxs-lookup"><span data-stu-id="00751-121">Parent Elements</span></span>  
  
|<span data-ttu-id="00751-122">要素</span><span class="sxs-lookup"><span data-stu-id="00751-122">Element</span></span>|<span data-ttu-id="00751-123">説明</span><span class="sxs-lookup"><span data-stu-id="00751-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00751-124">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="00751-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="00751-125">さまざまなタイプのエンドポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="00751-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00751-126">コメント</span><span class="sxs-lookup"><span data-stu-id="00751-126">Remarks</span></span>  
 <span data-ttu-id="00751-127">オプション ヘッダーは、エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="00751-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="00751-128">たとえば、ヘッダーを使用して、受信メッセージの処理方法や、エンドポイントからの応答メッセージの送信先を指定できるほか、複数のサービス インスタンスが使用できる場合に、特定ユーザーからの受信メッセージの処理に使用するインスタンスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="00751-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00751-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="00751-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="00751-130">エンドポイント: アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="00751-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
