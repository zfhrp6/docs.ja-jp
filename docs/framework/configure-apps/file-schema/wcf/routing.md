---
title: '&lt;ルーティング&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 1771d8a2603a8f61af6ba6e2acf6243d2fd073f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747727"
---
# <a name="ltroutinggt"></a>&lt;ルーティング&gt;

Windows Communication Foundation (WCF) の種類を決定するルーティング フィルター セットを定義する構成セクションを表します<xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージの評価とルーティング テーブルをするターゲット エンドポイントを定義するときに使用されます。フィルターに一致する場合にメッセージを送信します。

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;**\<ルーティング >**

## <a name="syntax"></a>構文

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

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

なし

### <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [**\<フィルター >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | 受信メッセージを評価するときに使用する Windows Communication Foundation (WCF) MessageFilter の種類を決定するルーティング フィルター セットを格納します。 |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | ルーティング フィルターとターゲット エンドポイントとのマッピングを格納します。フィルターが一致したときにエンドポイントを指定するために使用されます。 |

### <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| **\<システムです。ServiceModel >** | すべての WCF 構成要素のルート要素です。 |

## <a name="see-also"></a>関連項目

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
