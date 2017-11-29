---
title: "&lt;routing&gt; の &lt;filters&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9dddd9f9ba5f4c2cea7e92c666e8d224ccf21cee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="ee42d-102">&lt;routing&gt; の &lt;filters&gt;</span><span class="sxs-lookup"><span data-stu-id="ee42d-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="ee42d-103">受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を指定するルーティング フィルター セットを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="ee42d-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="ee42d-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ee42d-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="ee42d-105">&nbsp;&nbsp;[**\<ルーティング >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="ee42d-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="ee42d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<フィルター >**</span><span class="sxs-lookup"><span data-stu-id="ee42d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ee42d-107">構文</span><span class="sxs-lookup"><span data-stu-id="ee42d-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ee42d-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="ee42d-108">Attributes and elements</span></span>

<span data-ttu-id="ee42d-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee42d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ee42d-110">属性</span><span class="sxs-lookup"><span data-stu-id="ee42d-110">Attributes</span></span>

<span data-ttu-id="ee42d-111">なし</span><span class="sxs-lookup"><span data-stu-id="ee42d-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="ee42d-112">子要素</span><span class="sxs-lookup"><span data-stu-id="ee42d-112">Child elements</span></span>

|     | <span data-ttu-id="ee42d-113">説明</span><span class="sxs-lookup"><span data-stu-id="ee42d-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ee42d-114">**\<フィルター >**</span><span class="sxs-lookup"><span data-stu-id="ee42d-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="ee42d-115">受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を定義するルーティング フィルターを格納します。</span><span class="sxs-lookup"><span data-stu-id="ee42d-115">Contains a routing filter that determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="ee42d-116">親要素</span><span class="sxs-lookup"><span data-stu-id="ee42d-116">Parent elements</span></span>

|     | <span data-ttu-id="ee42d-117">説明</span><span class="sxs-lookup"><span data-stu-id="ee42d-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ee42d-118">**\<ルーティング >**</span><span class="sxs-lookup"><span data-stu-id="ee42d-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="ee42d-119">受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を定義するルーティング フィルター セットと、フィルターが一致するときにメッセージを送信するターゲット エンドポイントを指定するルーティング テーブルを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="ee42d-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ee42d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee42d-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
