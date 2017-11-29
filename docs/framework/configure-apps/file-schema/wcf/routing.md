---
title: "&lt;ルーティング&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed2dd4e68584d6e79e18fc9b61fcc8f078615dac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltroutinggt"></a><span data-ttu-id="b0e93-102">&lt;ルーティング&gt;</span><span class="sxs-lookup"><span data-stu-id="b0e93-102">&lt;routing&gt;</span></span>

<span data-ttu-id="b0e93-103">受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を定義するルーティング フィルター セットと、フィルターが一致するときにメッセージを送信するターゲット エンドポイントを指定するルーティング テーブルを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="b0e93-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="b0e93-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b0e93-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="b0e93-105">&nbsp;&nbsp;**\<ルーティング >**</span><span class="sxs-lookup"><span data-stu-id="b0e93-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b0e93-106">構文</span><span class="sxs-lookup"><span data-stu-id="b0e93-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b0e93-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="b0e93-107">Attributes and elements</span></span>

<span data-ttu-id="b0e93-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b0e93-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b0e93-109">属性</span><span class="sxs-lookup"><span data-stu-id="b0e93-109">Attributes</span></span>

<span data-ttu-id="b0e93-110">なし</span><span class="sxs-lookup"><span data-stu-id="b0e93-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b0e93-111">子要素</span><span class="sxs-lookup"><span data-stu-id="b0e93-111">Child elements</span></span>

|     | <span data-ttu-id="b0e93-112">説明</span><span class="sxs-lookup"><span data-stu-id="b0e93-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b0e93-113">**\<フィルター >**</span><span class="sxs-lookup"><span data-stu-id="b0e93-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="b0e93-114">受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter の種類を定義するルーティング フィルター セットを格納します。</span><span class="sxs-lookup"><span data-stu-id="b0e93-114">Contains a set of routing filters that determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="b0e93-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="b0e93-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="b0e93-116">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納します。フィルターが一致したときにエンドポイントを指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b0e93-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="b0e93-117">親要素</span><span class="sxs-lookup"><span data-stu-id="b0e93-117">Parent elements</span></span>

|     | <span data-ttu-id="b0e93-118">説明</span><span class="sxs-lookup"><span data-stu-id="b0e93-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="b0e93-119">**\<システムです。ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="b0e93-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="b0e93-120">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="b0e93-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="b0e93-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0e93-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
