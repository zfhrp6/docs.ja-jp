---
title: '&lt;backupLists&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fee9e455189d5be1c81fb950eff3882aa8222b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="9b2ad-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="9b2ad-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="9b2ad-103">エラー処理に使用されるバックアップ サービス セットを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="9b2ad-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="9b2ad-104">各子要素は、プライマリ エンドポイントに到達できない場合に使用するルーティング サービスを希望するエンドポイントのセットを列挙するバックアップの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9b2ad-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="9b2ad-105">リストの最初のエンドポイントがダウンしていると、ルーティング サービスは自動的にリスト内で次にあるエンドポイントにフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="9b2ad-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="9b2ad-106">これにより、クライアント アプリケーションに複雑なパターンの処理方法やサービスの配置場所を示すことなく、アプリケーションの信頼性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="9b2ad-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="9b2ad-107">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9b2ad-107">\<system.serviceModel></span></span>  
<span data-ttu-id="9b2ad-108">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="9b2ad-108">\<routing></span></span>  
<span data-ttu-id="9b2ad-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="9b2ad-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b2ad-110">構文</span><span class="sxs-lookup"><span data-stu-id="9b2ad-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b2ad-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9b2ad-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9b2ad-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b2ad-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b2ad-113">属性</span><span class="sxs-lookup"><span data-stu-id="9b2ad-113">Attributes</span></span>  
 <span data-ttu-id="9b2ad-114">なし。</span><span class="sxs-lookup"><span data-stu-id="9b2ad-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b2ad-115">子要素</span><span class="sxs-lookup"><span data-stu-id="9b2ad-115">Child Elements</span></span>  
  
|<span data-ttu-id="9b2ad-116">要素</span><span class="sxs-lookup"><span data-stu-id="9b2ad-116">Element</span></span>|<span data-ttu-id="9b2ad-117">説明</span><span class="sxs-lookup"><span data-stu-id="9b2ad-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b2ad-118">\<filter></span><span class="sxs-lookup"><span data-stu-id="9b2ad-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="9b2ad-119">プライマリ エンドポイントに到達できない場合に使用するルーティング サービスを希望するエンドポイントの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9b2ad-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="9b2ad-120">である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b2ad-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b2ad-121">親要素</span><span class="sxs-lookup"><span data-stu-id="9b2ad-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9b2ad-122">要素</span><span class="sxs-lookup"><span data-stu-id="9b2ad-122">Element</span></span>|<span data-ttu-id="9b2ad-123">説明</span><span class="sxs-lookup"><span data-stu-id="9b2ad-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b2ad-124">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="9b2ad-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="9b2ad-125">受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を定義するルーティング フィルター セットと、フィルターが一致するときにメッセージを送信するターゲット エンドポイントを指定するルーティング テーブルを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="9b2ad-125">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b2ad-126">参照</span><span class="sxs-lookup"><span data-stu-id="9b2ad-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
