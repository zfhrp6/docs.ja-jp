---
title: "&lt;serviceActivations&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 956134f0db25055fb9a2f9317a770989cfdab67f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a>&lt;serviceActivations&gt; の &lt;add&gt;
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスの種類にマップする仮想サービス アクティベーション設定を定義できる構成要素。 これにより、.svc ファイルを使用せずに、WAS/IIS でホストされているサービスをアクティブ化できます。  
  
 \<システムです。ServiceModel >  
\<ServiceHostingEnvironment >  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|factory|サービス アクティベーション要素を生成するファクトリの CLR 型名を指定する文字列。|  
|service|サービスを実装する ServiceType (完全修飾 Typename または省略形の Typename (App_Code フォルダーに配置されている場合))。|  
|relativeAddress|現在の IIS アプリケーション内の相対アドレス (たとえば "Service.svc")。 WCF 4.0 ではこの相対アドレスが 1 個の既知のファイル拡張子 (.svc、.xamlx など) を含む必要があります。relativeUrl 用の物理ファイルは必要ありません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|アクティベーション設定を記述する構成セクション。|  
  
## <a name="remarks"></a>コメント  
 web.config ファイルでアクティベーション設定を構成する方法を次の例に示します。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 この構成を使用して、.svc ファイルを使用せずに、GreetingService をアクティブ化できます。  
  
 `<serviceHostingEnvironment>` はアプリケーション レベルの構成であることに注意してください。 構成を格納した `web.config` は、仮想アプリケーションのルートの下に配置する必要があります。 また、`serviceHostingEnvironment` は machinetoApplication の継承可能なセクションです。 コンピューターのルートに単一のサービスを登録すると、アプリケーションの各サービスはこのサービスを継承します。  
  
 構成ベースのアクティベーションは、http および非 http プロトコル経由のアクティベーションをサポートします。 relatativeAddress では、.svc、.xoml、.xamlx などの拡張子が必要です。 既知の buildProviders に対して独自の拡張子をマップできます。これにより、任意の拡張子を使用してサービスをアクティブ化できるようになります。 競合が発生した場合には、`<serviceActivations>` セクションにより、.svc の登録がオーバーライドされます。  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
