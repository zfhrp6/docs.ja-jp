---
title: "&lt;nameEntry&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<nameEntry> 要素"
  - "nameEntry 要素"
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;nameEntry&gt; 要素
クラス名をアルゴリズムの表示名に割り当てます。これにより、1 つのクラスに複数の表示名を割り当てることができるようになります。  
  
## 構文  
  
```  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|**name**|必須の属性です。<br /><br /> 暗号化クラスを実装するアルゴリズムの表示名を指定します。|  
|**class**|必須の属性です。<br /><br /> [\<cryptoClass\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) 要素で **名前** 属性の値を指定します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.web`|ASP.NET 構成セクションのルート要素を指定します。|  
  
## 解説  
 **name** 属性は、<xref:System.Security.Cryptography> 名前空間に存在するいずれかの抽象クラスの名前です。  抽象暗号化クラスで **Create** メソッドを呼び出すと、抽象クラス名が [Security.CryptoConfig.CreateFromName](frlrfSystemSecurityCryptographyCryptoConfigClassCreateFromNameTopic) メソッドに渡されます。  **CreateFromName** は、**class** 属性で示された型のインスタンスを返します。  **name** 属性が RSA のような短い名前の場合は、**CreateFromName** メソッドを呼び出すときにこの名前を使用できます。  
  
## 使用例  
 次の例では、暗号化クラスを参照し、ランタイムを構成するために **\<nameEntry\>** 要素を使用する方法を示します。  その後、文字列 "RSA" を <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=fullName> メソッドに渡し、<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> メソッドを使用して `MyCryptoRSAClass` オブジェクトを取得できます。  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## 参照  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [暗号設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [暗号サービス](../../../../../docs/standard/security/cryptographic-services.md)   
 [暗号化クラスの設定](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)