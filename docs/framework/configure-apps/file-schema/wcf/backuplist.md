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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9f8138f2a2448293e1f26da5f7d0562b1338b7d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltbackuplistgt"></a><span data-ttu-id="b88ec-102">&lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="b88ec-102">&lt;backupList&gt;</span></span>
<span data-ttu-id="b88ec-103">プライマリ エンドポイントに到達できない場合に使用するルーティング サービスを希望するエンドポイントのセットを列挙したバックアップ リストを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="b88ec-103">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="b88ec-104">リストの最初のエンドポイントがダウンしていると、ルーティング サービスは自動的にリスト内で次にあるエンドポイントにフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="b88ec-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="b88ec-105">これにより、クライアント アプリケーションに複雑なパターンの処理方法やサービスの配置場所を示すことなく、アプリケーションの信頼性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="b88ec-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="b88ec-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b88ec-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b88ec-107">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="b88ec-107">\<routing></span></span>  
<span data-ttu-id="b88ec-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="b88ec-108">\<backupLists></span></span>  
<span data-ttu-id="b88ec-109">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="b88ec-109">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b88ec-110">構文</span><span class="sxs-lookup"><span data-stu-id="b88ec-110">Syntax</span></span>  
  
```xml 
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b88ec-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b88ec-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b88ec-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b88ec-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b88ec-113">属性</span><span class="sxs-lookup"><span data-stu-id="b88ec-113">Attributes</span></span>  
  
|<span data-ttu-id="b88ec-114">属性</span><span class="sxs-lookup"><span data-stu-id="b88ec-114">Attribute</span></span>|<span data-ttu-id="b88ec-115">説明</span><span class="sxs-lookup"><span data-stu-id="b88ec-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b88ec-116">name</span><span class="sxs-lookup"><span data-stu-id="b88ec-116">name</span></span>|<span data-ttu-id="b88ec-117">このエンドポイント リストを指定するために使用される名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b88ec-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b88ec-118">子要素</span><span class="sxs-lookup"><span data-stu-id="b88ec-118">Child Elements</span></span>  
  
|<span data-ttu-id="b88ec-119">要素</span><span class="sxs-lookup"><span data-stu-id="b88ec-119">Element</span></span>|<span data-ttu-id="b88ec-120">説明</span><span class="sxs-lookup"><span data-stu-id="b88ec-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b88ec-121">\<filter></span><span class="sxs-lookup"><span data-stu-id="b88ec-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="b88ec-122">親要素</span><span class="sxs-lookup"><span data-stu-id="b88ec-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b88ec-123">要素</span><span class="sxs-lookup"><span data-stu-id="b88ec-123">Element</span></span>|<span data-ttu-id="b88ec-124">説明</span><span class="sxs-lookup"><span data-stu-id="b88ec-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b88ec-125">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="b88ec-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="b88ec-126">バックアップ エンドポイントの一覧。</span><span class="sxs-lookup"><span data-stu-id="b88ec-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b88ec-127">コメント</span><span class="sxs-lookup"><span data-stu-id="b88ec-127">Remarks</span></span>  
 <span data-ttu-id="b88ec-128">このセクションには、プライマリ エンドポイントへの送信時に通信例外が発生した場合にメッセージが送信されるエンドポイントの、順序付けられたコレクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b88ec-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="b88ec-129">プライマリ エンドポイントへの送信に示されている場合、`endpointName`の属性[\<追加 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md)通信例外によって失敗する、ルーティング サービスを試みますこの最初のエンドポイントにメッセージを送信するには構成セクション。</span><span class="sxs-lookup"><span data-stu-id="b88ec-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="b88ec-130">これも通信例外によって失敗した場合、ルーティング サービスは、送信に成功するか、通信例外以外のエラーを返すか、コレクション内のすべてのエンドポイントがエラーを返すまで、このセクションに格納された次のエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="b88ec-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="b88ec-131">次の例では、"Destination"という名前のプライマリ エンドポイントへの送信には、通信例外が返された場合、サービスは"alternateServiceQueue"にメッセージを送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="b88ec-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="b88ec-132">この試行でも通信例外が返された場合、ルーティング サービスはコレクション内の次のエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="b88ec-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b88ec-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="b88ec-133">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
