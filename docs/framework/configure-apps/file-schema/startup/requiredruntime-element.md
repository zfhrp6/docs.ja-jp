---
title: "&lt;requiredRuntime&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<requiredRuntime> 要素"
  - "コンテナー タグ, <requiredRuntime> 要素"
  - "requiredRuntime 要素"
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;requiredRuntime&gt; 要素
共通言語ランタイムのバージョン 1.0 だけがアプリケーションでサポートされることを指定します。  
  
## 構文  
  
```  
  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`version`|省略可能な属性。<br /><br /> このアプリケーションがサポートする .NET Framework のバージョンを指定する文字列値。  文字列値は、.NET Framework のインストール ルートの下にあるディレクトリの名前に一致する必要があります。  文字列値の内容は、解析されません。|  
|`safemode`|省略可能な属性。<br /><br /> ランタイム スタートアップ コードが、レジストリを検索してランタイムのバージョンを判断するかどうかを指定します。|  
  
## safemode 属性  
  
|値|説明|  
|-------|--------|  
|`false`|ランタイム スタートアップ コードはレジストリを検索します。  これが既定値です。|  
|`true`|ランタイム スタートアップ コードはレジストリを検索しません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`startup`|`<requiredRuntime>` 要素を含みます。|  
  
## 解説  
 ランタイムのバージョン 1.0 のみをサポートするようにビルドされたアプリケーションでは、`<requiredRuntime>` 要素を使用する必要があります。  ランタイムのバージョン 1.1 以降を使用してビルドされたアプリケーションでは、`<supportedRuntime>` 要素を使用する必要があります。  
  
> [!NOTE]
>  [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 関数を使用して構成ファイルを指定する場合は、すべてのバージョンのランタイムに `<requiredRuntime>` 要素を使用する必要があります。  [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) を使用すると、`<supportedRuntime>` 要素は無視されます。  
  
 `version` 属性文字列は、指定したバージョンの .NET Framework のインストール フォルダー名と一致する必要があります。  この文字列は解釈されません。  ランタイム スタートアップ コードで一致するフォルダーが見つからなかった場合、ランタイムは読み込まれません。スタートアップ コードはエラー メッセージを表示し、終了します。  
  
> [!NOTE]
>  Microsoft Internet Explorer でホストされるアプリケーションのスタートアップ コードは、`<requiredRuntime>` 要素を無視します。  
  
## 使用例  
 構成ファイルでランタイムのバージョンを指定する例を示します。  
  
```  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## 参照  
 [スタートアップ設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/ja-jp/c376208d-980d-42b4-865b-fbe0d9cc97c2)