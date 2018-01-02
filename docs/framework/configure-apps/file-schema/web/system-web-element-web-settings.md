---
title: "&lt;system.web&gt;要素 (Web 設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 59899178fd9fc8da2334883ed62d9f8655eb335b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a>&lt;system.web&gt;要素 (Web 設定)
ASP.NET ホスト層がプロセス全体の動作を管理する方法についてを説明します。  
  
 \<configuration>  
\<system.web > 要素 (Web 設定)  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Aspnet.config ファイルでは、IIS アプリケーション プールの構成設定を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="remarks"></a>コメント  
 `system.web`要素とその子`applicationPool`に要素が追加された、[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]の[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]します。 実行すると[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]または以降のバージョンの統合モードでは、この要素の組み合わせ ASP.NET がスレッドを管理する方法と、ASP.NET は IIS アプリケーション プールでホストされている場合に要求をキューに方法を設定できます。 実行する場合[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]以降のバージョン クラシック、または ISAPI モードでは、これらの設定は無視されます。  
  
## <a name="example"></a>例  
 次の例では、ASP.NET は IIS アプリケーション プールでホストされている場合、aspnet.config ファイルで ASP.NET プロセス全体の動作を構成する方法を示します。 この例では統合で IIS が実行されているモードと、アプリケーションを使用している、[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]以降のバージョン。 バージョンでこの動作は発生しません、[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]よりも前、[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]です。 値の例では、既定値です。  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|名前空間||  
|スキーマ名||  
|検証ファイル||  
|空にすることができます。||  
  
## <a name="see-also"></a>参照  
 [\<applicationPool> 要素 (Web 設定)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
