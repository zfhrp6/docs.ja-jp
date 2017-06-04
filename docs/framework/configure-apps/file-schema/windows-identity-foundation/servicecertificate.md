---
title: "&lt;serviceCertificate&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;serviceCertificate&gt;
暗号化し、トークンを復号化に使用される X.509 証明書を構成します。  
  
## 構文  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<certificateReference\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|検索して、証明書ストアの X.509 証明書を検証するために使用する設定を指定します。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定を含む、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) と、 <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\)。|  
  
## 使用例  
 \<serviceCertificate\> の使用、次の XML を示しています。 要素。  XML から取得されます、 `CustomToken`サンプル。  
  
```  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```