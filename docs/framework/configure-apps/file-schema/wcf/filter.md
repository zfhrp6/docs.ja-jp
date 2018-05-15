---
title: '&lt;フィルター&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 93d47fc6b25a75eedae43cd70582abc863a74e6c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt"></a><span data-ttu-id="31cc9-102">&lt;フィルター&gt;</span><span class="sxs-lookup"><span data-stu-id="31cc9-102">&lt;filter&gt;</span></span>

<span data-ttu-id="31cc9-103">Windows Communication Foundation (WCF) の型を決定するルーティング フィルター定義<xref:System.ServiceModel.Dispatcher.MessageFilter>も任意のサポート データまたはフィルターに必要なパラメーターとして、受信メッセージを評価するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="31cc9-103">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="31cc9-104">\<system.serviceModel >\<ルーティング >\<フィルター >\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="31cc9-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="31cc9-105">構文</span><span class="sxs-lookup"><span data-stu-id="31cc9-105">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="31cc9-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="31cc9-106">Attributes and elements</span></span>

<span data-ttu-id="31cc9-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="31cc9-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="31cc9-108">属性</span><span class="sxs-lookup"><span data-stu-id="31cc9-108">Attributes</span></span>

| <span data-ttu-id="31cc9-109">属性</span><span class="sxs-lookup"><span data-stu-id="31cc9-109">Attribute</span></span>  | <span data-ttu-id="31cc9-110">説明</span><span class="sxs-lookup"><span data-stu-id="31cc9-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="31cc9-111">customType</span><span class="sxs-lookup"><span data-stu-id="31cc9-111">customType</span></span> | <span data-ttu-id="31cc9-112">フィルターとして使用されるカスタム型の完全修飾型名を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="31cc9-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="31cc9-113">場合`filterType`に設定されている`custom`、この属性には作成するクラスの完全修飾型名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="31cc9-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="31cc9-114">`filterData` カスタム型フィルターの評価中に使用される値もあります。</span><span class="sxs-lookup"><span data-stu-id="31cc9-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="31cc9-115">filterData</span><span class="sxs-lookup"><span data-stu-id="31cc9-115">filterData</span></span> | <span data-ttu-id="31cc9-116">フィルター データを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="31cc9-116">A string containing the filter data.</span></span> <span data-ttu-id="31cc9-117">この属性を指定する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31cc9-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="31cc9-118">filterType</span><span class="sxs-lookup"><span data-stu-id="31cc9-118">filterType</span></span> | <span data-ttu-id="31cc9-119">フィルターの種類を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="31cc9-119">A string containing the filter type.</span></span> <span data-ttu-id="31cc9-120">この属性は <xref:System.ServiceModel.Routing.Configuration.FilterType> 型です。</span><span class="sxs-lookup"><span data-stu-id="31cc9-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="31cc9-121">`filterData` 属性を使用する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31cc9-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="31cc9-122">name</span><span class="sxs-lookup"><span data-stu-id="31cc9-122">name</span></span>       | <span data-ttu-id="31cc9-123">フィルター要素の一意の名前を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="31cc9-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="31cc9-124">子要素</span><span class="sxs-lookup"><span data-stu-id="31cc9-124">Child elements</span></span>

<span data-ttu-id="31cc9-125">なし。</span><span class="sxs-lookup"><span data-stu-id="31cc9-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31cc9-126">親要素</span><span class="sxs-lookup"><span data-stu-id="31cc9-126">Parent elements</span></span>

| <span data-ttu-id="31cc9-127">要素</span><span class="sxs-lookup"><span data-stu-id="31cc9-127">Element</span></span> | <span data-ttu-id="31cc9-128">説明</span><span class="sxs-lookup"><span data-stu-id="31cc9-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="31cc9-129">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="31cc9-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="31cc9-130">Windows Communication Foundation (WCF) の種類を決定するルーティング フィルター セットを定義するための構成セクション<xref:System.ServiceModel.Dispatcher.MessageFilter>着信メッセージを評価するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="31cc9-130">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="31cc9-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="31cc9-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
