---
title: '&lt;header&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 7683b07093719cda6b210a4174d47e5785d4644d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747152"
---
# <a name="ltheadersgt"></a><span data-ttu-id="3f210-102">&lt;header&gt;</span><span class="sxs-lookup"><span data-stu-id="3f210-102">&lt;headers&gt;</span></span>
<span data-ttu-id="3f210-103">エンドポイントは、基本となる URI だけでなく、1 つ以上の SOAP ヘッダーによってアドレス指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f210-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="3f210-104">これが役に立つのは、エンドポイントのクライアントに中継局を指す SOAP ヘッダーを含める必要がある、SOAP 中継局のシナリオの場合です。</span><span class="sxs-lookup"><span data-stu-id="3f210-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="3f210-105">この構成要素を使用して、カスタムのアドレス ヘッダーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="3f210-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="3f210-106">エンドポイント ヘッダー コレクション内のエントリは、ユーザー定義の XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="3f210-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="3f210-107">各要素は、正しい形式の XML である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f210-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="3f210-108">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3f210-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="3f210-109">\<client></span><span class="sxs-lookup"><span data-stu-id="3f210-109">\<client></span></span>  
<span data-ttu-id="3f210-110">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="3f210-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f210-111">構文</span><span class="sxs-lookup"><span data-stu-id="3f210-111">Syntax</span></span>  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f210-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3f210-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3f210-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f210-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f210-114">属性</span><span class="sxs-lookup"><span data-stu-id="3f210-114">Attributes</span></span>  
 <span data-ttu-id="3f210-115">なし。</span><span class="sxs-lookup"><span data-stu-id="3f210-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f210-116">子要素</span><span class="sxs-lookup"><span data-stu-id="3f210-116">Child Elements</span></span>  
  
|<span data-ttu-id="3f210-117">要素</span><span class="sxs-lookup"><span data-stu-id="3f210-117">Element</span></span>|<span data-ttu-id="3f210-118">説明</span><span class="sxs-lookup"><span data-stu-id="3f210-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f210-119">Region</span><span class="sxs-lookup"><span data-stu-id="3f210-119">Region</span></span>||  
|<span data-ttu-id="3f210-120">メンバー</span><span class="sxs-lookup"><span data-stu-id="3f210-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="3f210-121">親要素</span><span class="sxs-lookup"><span data-stu-id="3f210-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3f210-122">要素</span><span class="sxs-lookup"><span data-stu-id="3f210-122">Element</span></span>|<span data-ttu-id="3f210-123">説明</span><span class="sxs-lookup"><span data-stu-id="3f210-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f210-124">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="3f210-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="3f210-125">さまざまなタイプのエンドポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="3f210-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f210-126">コメント</span><span class="sxs-lookup"><span data-stu-id="3f210-126">Remarks</span></span>  
 <span data-ttu-id="3f210-127">オプション ヘッダーは、エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3f210-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="3f210-128">たとえば、ヘッダーを使用して、受信メッセージの処理方法や、エンドポイントからの応答メッセージの送信先を指定できるほか、複数のサービス インスタンスが使用できる場合に、特定ユーザーからの受信メッセージの処理に使用するインスタンスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3f210-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f210-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f210-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="3f210-130">エンドポイント : アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="3f210-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
