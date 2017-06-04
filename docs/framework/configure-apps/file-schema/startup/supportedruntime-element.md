---
title: "&lt;supportedRuntime&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<supportedRuntime> 要素"
  - "supportedRuntime 要素"
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
caps.latest.revision: 33
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 28
---
# &lt;supportedRuntime&gt; 要素
アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。 バージョン 1.1 以降の .NET Framework で構築されたすべてのアプリケーションでは、この要素を使用する必要があります。  
  
 [\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<startup\>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
  
 **\<supportedRuntime\>**  
  
## 構文  
  
```  
  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## 属性  
  
|属性|説明|  
|--------|--------|  
|**version**|省略可能な属性です。<br /><br /> このアプリケーションがサポートする共通言語ランタイム \(CLR: Common Language Runtime\) のバージョンを指定する文字列値。`version` 属性の有効な値については、「["ランタイム バージョン" の値](#version)」セクションを参照してください。 **Note:**  .NET Framework 3.5 では、"*ランタイム バージョン*" の値は「*メジャー*.*マイナー*.*ビルド*」の形式になります。[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降では、必要となるのはメジャー バージョン番号とマイナー バージョン番号のみです \(つまり、"v4.0.30319" ではなく "v4.0"\)。 短い文字列を使用することをお勧めします。|  
|**sku**|省略可能な属性です。<br /><br /> 在庫管理単位 \(SKU\) を指定する文字列の値。SKU はこのアプリケーションがサポートする .NET Framework リリースを指定します。<br /><br /> .NET Framework 4.0 以降では、`sku` 属性の使用が推奨されます。  この属性が指定される場合は、アプリケーションが対象とする .NET Framework のバージョンを示します。<br /><br /> SKU 属性の有効な値については、「["sku id" の値](#sku)」セクションを参照してください。|  
  
## 解説  
 アプリケーション構成ファイルに **\<supportedRuntime\>** 要素がない場合は、アプリケーションの構築に使われたランタイムのバージョンが使用されます。  
  
 ランタイムのバージョン 1.1 以降を使用して構築されたすべてのアプリケーションでは、**\<supportedRuntime\>** 要素を使用する必要があります。 ランタイムのバージョン 1.0 をサポートするアプリケーションでは、[\<requiredRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) 要素を使用する必要があります。  
  
> [!NOTE]
>  [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 関数を使用して構成ファイルを指定する場合は、すべてのバージョンのランタイムに `<requiredRuntime>` 要素を使用する必要があります。[CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) を使用すると、`<supportedRuntime>` 要素は無視されます。  
  
 NET Framework 1.1 から 3.5 までのランタイムの複数のバージョンをサポートするアプリケーションでは、ランタイムの複数のバージョンをサポートする場合は、最初の要素で最も優先度の高いバージョンを指定し、最後の要素で最も優先度の低いバージョンを指定する必要があります。 .NET Framework 4.0 以降のバージョンをサポートするアプリケーションでは、`version` 属性は .NET Framework 4 以降のバージョンで共通の CLR バージョンを示します。`sku` 属性は、アプリケーションが対象とする単一の .NET Framework バージョンを示します。  
  
> [!NOTE]
>  アプリケーションで [CorBindToRuntimeEx 関数](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)などのレガシ アクティブ化パスが使用されていて、これらのパスで CLR の以前のバージョンではなくバージョン 4 をアクティブ化する場合、または、アプリケーションは [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] でビルドされているが、以前のバージョンの .NET Framework でビルドされた混合モードのアセンブリに対する依存関係がある場合、サポートされるランタイムの一覧で [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] を指定するだけでは十分ではありません。 さらに、構成ファイル内の [\<startup\> 要素](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)で、`useLegacyV2RuntimeActivationPolicy` 属性を `true` に設定する必要があります。 ただし、この属性を `true` に設定することは、以前のバージョンの .NET Framework でビルドされたすべてのコンポーネントが、それらのビルドに使用されたランタイムではなく、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] を使用して実行されることを意味します。  
  
 アプリケーションは、そのアプリケーションを実行できる .NET Framework のすべてのバージョンでテストすることをお勧めします。  
  
<a name="version"></a>   
## "ランタイム バージョン" の値  
 次の表は、`version` 属性の "*ランタイム バージョン*" に指定可能な値の一覧です。  
  
|.NET Framework のバージョン|`version` 属性|  
|---------------------------|------------------|  
|1.0|"v1.0.3705"|  
|1.1|"v1.1.4322"|  
|2.0|"v2.0.50727"|  
|3.0|"v2.0.50727"|  
|3.5|"v2.0.50727"|  
|4.0|"v4.0"|  
|4.5|"v4.0"|  
|4.5.1|"v4.0"|  
|4.5.2|"v4.0"|  
|4.6|"v4.0"|  
|4.6.1|"v4.0"|  
  
<a name="sku"></a>   
## "sku id" の値  
 次の表は、`sku` 属性がサポートする .NET Framework 4 以降の .NET Framework のバージョンの一覧です。  .NET Framework 4 以降の `sku` 属性は、アプリケーションが対象とする .NET Framework のバージョンを示す点に注意してください。  
  
|.NET Framework のバージョン|`sku` 属性|  
|---------------------------|--------------|  
|4.0|".NETFramework,Version\=v4.0"|  
|4.0、Client Profile|".NETFramework,Version\=v4.0,Profile\=Client"|  
|4.0、プラットフォームの更新プログラム 1|.NETFramework,Version\=v4.0.1|  
|4.0、Client Profile、更新プログラム 1|.NETFramework,Version\=v4.0.1,Profile\=Client|  
|4.0、プラットフォームの更新プログラム 2|.NETFramework,Version\=v4.0.2|  
|4.0、Client Profile、更新プログラム 2|.NETFramework,Version\=v4.0.2,Profile\=Client|  
|4.0、プラットフォームの更新プログラム 3|.NETFramework,Version\=v4.0.3|  
|4.0、Client Profile、更新プログラム 3|.NETFramework,Version\=v4.0.3,Profile\=Client|  
|4.5|".NETFramework,Version\=v4.5"|  
|4.5.1|".NETFramework,Version\=v4.5.1"|  
|4.5.2|".NETFramework,Version\=v4.5.2"|  
|4.6|".NETFramework,Version\=v4.6"|  
|4.6.1|".NETFramework,Version\=v4.6.1"|  
  
 次の表に、`version` 属性が v4.0 であり、`sku` 属性が NET Framework 4 またはそのプラットフォーム更新プログラム \(PU\) のいずれかを示す場合に、さまざまな `sku` 属性の値について、アプリケーションが実行されるインストール済みの .NET Framework 4 のバージョンを示します。  
  
|`sku` 属性の値|4.0 Client|4.0 Full|4.0 Client \+ PU 1|4.0 Full \+ PU 1|4.0 Client \+ PU 2|4.0 Full \+ PU 2|4.0 Client \+ PU 3|4.0 Full \+ PU 3|4.5 以降|  
|----------------|----------------|--------------|------------------------|----------------------|------------------------|----------------------|------------------------|----------------------|------------|  
|.NETFramework,Version\=v4.0,Profile\=Client|はい|はい|はい|はい|はい|はい|はい|はい|はい|  
|.NETFramework,Version\=v4.0||はい||はい||はい||はい|はい|  
|.NETFramework,Version\=v4.0.1,Profile\=Client|||はい|はい|はい|はい|はい|はい|はい|  
|.NETFramework,Version\=v4.0.1||||はい||はい||はい|はい|  
|.NETFramework,Version\=v4.0.2,Profile\=Client|||||はい|はい|はい|はい|はい|  
|.NETFramework,Version\=v4.0.2||||||はい||はい|はい|  
|.NETFramework,Version\=v4.0.3,Profile\=Client|||||||はい|はい|はい|  
|.NETFramework,Version\=v4.0.3||||||||はい|はい|  
  
## 使用例  
 サポートされているランタイムのバージョンを構成ファイルで指定する例を次に示します。 この構成ファイルは、アプリケーションが .NET Framework 4.6 を対象としていることを示します。  
  
```xml  
  
<configuration> <startup> <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" /> </startup> </configuration>  
  
```  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルで使用できます。  
  
## 参照  
 [スタートアップ設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> 使用するランタイム バージョンの指定](http://msdn.microsoft.com/ja-jp/c376208d-980d-42b4-865b-fbe0d9cc97c2)   
 [インプロセスの side\-by\-side 実行](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)