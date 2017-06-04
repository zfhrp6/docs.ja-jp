---
title: "&lt;cryptoNameMapping&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<cryptoNameMapping> 要素"
  - "cryptoNameMapping 要素"
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;cryptoNameMapping&gt; 要素
クラスと表示名との割り当てが含まれます。  
  
## 構文  
  
```  
  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|`cryptoClasses`|**\<nameEntry\>** 要素の表示名への割り当てが設定されている暗号化クラスを示します。|  
|`nameEntry`|クラス名をアルゴリズムの表示名に割り当てます。これにより、1 つのクラスに複数の表示名を割り当てることができるようになります。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`cryptographySettings`|暗号に関する設定が含まれます。|  
|`cryptoNameMapping`|クラスと表示名との割り当てが含まれます。|  
|`mscorlib`|cryptographySettings\>  \<要素を含みます。|  
  
## 使用例  
 次の例では、暗号化クラスを参照し、ランタイムを構成するために **\<cryptoNameMapping\>** 要素を使用する方法を示します。  その後、文字列 "RSA" を <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=fullName> メソッドに渡し、<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> メソッドを使用して `MyCryptoRSAClass` オブジェクトを取得できます。  
  
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