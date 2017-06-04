---
title: "暗号設定スキーマ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
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
  - "構成スキーマ [.NET Framework], 暗号化"
  - "構成のセクション [.NET Framework]"
  - "構成の設定 [.NET Framework], 暗号化"
  - "暗号化, 割り当て (アルゴリズム名の)"
  - "暗号化, 設定スキーマ"
  - "要素 [.NET Framework], 暗号化"
  - "スキーマ構成の設定"
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 暗号設定スキーマ
暗号設定スキーマには、アルゴリズムの表示名を暗号化アルゴリズムを実装するクラスに割り当てる方法を指定する要素が含まれます。  
  
 [\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<mscorlib\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [\<cryptographySettings\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [\<cryptoNameMapping\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [\<cryptoClasses\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [\<cryptoClass\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [\<oidMap\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [\<oidEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|要素|説明|  
|--------|--------|  
|[\<cryptoClasses\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|**\<nameEntry\>** 要素の表示名への割り当てが設定されている暗号化クラスを示します。|  
|[\<cryptoClass\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|**\<nameEntry\>** 要素の表示名への割り当てが設定されている暗号化クラスが含まれています。|  
|[\<cryptographySettings\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|暗号に関する設定が含まれます。|  
|[\<cryptoNameMapping\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|クラスと表示名との割り当てが含まれます。|  
|[\<暗号設定の mscorlibelement\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|**\<cryptographySettings\>**要素が含まれています。|  
|[\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|クラス名をアルゴリズムの表示名に割り当てます。これにより、1 つのクラスに複数の表示名を割り当てることができるようになります。|  
|[\<oidEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|ASN.1 オブジェクト識別子 \(OID\) を表示名に割り当てます。|  
|[\<oidMap\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|クラスへの ASN.1 OID 割り当てが含まれます。|  
  
## 参照  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [暗号サービス](../../../../../docs/standard/security/cryptographic-services.md)