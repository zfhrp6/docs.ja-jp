---
title: "&lt;oidEntry&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<oidEntry> 要素"
  - "oidEntry 要素"
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;oidEntry&gt; 要素
ASN.1 オブジェクト識別子 \(OID\) を表示名に割り当てます。  
  
## 構文  
  
```  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|**OID**|必須の属性です。<br /><br /> クラスで実装されるアルゴリズムに対応する ASN.1 OID を指定します。|  
|**name**|必須の属性です。<br /><br /> [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) タグで **名前** 属性の値を指定します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`cryptographySettings`|暗号に関する設定が含まれます。|  
|`mscorlib`|`cryptographySettings` 要素を含みます。|  
|`oidMap`|クラスへの ASN.1 オブジェクト識別子 \(OID\) 割り当てが含まれます。|  
  
## 解説  
 ASN.1 オブジェクト識別子は、ある暗号化形式のアルゴリズムを識別します。  オブジェクト識別子を、識別するアルゴリズムの表示名に割り当てます。  オブジェクト識別子の詳細については、MSDN ライブラリを参照してください。  
  
## 使用例  
 次の例は、このハッシュ アルゴリズムの実装に RIPEMD\-160 ハッシュ アルゴリズムにオブジェクト ID を割り当てるために **\<oidEntry\>** 要素を使用する方法を示します。  
  
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
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
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