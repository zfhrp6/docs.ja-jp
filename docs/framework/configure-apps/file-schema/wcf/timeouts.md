---
title: "&lt;タイムアウト&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41ebd88f64b001b577342562c9c3010b307aaccc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttimeoutsgt"></a>&lt;タイムアウト&gt;
サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素を表します。  
  
 \<システムです。ServiceModel >  
\<クライアント >  
\<エンドポイント >  
\<ホスト >  
\<タイムアウト >  
  
## <a name="syntax"></a>構文  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`closeTimeout`|サービス ホストを閉じるまでに待機できる期間を指定する <xref:System.TimeSpan> 値。|  
|`openTimeout`|サービス ホストを開くまでに待機できる期間を指定する <xref:System.TimeSpan> 値。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ホスト >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|サービス ホストの設定を指定する構成要素です。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [ホスティング](../../../../../docs/framework/wcf/feature-details/hosting.md)
