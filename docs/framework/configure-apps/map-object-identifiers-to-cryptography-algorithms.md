---
title: "暗号化アルゴリズムへのオブジェクト ID の割り当て | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "暗号アルゴリズム"
  - "暗号化, 割り当て (オブジェクト ID の)"
  - "デジタル署名"
  - "識別子, 割り当て (オブジェクト ID の)"
  - "割り当て (オブジェクト ID の)"
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 暗号化アルゴリズムへのオブジェクト ID の割り当て
デジタル署名は、データをあるプログラムから別のプログラムへ送信したときに、データが不正に変更されないことを保証するために使用されます。  一般に、デジタル署名は、署名の対象となるデータのハッシュに数値演算関数を適用して計算されます。  署名対象のハッシュ値をフォーマットするときに、一定のデジタル署名アルゴリズムにより、フォーマット操作の一部として ASN.1 OID \(オブジェクト ID\) が付加されます。  OID は、ハッシュの計算に使用されたアルゴリズムを識別します。  アルゴリズムにオブジェクト ID を割り当てることにより、カスタムのアルゴリズムを使用するように暗号機構を拡張できます。  新しいハッシュ アルゴリズムにオブジェクト ID を割り当てる方法を次の例で示します。  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [\<oidEntry\> 要素](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) は 2 個の属性が含まれています。  **OID** 属性は、オブジェクト ID 番号です。  **名前** 属性は [\<nameEntry\> 要素](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)から **名前** 属性の値です。  オブジェクト ID に簡易名を割り当てるには、あらかじめ、クラスにアルゴリズム名を割り当てる必要があります。  
  
## 参照  
 [暗号化クラスの設定](../../../docs/framework/configure-apps/configure-cryptography-classes.md)   
 [暗号サービス](../../../docs/standard/security/cryptographic-services.md)