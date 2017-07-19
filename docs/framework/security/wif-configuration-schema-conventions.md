---
title: "WIF 構成スキーマの規則 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# WIF 構成スキーマの規則
このトピックでは、Windows ID Foundation \(WIF\) の構成に関するトピック全体で使用される規則について説明し、[\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) と [\<system.identityModel.services\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) のセクションで使用される共通機能と属性について説明します。  
  
<a name="BKMK_Modes"></a>   
## モード  
 WIF の構成要素の多くに `mode` の属性があります。  処理の特定の部分にクラスが使用される構成要素が現在の要素の子要素として指定し、この属性は通常、制御します。  構成エラーは、構成ファイルに含まれる要素がモードの設定では、は無視されます発生します。  
  
<a name="BKMK_TimespanValues"></a>   
## 時刻値  
 許可される書式を表示するには、属性の型は、<xref:System.TimeSpan.Parse%28System.String%29> のメソッドを表示するときに <xref:System.TimeSpan> を使用する場所。  この形式は、次の仕様に準拠します。  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 たとえば、「30 "、「30.00:00」、「30.00:00: すべて平均 30 日 00 "; および「00:05」、「00:05: 00 "、「0.00:05: すべて 5 分 00.00 "を意味します。  
  
<a name="BKMK_CertificateReferences"></a>   
## 証明書の参照  
 `<certificateReference;>` の要素を使用して証明書複数の要素への参照の取得。  証明書を参照すると、次の属性があります。  
  
|||  
|-|-|  
|`storeLocation`|<xref:System.Security.Cryptography.X509Certificates.StoreLocation> の列挙値: `CurrentUser` か `CurrentMachine`。|  
|`storeName`|<xref:System.Security.Cryptography.X509Certificates.StoreName> の列挙値; このコンテキストの最も役立つの `My` と `TrustedPeople`です。|  
|`x509FindType`|<xref:System.Security.Cryptography.X509Certificates.X509FindType> の列挙値; このコンテキストの最も役立つの `FindBySubjectName` と `FindByThumbprint`です。  `FindByThumbprint` の型が稼働環境で使用するエラーの可能性を削減することをお勧めします。|  
|`findValue`|`x509FindType` の属性に基づいて証明書を検索するために使用される値。  `FindByThumbprint` の型が稼働環境で使用するエラーの可能性を削減することをお勧めします。  `FindByThumbPrint` が指定された場合、この属性は証明書のサムプリントの 16 進数文字列の形式である値を受け取ります; たとえば、「」97249e1a5fa6bee5e515b82111ef524a4c91583f。|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## カスタム型の参照  
 `type` の属性を使用して複数の要素の参照のカスタム型。  この属性は、カスタムの型の名前を指定する必要があります。  グローバル アセンブリ キャッシュ \(GAC\) の型を参照するには、厳密な名前を使用する必要があります。  Bin ディレクトリにアセンブリの型を参照するには、単純なアセンブリ修飾参照を使用することがあります。  App\_Code\/ディレクトリに定義された型は、アセンブリ修飾なしの型名だけを指定することによって参照できます。  
  
 カスタム型で指定された型から派生していない場合、`public` の既定値 \(0\) コンストラクターの引数を指定する必要があります。  
  
## 参照  
 [\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)   
 [\<system.identityModel.services\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)