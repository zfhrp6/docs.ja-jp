---
title: "&lt;idn&gt; 要素 (Uri 設定) | Microsoft Docs"
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
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;idn&gt; 要素 (Uri 設定)
国際化ドメイン名 \(IDN: Internationalized Domain Name\) による解析をドメイン名に適用するかどうかを指定します。  
  
## スキーマの階層  
 [\<configuration\> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri\> 要素 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<idn\>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## 構文  
  
```  
<idn  
  enabled="All|AllExceptIntranet|None"  
/idn>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**要素**|**説明**|  
|------------|------------|  
|`enabled`|ドメイン名に国際化ドメイン名 \(IDN: Internationalized Domain Name\) による解析を適用するかどうかを指定します。既定値は None です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|URI \(Uniform Resource Identifier\) で表現された Web アドレスが .NET Framework によってどのように処理されるかの設定を格納します。|  
  
## 解説  
 .NET Framework 3.5、3.0 SP1、および 2.0 SP1 では、既存の <xref:System.Uri> クラスが拡張され、IRI \(International Resource Identifier\) および国際化ドメイン名 \(IDN: Internationalized Domain Name\) をサポートするようになりました。  現在のユーザーからは、明確に IRI と IDN サポートを有効にしない限り、.NET Framework 2.0 の動作からの変更点は見えません。  これにより、以前のバージョンの .NET Framework との互換性が確保されます。  
  
 IRI のサポートを有効にするには、次の 2 点を変更する必要があります。  
  
1.  .NET Framework 2.0 ディレクトリの machine.config ファイルに次の行を追加する。  
  
    ```  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  ドメイン名に国際化ドメイン名 \(IDN: Internationalized Domain Name\) による解析を適用するか、IRI の解析規則を適用するかを指定します。  これは machine.config ファイルまたは app.config ファイルで行うことができます。  
  
 使用する DNS サーバーに応じて、IDN がとりうる値は次の 3 つです。  
  
-   idn enabled \= All  
  
     この値は、Unicode のドメイン名があれば、それを等価の Punycode \(IDN 名\) に変換します。  
  
-   idn enabled \= AllExceptIntranet  
  
     この値は、ローカルなイントラネット以外のすべての Unicode ドメイン名を、等価の Punycode \(IDN 名\) を使用するように変換します。  このように、ローカルなイントラネットで国際名を処理する場合、このイントラネットで使用する DNS サーバーは Unicode の名前解決をサポートしている必要があります。  
  
-   idn enabled \= None  
  
     この値は、どの Unicode のドメイン名も、Punycode を使用するように変換しません。  これが既定値であり、.NET Framework 2.0 の動作と同じです。  
  
 IDN を有効にすると、ドメイン名に含まれるすべての Unicode ラベルが等価の Punycode に変換されます。  Punycode 名は ASCII 文字だけで構成され、必ず xn\-\- というプレフィックスで始まります。  この目的は、インターネット上の既存の DNS サーバーをサポートすることです。ほとんどの DNS サーバーは、ASCII 文字しかサポートしていません \(RFC 3940 を参照\)。  
  
### 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 例  
  
### 説明  
 次のコード例は、<xref:System.Uri> クラスで IRI の解析および IDN 名をサポートするための構成を示しています。  
  
### コード  
  
```  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## 参照  
 <xref:System.Configuration.IdnElement?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)