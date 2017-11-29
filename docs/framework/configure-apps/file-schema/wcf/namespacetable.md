---
title: '&lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 470dd2dcc2e8554bb89eec159c6b96b24795c5d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="cfac9-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="cfac9-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="cfac9-103">名前空間とプレフィックスのマッピングを含む要素セットを定義する構成セクションを表します。これは、ルーティングの XPath フィルターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="cfac9-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="cfac9-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="cfac9-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="cfac9-105">&nbsp;&nbsp;**\<ルーティング >** </span><span class="sxs-lookup"><span data-stu-id="cfac9-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="cfac9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="cfac9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cfac9-107">構文</span><span class="sxs-lookup"><span data-stu-id="cfac9-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="cfac9-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="cfac9-108">Attributes and elements</span></span>

<span data-ttu-id="cfac9-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cfac9-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cfac9-110">属性</span><span class="sxs-lookup"><span data-stu-id="cfac9-110">Attributes</span></span>

<span data-ttu-id="cfac9-111">なし</span><span class="sxs-lookup"><span data-stu-id="cfac9-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="cfac9-112">子要素</span><span class="sxs-lookup"><span data-stu-id="cfac9-112">Child elements</span></span>

|     | <span data-ttu-id="cfac9-113">説明</span><span class="sxs-lookup"><span data-stu-id="cfac9-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cfac9-114">**\<フィルター >**</span><span class="sxs-lookup"><span data-stu-id="cfac9-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="cfac9-115">XPath 式に使用される名前空間とプレフィックスのマッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="cfac9-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="cfac9-116">親要素</span><span class="sxs-lookup"><span data-stu-id="cfac9-116">Parent elements</span></span>

|     | <span data-ttu-id="cfac9-117">説明</span><span class="sxs-lookup"><span data-stu-id="cfac9-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cfac9-118">**\<ルーティング >**</span><span class="sxs-lookup"><span data-stu-id="cfac9-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="cfac9-119">受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を定義するルーティング フィルター セットと、フィルターが一致するときにメッセージを送信するターゲット エンドポイントを指定するルーティング テーブルを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="cfac9-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="cfac9-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfac9-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
