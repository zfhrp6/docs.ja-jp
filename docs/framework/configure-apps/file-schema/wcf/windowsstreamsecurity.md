---
title: "&lt;windowsStreamSecurity&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# &lt;windowsStreamSecurity&gt;
カスタム バインディングの Windows ストリーム セキュリティ設定を指定します。  
  
## 構文  
  
```  
  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|protectionLevel|メッセージ レベルのセキュリティを定義します。  メッセージに署名すると、転送中のメッセージが第三者によって改ざんされるリスクを軽減します。  暗号化により、転送中にデータレベルのプライバシーが提供されます。  以下の値が有効です。<br /><br /> -   None: 保護されません。<br />-   Sign: メッセージは署名されます。<br />-   EncryptAndSign: メッセージは署名および暗号化されます。<br /><br /> 既定値は EncryptAndSign です。<br /><br /> この属性は <xref:System.Net.Security.ProtectionLevel> 型です。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<binding\>](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## 解説  
 TCP などのストリーム指向プロトコルおよび名前付きパイプを使用するトランスポートは、ストリーム ベースのトランスポート アップグレードをサポートします。  特に、WCF にはセキュリティ アップグレードが用意されています。  このトランスポート セキュリティの構成は、この構成要素および [\<sslStreamSecurity\>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) によってカプセル化され、構成してカスタム バインディングに追加できます。  
  
## 参照  
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>   
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)