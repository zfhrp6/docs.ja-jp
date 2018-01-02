---
title: '&lt;backupList&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00a4c84ee5c9a833cc789c8871df79a3886fa0e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbackuplistgt"></a><span data-ttu-id="1eccf-102">&lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="1eccf-102">&lt;backupList&gt;</span></span>
<span data-ttu-id="1eccf-103">プライマリ エンドポイントに到達できない場合に使用するルーティング サービスを希望するエンドポイントのセットを列挙したバックアップ リストを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="1eccf-103">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="1eccf-104">リストの最初のエンドポイントがダウンしていると、ルーティング サービスは自動的にリスト内で次にあるエンドポイントにフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="1eccf-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="1eccf-105">これにより、クライアント アプリケーションに複雑なパターンの処理方法やサービスの配置場所を示すことなく、アプリケーションの信頼性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="1eccf-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="1eccf-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1eccf-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1eccf-107">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="1eccf-107">\<routing></span></span>  
<span data-ttu-id="1eccf-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="1eccf-108">\<backupLists></span></span>  
<span data-ttu-id="1eccf-109">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="1eccf-109">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eccf-110">構文</span><span class="sxs-lookup"><span data-stu-id="1eccf-110">Syntax</span></span>  
  
```xml 
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1eccf-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1eccf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1eccf-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1eccf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1eccf-113">属性</span><span class="sxs-lookup"><span data-stu-id="1eccf-113">Attributes</span></span>  
  
|<span data-ttu-id="1eccf-114">属性</span><span class="sxs-lookup"><span data-stu-id="1eccf-114">Attribute</span></span>|<span data-ttu-id="1eccf-115">説明</span><span class="sxs-lookup"><span data-stu-id="1eccf-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1eccf-116">name</span><span class="sxs-lookup"><span data-stu-id="1eccf-116">name</span></span>|<span data-ttu-id="1eccf-117">このエンドポイント リストを指定するために使用される名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="1eccf-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1eccf-118">子要素</span><span class="sxs-lookup"><span data-stu-id="1eccf-118">Child Elements</span></span>  
  
|<span data-ttu-id="1eccf-119">要素</span><span class="sxs-lookup"><span data-stu-id="1eccf-119">Element</span></span>|<span data-ttu-id="1eccf-120">説明</span><span class="sxs-lookup"><span data-stu-id="1eccf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1eccf-121">\<filter></span><span class="sxs-lookup"><span data-stu-id="1eccf-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="1eccf-122">親要素</span><span class="sxs-lookup"><span data-stu-id="1eccf-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1eccf-123">要素</span><span class="sxs-lookup"><span data-stu-id="1eccf-123">Element</span></span>|<span data-ttu-id="1eccf-124">説明</span><span class="sxs-lookup"><span data-stu-id="1eccf-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1eccf-125">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="1eccf-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1eccf-126">バックアップ エンドポイントの一覧。</span><span class="sxs-lookup"><span data-stu-id="1eccf-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eccf-127">コメント</span><span class="sxs-lookup"><span data-stu-id="1eccf-127">Remarks</span></span>  
 <span data-ttu-id="1eccf-128">このセクションには、プライマリ エンドポイントへの送信時に通信例外が発生した場合にメッセージが送信されるエンドポイントの、順序付けられたコレクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1eccf-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="1eccf-129">プライマリ エンドポイントへの送信に示されている場合、`endpointName`の属性[\<追加 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md)通信例外によって失敗する、ルーティング サービスを試みますこの最初のエンドポイントにメッセージを送信するには構成セクション。</span><span class="sxs-lookup"><span data-stu-id="1eccf-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="1eccf-130">これも通信例外によって失敗した場合、ルーティング サービスは、送信に成功するか、通信例外以外のエラーを返すか、コレクション内のすべてのエンドポイントがエラーを返すまで、このセクションに格納された次のエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="1eccf-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="1eccf-131">次の例では、"Destination"という名前のプライマリ エンドポイントへの送信には、通信例外が返された場合、サービスは"alternateServiceQueue"にメッセージを送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="1eccf-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="1eccf-132">この試行でも通信例外が返された場合、ルーティング サービスはコレクション内の次のエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="1eccf-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1eccf-133">参照</span><span class="sxs-lookup"><span data-stu-id="1eccf-133">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
