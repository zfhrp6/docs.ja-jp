---
title: "webRequestModules の &lt;add&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> 要素, webRequestModules"
  - "<webRequestModules>, add 要素"
  - "add 要素, webRequestModules"
  - "webRequestModules, add 要素"
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 16
---
# webRequestModules の &lt;add&gt; 要素 (ネットワーク設定)
カスタム Web 要求モジュールをアプリケーションに追加します。  
  
## 構文  
  
```  
  
      <add   
  prefix = "URI prefix"   
  type = "module name, Version, Culture, PublicKeyToken"   
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**Attribute**|**説明**|  
|-------------------|------------|  
|`prefix`|この Web 要求モジュールで処理される要求の URI プレフィックス。|  
|`type`|この Web 要求モジュールを実装するモジュールのアセンブリ名およびクラス名。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|ネットワーク ホストからの情報を要求するために使用するモジュールを指定します。|  
  
## 解説  
 `prefix` 属性は、指定した Web 要求モジュールを使用する URI プレフィックスを定義します。  通常、Web 要求モジュールは、HTTP や FTP などの特定のプロトコルを処理するために登録します。ただし、特定のサーバーまたはサーバー上の特定のパスへの要求を処理するために登録することもできます。  
  
 Web 要求モジュールは、プレフィックスと一致する URI が <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> メソッドに渡されると作成されます。  
  
 `prefix` 属性の値は、"http" や "http:\/\/www.contoso.com" のように、有効な UR の先行文字である必要があります。  
  
 `type` 属性の値は、有効な DLL 名および対応するクラスの名前をコンマで区切って指定する必要があります。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 HTTP 用のカスタム Web 要求モジュールを登録するコード例を次に示します。  Version の値および PublicKeyToken の値は、指定したモジュールに対応する正しい値に置き換える必要があります。  
  
```  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.WebRequest>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)