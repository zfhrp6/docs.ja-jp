---
title: '&lt;routing&gt; の &lt;filters&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 9f0fa9bf51d264346738172f57a8efca7950fdb7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753116"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="8fb6d-102">&lt;routing&gt; の &lt;filters&gt;</span><span class="sxs-lookup"><span data-stu-id="8fb6d-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="8fb6d-103">Windows Communication Foundation (WCF) の種類を決定するルーティング フィルター セットを定義する構成セクションを表します<xref:System.ServiceModel.Dispatcher.MessageFilter>着信メッセージを評価するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="8fb6d-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="8fb6d-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="8fb6d-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="8fb6d-105">&nbsp;&nbsp;[**\<ルーティング >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="8fb6d-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="8fb6d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<フィルター >**</span><span class="sxs-lookup"><span data-stu-id="8fb6d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8fb6d-107">構文</span><span class="sxs-lookup"><span data-stu-id="8fb6d-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="8fb6d-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="8fb6d-108">Attributes and elements</span></span>

<span data-ttu-id="8fb6d-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8fb6d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8fb6d-110">属性</span><span class="sxs-lookup"><span data-stu-id="8fb6d-110">Attributes</span></span>

<span data-ttu-id="8fb6d-111">なし</span><span class="sxs-lookup"><span data-stu-id="8fb6d-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="8fb6d-112">子要素</span><span class="sxs-lookup"><span data-stu-id="8fb6d-112">Child elements</span></span>

|     | <span data-ttu-id="8fb6d-113">説明</span><span class="sxs-lookup"><span data-stu-id="8fb6d-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8fb6d-114">**\<フィルター >**</span><span class="sxs-lookup"><span data-stu-id="8fb6d-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="8fb6d-115">Windows Communication Foundation (WCF) の種類を決定するルーティング フィルターを含む<xref:System.ServiceModel.Dispatcher.MessageFilter>は着信メッセージを評価する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="8fb6d-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="8fb6d-116">親要素</span><span class="sxs-lookup"><span data-stu-id="8fb6d-116">Parent elements</span></span>

|     | <span data-ttu-id="8fb6d-117">説明</span><span class="sxs-lookup"><span data-stu-id="8fb6d-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8fb6d-118">**\<ルーティング >**</span><span class="sxs-lookup"><span data-stu-id="8fb6d-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="8fb6d-119">Windows Communication Foundation (WCF) の種類を決定するルーティング フィルター セットを定義する構成セクションを表します<xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージの評価とルーティング テーブルをするターゲット エンドポイントを定義するときに使用されます。フィルターに一致する場合にメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="8fb6d-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="8fb6d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fb6d-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
