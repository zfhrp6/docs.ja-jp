---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5fb89ce5a942db40b07a65f59ddd05ab4cd624aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749596"
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="811dc-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="811dc-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="811dc-103">エラー処理に使用されるバックアップ サービス セットを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="811dc-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="811dc-104">各子要素は、プライマリ エンドポイントに到達できない場合に使用するルーティング サービスを希望するエンドポイントのセットを列挙するバックアップの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="811dc-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="811dc-105">リストの最初のエンドポイントがダウンしていると、ルーティング サービスは自動的にリスト内で次にあるエンドポイントにフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="811dc-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="811dc-106">これにより、クライアント アプリケーションに複雑なパターンの処理方法やサービスの配置場所を示すことなく、アプリケーションの信頼性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="811dc-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="811dc-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="811dc-107">\<system.serviceModel></span></span>  
<span data-ttu-id="811dc-108">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="811dc-108">\<routing></span></span>  
<span data-ttu-id="811dc-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="811dc-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="811dc-110">構文</span><span class="sxs-lookup"><span data-stu-id="811dc-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="811dc-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="811dc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="811dc-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="811dc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="811dc-113">属性</span><span class="sxs-lookup"><span data-stu-id="811dc-113">Attributes</span></span>  
 <span data-ttu-id="811dc-114">なし。</span><span class="sxs-lookup"><span data-stu-id="811dc-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="811dc-115">子要素</span><span class="sxs-lookup"><span data-stu-id="811dc-115">Child Elements</span></span>  
  
|<span data-ttu-id="811dc-116">要素</span><span class="sxs-lookup"><span data-stu-id="811dc-116">Element</span></span>|<span data-ttu-id="811dc-117">説明</span><span class="sxs-lookup"><span data-stu-id="811dc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="811dc-118">\<filter></span><span class="sxs-lookup"><span data-stu-id="811dc-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="811dc-119">プライマリ エンドポイントに到達できない場合に使用するルーティング サービスを希望するエンドポイントの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="811dc-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="811dc-120">である必要があります。</span><span class="sxs-lookup"><span data-stu-id="811dc-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="811dc-121">親要素</span><span class="sxs-lookup"><span data-stu-id="811dc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="811dc-122">要素</span><span class="sxs-lookup"><span data-stu-id="811dc-122">Element</span></span>|<span data-ttu-id="811dc-123">説明</span><span class="sxs-lookup"><span data-stu-id="811dc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="811dc-124">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="811dc-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="811dc-125">Windows Communication Foundation (WCF) の種類を決定するルーティング フィルター セットを定義する構成セクションを表します<xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージの評価とルーティング テーブルをするターゲット エンドポイントを定義するときに使用されます。フィルターに一致する場合にメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="811dc-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="811dc-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="811dc-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
