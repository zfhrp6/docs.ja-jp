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
ms.openlocfilehash: af2095289d5f711733c71238b855c685114d1997
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltergt"></a>&lt;フィルター&gt;

受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> の種類と、フィルターが必要とする任意のサポート対象のデータまたはパラメーターを指定するルーティング フィルターを定義します。

\<system.serviceModel >\<ルーティング >\<フィルター >\<フィルター >

## <a name="syntax"></a>構文

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

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

| 属性  | 説明 |
| ---------- | ----------- |
| customType | フィルターとして使用されるカスタム型の完全修飾型名を示す文字列。 場合`filterType`に設定されている`custom`、この属性には作成するクラスの完全修飾型名が含まれています。  `filterData`カスタム型フィルターの評価中に使用される値もあります。 |
| filterData | フィルター データを示す文字列。 この属性を指定する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。 |
| filterType | フィルターの種類を示す文字列。 この属性は <xref:System.ServiceModel.Routing.Configuration.FilterType> 型です。  `filterData` 属性を使用する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。 |
| name       | フィルター要素の一意の名前を示す文字列。 |

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

| 要素 | 説明 |
| ------- | ----------- |
| [\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | 受信メッセージの評価に使用される [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を指定するルーティング フィルター セットを定義する構成セクション。 |

## <a name="see-also"></a>関連項目

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
