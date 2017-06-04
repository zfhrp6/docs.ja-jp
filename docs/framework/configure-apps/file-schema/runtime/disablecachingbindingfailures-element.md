---
title: "&lt;disableCachingBindingFailures&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<disableCachingBindingFailures> 要素"
  - "アセンブリ [.NET Framework], キャッシュ (バインディング エラーを)"
  - "キャッシュ (アセンブリ バインディング エラーを)"
  - "disableCachingBindingFailures 要素"
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# &lt;disableCachingBindingFailures&gt; 要素
調査でアセンブリが見つからなかったために発生するバインディング エラーのキャッシュを無効にするかどうかを指定します。  
  
## 構文  
  
```  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|enabled|必須の属性です。<br /><br /> 調査でアセンブリが見つからなかったために発生するバインディング エラーのキャッシュを無効にするかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|0|調査でアセンブリが見つからなかったために発生するバインディング エラーのキャッシュを無効にしません。  これは .NET Framework Version 2.0 以降での既定のバインディング動作です。|  
|1|調査でアセンブリが見つからなかったために発生するバインディング エラーのキャッシュを無効にします。  この設定により、.NET Framework Version 1.1 のバインディング動作に戻ります。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 .NET Framework Version 2.0 以降では、アセンブリを読み込む際の既定の動作として、すべてのバインディング エラーおよび読み込みエラーがキャッシュされます。  つまり、アセンブリの読み込みに失敗した場合、それ以降の同じアセンブリの読み込みの要求は即座に失敗します。アセンブリを探す試みは行われません。  この要素は、調査パスでアセンブリが見つからなかったために発生するバインディング エラーに対応するための既定の動作を無効にします。  このようなエラーでは、<xref:System.IO.FileNotFoundException> がスローされます。  
  
 バインディング エラーおよび読み込みエラーの中には、この要素の影響を受けないものもあり、このようなエラーは常にキャッシュされます。  このようなエラーは、アセンブリが見つかっても読み込むことができなかった場合に発生します。  <xref:System.BadImageFormatException> または <xref:System.IO.FileLoadException> がスローされます。  このようなエラーの例を次の一覧に示します。  
  
-   有効なアセンブリではないファイルを読み込もうとした場合、その後に無効なファイルを正しいアセンブリに置き換えても、それ以降のそのアセンブリの読み込みは失敗します。  
  
-   ファイル システムによってロックされているアセンブリを読み込もうとした場合、その後にそのアセンブリがファイル システムによって解放されても、それ以降のそのアセンブリの読み込みは失敗します。  
  
-   読み込もうとしているアセンブリの 1 つ以上のバージョンが調査パスに存在するにもかかわらず、要求している特定のバージョンがその中に含まれていない場合、正しいバージョンを調査パスに移動しても、それ以降のそのバージョンの読み込みは失敗します。  
  
## 使用例  
 調査でアセンブリが見つからなかったために発生するアセンブリ バインディング エラーのキャッシュを無効にする方法を次のコード例に示します。  
  
```  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)