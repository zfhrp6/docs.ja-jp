---
title: "&lt;一方向&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1436bc0c1708649378ec6747aed9c23cfc1744dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltonewaygt"></a>&lt;一方向&gt;
カスタム バインドのパケット ルーティングを有効にし、一方向メソッドを使用できるようにします。  
  
 \<system.serviceModel >  
\<バインド >  
\<customBinding >  
\<バインド >  
\<oneWay >  
  
## <a name="syntax"></a>構文  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`packetRoutable`|パケット ルーティングが有効かどうかを示すブール値。 既定値は、`false` です。|  
|`MaxAcceptedChannels`|許容できるチャネルの最大数を指定する整数。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<channelPoolSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|現在のチャネルのチャネル プールのプロパティを格納する <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> オブジェクト。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<バインド >](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="remarks"></a>コメント  
 パケット ルーティングを有効にするには、この要素が提供する "一方向の変換" 層が必要です。 カスタム バインディングを作成し、このバインディングをセッション対応または要求応答のトランスポートの上に重ねて、パケット ルーティング可能にすることができます。 この要素は、一方向メソッドをよりネイティブな形式で公開するときにも役に立ちます。 複合二重や信頼できるメッセージ機能などのさらに大きい変換は、この層に対して適用できます。  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
