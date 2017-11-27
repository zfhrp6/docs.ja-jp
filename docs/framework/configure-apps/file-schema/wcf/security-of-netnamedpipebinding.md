---
title: "&lt;netNamedPipeBinding&gt; の &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: efb6289c63cdc98402336949ef5916e7568775a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a>&lt;netNamedPipeBinding&gt; の &lt;security&gt;
バインディングのセキュリティ設定を定義します。  
  
 \<システムです。ServiceModel >  
\<バインド >  
\<netNamedPipeBinding >  
\<バインド >  
\<セキュリティ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|モード|このバインディングに適用されるセキュリティの種類を指定します。 以下の値が有効です。<br /><br /> -なし: 無効になりますセキュリティ。<br />-トランスポート: セキュリティは、基になるトランスポート ベースのセキュリティを使用して提供します。 このモードでの保護レベルを制御できます。<br />-既定値は、トランスポートです。 この属性は <xref:System.ServiceModel.NetNamedPipeSecurityMode> 型です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|transport|トランスポートのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|バインド|バインド要素、 [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)です。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [サービスとクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [資格情報の種類を選択します。](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システム指定のバインディングを構成します。](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<バインド >](../../../../../docs/framework/misc/binding.md)
