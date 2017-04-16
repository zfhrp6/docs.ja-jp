---
title: "&lt;startup&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#startup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<startup> 要素"
  - "コンテナー タグ, <startup> 要素"
  - "startup 要素"
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: 19
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 19
---
# &lt;startup&gt; 要素
共通言語ランタイムのスタートアップ情報を指定します。  
  
## 構文  
  
```  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`useLegacyV2RuntimeActivationPolicy`|省略可能な属性。<br /><br /> [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] のランタイムのアクティブ化ポリシーを有効にするか、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] のアクティブ化ポリシーを使用するかを指定します。|  
  
## useLegacyV2RuntimeActivationPolicy 属性  
  
|値|説明|  
|-------|--------|  
|`true`|選択されたランタイムで [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] のランタイムのアクティブ化ポリシーを有効にし、ランタイムの上限を CLR バージョン 2.0 とするのではなく、レガシのランタイムのアクティブ化手法 \([CorBindToRuntimeEx 関数](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)など\) を、構成ファイルから選択されたランタイムにバインドするようにします。  これにより、構成ファイルから CLR バージョン 4 またはそれ以降が選択された場合、それ以前のバージョンの .NET Framework で作成された混合モード アセンブリは、選択された CLR バージョンで読み込まれます。  この値を設定すると、CLR バージョン 1.1 または CLR バージョン 2.0 が同じプロセスに読み込まれなくなり、インプロセスの side\-by\-side 機能は事実上無効になります。|  
|`false`|[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] およびそれ以降の既定のアクティブ化ポリシーを使用し、レガシのランタイムのアクティブ化手法で CLR バージョン 1.1 または 2.0 をプロセスに読み込むことができるようにします。  この値を設定すると、.NET Framework 4 以降に読み込まれなく .NET Framework 4 以降でビルドされていない限り、混合モード アセンブリは行われません。  この値が既定値です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<requiredRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|共通言語ランタイムのバージョン 1.0 だけがアプリケーションでサポートされることを指定します。  ランタイムのバージョン 1.1 以降でビルドされたアプリケーションは **\<supportedRuntime\>** 要素を使用する必要があります。|  
|[\<supportedRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## 解説  
 ランタイムのバージョン 1.1 以降を使用して構築されたすべてのアプリケーションでは、**\<supportedRuntime\>** 要素を使用する必要があります。  ランタイムのバージョン 1.0 をサポートするアプリケーションでは、**\<requiredRuntime\>** 要素を使用する必要があります。  
  
 Microsoft Internet Explorer でホストされるアプリケーションのスタートアップ コードは **\<startup\>** 要素およびその子要素は無視されます。  
  
## useLegacyV2RuntimeActivationPolicy 属性  
 アプリケーションで [CorBindToRuntimeEx 関数](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)などのレガシ アクティブ化パスが使用されていて、これらのパスで CLR の以前のバージョンではなくバージョン 4 をアクティブ化する場合、または、アプリケーションは [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] でビルドされているが、以前のバージョンの .NET Framework でビルドされた混合モードのアセンブリに対する依存関係がある場合、この属性は便利です。  このようなシナリオでは、属性を `true` に設定します。  
  
> [!NOTE]
>  属性を `true` に設定すると、CLR バージョン 1.1 または CLR バージョン 2.0 が同じプロセスに読み込まれなくなり、インプロセスの side\-by\-side 機能は事実上無効になります \(「[Side\-by\-Side Execution for COM Interop](http://msdn.microsoft.com/ja-jp/4302318c-3586-49bf-8620-b9a39cdf4a32)」を参照\)。  
  
## 使用例  
 構成ファイルでランタイムのバージョンを指定する例を示します。  
  
```  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## 参照  
 [スタートアップ設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/ja-jp/c376208d-980d-42b4-865b-fbe0d9cc97c2)   
 [Side\-by\-Side Execution for COM Interop](http://msdn.microsoft.com/ja-jp/4302318c-3586-49bf-8620-b9a39cdf4a32)   
 [インプロセスの side\-by\-side 実行](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)