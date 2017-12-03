---
title: "&lt;baseAddresses&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf417653652c2a0f28fe5c6491a7da9949678140
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a>&lt;baseAddresses&gt; の &lt;add&gt;
サービス ホストによって使用されるベース アドレスを指定する構成要素を表します。  
  
 \<システムです。ServiceModel >  
\<クライアント >  
\<エンドポイント >  
\<ホスト >  
\<baseAddresses >  
\<baseAddress >  
  
## <a name="syntax"></a>構文  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`baseAddress`|サービス ホストによって使用されるベース アドレスを指定する文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|`baseAddress` 要素のコレクション。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [ホスティング](../../../../../docs/framework/wcf/feature-details/hosting.md)
