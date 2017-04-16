---
title: "&lt;iriParsing&gt; 要素 (Uri 設定) | Microsoft Docs"
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
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;iriParsing&gt; 要素 (Uri 設定)
IRI \(International Resource Identifier\) 解析を <xref:System.Uri> に適用するかどうか、および IRI の解析規則を適用するかどうかを指定します。  
  
## スキーマの階層  
 [\<configuration\> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri\> 要素 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing\>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## 構文  
  
```  
<idn  
  enabled="true|false"  
/idn>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**要素**|**説明**|  
|------------|------------|  
|`enabled`|IRI の解析が有効かどうかを指定します。  既定値は `false` です。|  
  
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
  
2.  IRI の解析規則を適用するかどうかを指定する。  これは machine.config ファイルまたは app.config ファイルで行うことができます。  
  
 IRI 解析を有効にする \(iriParsing enabled \= `true`\) と、RFC 3987 の最新の IRI 規則に従って、正規化と文字チェックが行われます。  既定値は、`false` で、RFC 2396 および RFC 3986 に従って正規化と文字チェックが行われます \(IPv6 リテラルの場合\)  
  
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
 <xref:System.Configuration.IriParsingElement?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)