---
title: "&lt;transportConfigurationType&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b52345ae30ab56a6f34d2aa46f9836d67555b15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a>&lt;transportConfigurationType&gt; の &lt;add&gt;
この要素は、特定のトランスポートの種類を識別するキーと値のペアです。  
  
 \<システムです。ServiceModel >  
\<ServiceHostingEnvironment >  
\<transportConfigurationTypes >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|必須の文字列属性です。<br /><br /> トランスポートの種類を一意に識別するユーザー定義キーを含みます。|  
|transportConfigurationType|特定のトランスポートを実装する種類を含む文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<transportConfigurationTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|特定のトランスポートを実装する型のコレクション。|  
  
## <a name="example"></a>例  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [ホスティング](../../../../../docs/framework/wcf/feature-details/hosting.md)
