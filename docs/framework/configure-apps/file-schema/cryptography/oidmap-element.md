---
title: "&lt;oidMap&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<oidMap> 要素"
  - "oidMap 要素"
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;oidMap&gt; 要素
クラスへの ASN.1 オブジェクト識別子 \(OID\) 割り当てが含まれます。  
  
## 構文  
  
```  
<oidMap>   
</oidMap>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<oidEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|ASN.1 OID を表示名に割り当てます。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`cryptographySettings`|暗号に関する設定が含まれます。|  
|`mscorlib`|`cryptographySettings`  要素を含みます。|  
  
## 使用例  
 次の例は、このハッシュ アルゴリズムの実装に RIPEMD\-160 ハッシュ アルゴリズムの OID を格納するために **\<oidMap\>** 要素を使用する方法を示します。  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## 参照  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [暗号設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [暗号サービス](../../../../../docs/standard/security/cryptographic-services.md)   
 [暗号化クラスの設定](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)   
 [暗号化アルゴリズムへのオブジェクト ID の割り当て](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)