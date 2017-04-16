---
title: "&lt;system.identityModel&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;system.identityModel&gt;
アプリケーションでんだ Windows アイデンティティ基盤 \(ぜ\) オプションを有効にする構成を提供します。  
  
 \<system.identityModel\>  
  
## 構文  
  
```  
<system.identityModel>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス ・ レベルの id の設定を指定します。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|`<configuration>`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## 解説  
 追加、 `<system.identityModel>`してたんだ Windows アイデンティティ基盤 \(ぜ\) を使用するアプリケーション、サービスを構成するには、構成ファイルのセクション。  `<system.identityModel>`要素で表される、 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>クラス。  
  
## 使用例  
 追加する方法の例を示します、 `<system.identityModel>`するには、構成ファイルのセクション。  構成セクションと名前空間の宣言でを最初に追加する必要があります、 `<configSections>`要素。  追加することができ、 `<system.IdentityModel>` 1 つまたは複数の識別情報の構成を指定するのには、構成ファイルの要素。  
  
```  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## 参照  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>