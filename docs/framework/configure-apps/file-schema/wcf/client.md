---
title: "&lt;client&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#client"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# &lt;client&gt;
`client` 要素は、クライアントが接続可能なエンドポイントの一覧を定義します。  
  
## 構文  
  
```  
  
<system.serviceModel>  
    <client>  
        <endpoint>  
        </endpoint>  
                <metadata>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<endpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|このクライアントが接続可能なエンドポイントを指定するエンドポイント要素のコレクションを含みます。|  
|[\<metadata\>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|メタデータを処理するための設定を含みます。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<system.serviceModel\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|すべての Windows Communication Foundation \(WCF\) 構成要素のルート要素です。|  
  
## 解説  
 `client` セクションは、クライアントが接続可能なエンドポイントの一覧を定義します。  クライアント セクションに示される各エンドポイントは、独自のバインディング、動作、およびコントラクトを定義します。  各エンドポイントは、`name` 属性と `contract` 属性の組み合わせで一意に識別されます。  クライアント コードは、クライアントが実装するサービスのエンドポイントに接続するための `name` を指定します。  `name` 属性が省略されている場合、クライアントが実装するコントラクトのエンドポイントが既定のエンドポイントとして機能します。  
  
 さらに、このセクションはメタデータを処理するための設定も指定します。  
  
## 使用例  
  
```  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ClientSection>   
 <xref:System.ServiceModel.Configuration.MetadataElement>   
 [WCF クライアントの構成](../../../../../docs/framework/wcf/feature-details/client-configuration.md)   
 [クライアント](../../../../../docs/framework/wcf/feature-details/clients.md)