---
title: "&lt;netNamedPipeBinding&gt; の &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;netNamedPipeBinding&gt; の &lt;transport&gt;
名前付きパイプのトランスポート セキュリティ設定を定義します。  
  
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
|protectionLevel|名前付きパイプの保護レベルを定義します。  メッセージに署名すると、転送中のメッセージが第三者によって改ざんされるリスクを軽減します。  暗号化により、転送中にデータレベルのプライバシーが提供されます。  以下の値が有効です。<br /><br /> -   None: 保護されません。<br />-   Sign: メッセージは署名されます。<br />-   EncryptAndSign: メッセージは暗号化および署名されます。<br /><br /> 既定値は EncryptAndSign です。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|バインディングのセキュリティ設定を定義します。|  
  
## 参照  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>   
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)