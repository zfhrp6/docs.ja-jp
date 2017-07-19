---
title: "&lt;netNamedPipeBinding&gt; の &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# &lt;netNamedPipeBinding&gt; の &lt;security&gt;
バインディングのセキュリティ設定を定義します。  
  
## 構文  
  
```  
  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|モード|このバインディングに適用されるセキュリティの種類を指定します。  以下の値が有効です。<br /><br /> -   None: セキュリティは無効になります。<br />-   Transport: セキュリティは、基になるトランスポート ベースのセキュリティを使用して提供されます。  このモードでの保護レベルを制御できます。<br />-   既定値は、Transport です。  この属性は <xref:System.ServiceModel.NetNamedPipeSecurityMode> 型です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|transport|トランスポートのセキュリティ設定を定義します。  この要素は <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|バインド|[\<netNamedPipeBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)のバインディング要素です。|  
  
## 参照  
 <xref:System.ServiceModel.NetNamedPipeSecurity>   
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [資格情報の種類の選択](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)