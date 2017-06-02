---
title: "&lt;xmlSchemaImporterExtensions&gt; の &lt;add&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<xmlSchemaImporterExtensions> 要素の <add> 要素"
  - "XML シリアル化, 構成"
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;xmlSchemaImporterExtensions&gt; の &lt;add&gt; 要素
XSD 型を .NET Framework 型に対応付けるために、<xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。  構成ファイルの詳細については、「[構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。  
  
 \<XmlSchemaImporterExtensions\>  
\<add\>  
  
## 構文  
  
```  
  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|**name**|インスタンスの検索に使用される簡易名。|  
|**type**|必ず指定します。  追加するスキーマ拡張クラスを指定します。  **type** 属性の値は 1 行で指定し、完全修飾型名を含める必要があります。  アセンブリをグローバル アセンブリ キャッシュ \(GAC: Global Assembly Cache\) に配置する場合は、バージョン、カルチャ、およびアセンブリの署名に使用した公開キーのトークンも含める必要があります。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|\<xmlSchemaImporterExtensions\>|<xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型が含まれます。|  
  
## 使用例  
 型を対応付けるときに XmlSchemaImporter が使用できる拡張の型を追加するコード例を次に示します。  
  
```  
<configuration>  
  <system.xml.serialization>  
    <xmlSchemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </xmlSchemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## 参照  
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 [\<system.xml.serialization\> 要素](../../../docs/framework/serialization/system-xml-serialization-element.md)   
 [\<schemaImporterExtensions\> 要素](../../../docs/framework/serialization/schemaimporterextensions-element.md)