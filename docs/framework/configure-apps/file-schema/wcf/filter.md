---
title: "&lt;フィルター&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 186c511cd8a69cef5e30e369641628a10a0972d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt"></a><span data-ttu-id="f78ec-102">&lt;フィルター&gt;</span><span class="sxs-lookup"><span data-stu-id="f78ec-102">&lt;filter&gt;</span></span>

<span data-ttu-id="f78ec-103">受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> の種類と、フィルターが必要とする任意のサポート対象のデータまたはパラメーターを指定するルーティング フィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="f78ec-103">Defines a routing filter, which determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="f78ec-104">\<system.serviceModel >\<ルーティング >\<フィルター >\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="f78ec-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="f78ec-105">構文</span><span class="sxs-lookup"><span data-stu-id="f78ec-105">Syntax</span></span>

```xml
<routing>
  <filters>
    <filter customType="String" 
            filterData="String" 
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
            name="String" />
  </filters>
</routing>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f78ec-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="f78ec-106">Attributes and elements</span></span>

<span data-ttu-id="f78ec-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f78ec-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f78ec-108">属性</span><span class="sxs-lookup"><span data-stu-id="f78ec-108">Attributes</span></span>

| <span data-ttu-id="f78ec-109">属性</span><span class="sxs-lookup"><span data-stu-id="f78ec-109">Attribute</span></span>  | <span data-ttu-id="f78ec-110">説明</span><span class="sxs-lookup"><span data-stu-id="f78ec-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="f78ec-111">customType</span><span class="sxs-lookup"><span data-stu-id="f78ec-111">customType</span></span> | <span data-ttu-id="f78ec-112">フィルターとして使用されるカスタム型の完全修飾型名を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="f78ec-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="f78ec-113">場合`filterType`に設定されている`custom`、この属性には作成するクラスの完全修飾型名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f78ec-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="f78ec-114">`filterData`カスタム型フィルターの評価中に使用される値もあります。</span><span class="sxs-lookup"><span data-stu-id="f78ec-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="f78ec-115">filterData</span><span class="sxs-lookup"><span data-stu-id="f78ec-115">filterData</span></span> | <span data-ttu-id="f78ec-116">フィルター データを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="f78ec-116">A string containing the filter data.</span></span> <span data-ttu-id="f78ec-117">この属性を指定する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f78ec-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f78ec-118">filterType</span><span class="sxs-lookup"><span data-stu-id="f78ec-118">filterType</span></span> | <span data-ttu-id="f78ec-119">フィルターの種類を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="f78ec-119">A string containing the filter type.</span></span> <span data-ttu-id="f78ec-120">この属性は <xref:System.ServiceModel.Routing.Configuration.FilterType> 型です。</span><span class="sxs-lookup"><span data-stu-id="f78ec-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="f78ec-121">`filterData` 属性を使用する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f78ec-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f78ec-122">name</span><span class="sxs-lookup"><span data-stu-id="f78ec-122">name</span></span>       | <span data-ttu-id="f78ec-123">フィルター要素の一意の名前を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="f78ec-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f78ec-124">子要素</span><span class="sxs-lookup"><span data-stu-id="f78ec-124">Child elements</span></span>

<span data-ttu-id="f78ec-125">なし。</span><span class="sxs-lookup"><span data-stu-id="f78ec-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f78ec-126">親要素</span><span class="sxs-lookup"><span data-stu-id="f78ec-126">Parent elements</span></span>

| <span data-ttu-id="f78ec-127">要素</span><span class="sxs-lookup"><span data-stu-id="f78ec-127">Element</span></span> | <span data-ttu-id="f78ec-128">説明</span><span class="sxs-lookup"><span data-stu-id="f78ec-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="f78ec-129">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="f78ec-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="f78ec-130">受信メッセージの評価に使用される [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を指定するルーティング フィルター セットを定義する構成セクション。</span><span class="sxs-lookup"><span data-stu-id="f78ec-130">A configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f78ec-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f78ec-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
