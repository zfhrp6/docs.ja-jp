---
title: '&lt;ルーティング&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 1771d8a2603a8f61af6ba6e2acf6243d2fd073f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltroutinggt"></a><span data-ttu-id="edada-102">&lt;ルーティング&gt;</span><span class="sxs-lookup"><span data-stu-id="edada-102">&lt;routing&gt;</span></span>

<span data-ttu-id="edada-103">Windows Communication Foundation (WCF) の種類を決定するルーティング フィルター セットを定義する構成セクションを表します<xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージの評価とルーティング テーブルをするターゲット エンドポイントを定義するときに使用されます。フィルターに一致する場合にメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="edada-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="edada-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="edada-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="edada-105">&nbsp;&nbsp;**\<ルーティング >**</span><span class="sxs-lookup"><span data-stu-id="edada-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="edada-106">構文</span><span class="sxs-lookup"><span data-stu-id="edada-106">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String" 
               filterName="String" 
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="edada-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="edada-107">Attributes and elements</span></span>

<span data-ttu-id="edada-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="edada-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="edada-109">属性</span><span class="sxs-lookup"><span data-stu-id="edada-109">Attributes</span></span>

<span data-ttu-id="edada-110">なし</span><span class="sxs-lookup"><span data-stu-id="edada-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="edada-111">子要素</span><span class="sxs-lookup"><span data-stu-id="edada-111">Child elements</span></span>

|     | <span data-ttu-id="edada-112">説明</span><span class="sxs-lookup"><span data-stu-id="edada-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="edada-113">**\<フィルター >**</span><span class="sxs-lookup"><span data-stu-id="edada-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="edada-114">受信メッセージを評価するときに使用する Windows Communication Foundation (WCF) MessageFilter の種類を決定するルーティング フィルター セットを格納します。</span><span class="sxs-lookup"><span data-stu-id="edada-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="edada-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="edada-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="edada-116">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納します。フィルターが一致したときにエンドポイントを指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="edada-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="edada-117">親要素</span><span class="sxs-lookup"><span data-stu-id="edada-117">Parent elements</span></span>

|     | <span data-ttu-id="edada-118">説明</span><span class="sxs-lookup"><span data-stu-id="edada-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="edada-119">**\<システムです。ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="edada-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="edada-120">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="edada-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="edada-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="edada-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
