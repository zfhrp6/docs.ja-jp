---
title: "&lt;applicationPool&gt; 要素 (Web 設定) | Microsoft Docs"
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
  - "<applicationPool> 要素"
  - "applicationPool 要素"
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;applicationPool&gt; 要素 (Web 設定)
ASP.NET アプリケーションが [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 以降のバージョンの統合モードで実行されている場合に、プロセス全体の動作を管理するために ASP.NET で使用される構成設定を指定します。  
  
> [!IMPORTANT]
>  この要素と、この要素でサポートされる機能は、ASP.NET アプリケーションが [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 以降のバージョンでホストされる場合にのみ機能します。  
  
## 構文  
  
```  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`maxConcurrentRequestsPerCPU`|ASP.NET で許可する CPU あたりの同時要求数を指定します。|  
|`maxConcurrentThreadsPerCPU`|各 CPU のアプリケーション プールで実行できる同時スレッド数を指定します。  これは、要求を処理するために CPU あたりで使用できるマネージ スレッドの数を制限できるため、ASP.NET の同時実行を制御する手段の選択肢となります。  既定の設定は 0 で、この場合、ASP.NET は CPU あたりの作成可能なスレッド数を制限しません。ただし、作成可能なスレッド数には、共通言語ランタイム \(CLR: Common Language Runtime\) のスレッド プールによる制限も適用されます。|  
|`requestQueueLimit`|単一のプロセスで ASP.NET のキューに配置できる要求の最大数を指定します。  複数の ASP.NET アプリケーションが 1 つのアプリケーション プールで実行される場合、そのアプリケーション プール内のアプリケーションに対する要求の累積数は、この設定によって制限されます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<system.web\>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|ASP.NET とホスト アプリケーションの対話方法に関する情報が含まれます。|  
  
## 解説  
 [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 以降を統合モードで実行する場合は、この要素の組み合わせによって、アプリケーションが IIS アプリケーション プールでホストされているときに ASP.NET でどのようにスレッドを管理し、どのように要求をキューに配置するかを構成できます。  IIS 6 を実行する場合や、[!INCLUDE[iisver](../../../../../includes/iisver-md.md)] をクラシック モードまたは ISAPI モードで実行する場合は、これらの設定は無視されます。  
  
 `applicationPool` の設定は、.NET Framework の特定のバージョンで実行されるすべてのアプリケーション プールに適用されます。  この設定は aspnet.config ファイルに含まれています。  .NET Framework の Version 2.0 と 4 には、このファイルの個別のバージョンがあります \(.NET Framework Version 3.0 および 3.5 では、Version 2.0 と aspnet.config ファイルが共有されます\)。  
  
> [!IMPORTANT]
>  [!INCLUDE[win7](../../../../../includes/win7-md.md)] で [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] を実行する場合は、アプリケーション プールごとに別々の aspnet.config ファイルを構成できます。  これにより、アプリケーション プールごとにスレッドのパフォーマンスを調整できます。  
  
 `maxConcurrentRequestsPerCPU` 設定については、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] での既定の設定は "5000" で、実際に CPU あたりの要求数が 5000 以上にならない限り、ASP.NET によって制御される要求調整は実質的に無効になります。  代わりに、CLR スレッド プールの制限によって、CPU あたりの同時実行が自動的に管理されます。  非同期要求処理を広く利用するアプリケーションや、長時間実行される多数の要求がネットワーク I\/O でブロックされるアプリケーションには、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] の既定の緩やかな制限が適しています。  `maxConcurrentRequestsPerCPU` を 0 に設定すると、ASP.NET の要求の処理にマネージ スレッドは使用されなくなります。  アプリケーションが IIS アプリケーション プールで実行される場合、要求は IIS I\/O スレッドにとどまるので、同時実行は IIS スレッドの設定によって調整されます。  
  
 `requestQueueLimit` の設定は、ASP.NET アプリケーションの Web.config ファイルで設定される [processModel](http://msdn.microsoft.com/ja-jp/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) 要素の `requestQueueLimit` 属性と同じように機能します。  ただし、aspnet.config ファイルにある `requestQueueLimit` の設定は、Web.config ファイルにある `requestQueueLimit` の設定をオーバーライドします。  つまり、両方の属性を設定した場合 \(既定で両方とも設定されています\)、aspnet.config ファイルにある `requestQueueLimit` の設定が優先されます。  
  
## 使用例  
 以下の例では、次の環境において aspnet.config ファイルで ASP.NET プロセス全体の動作を構成する方法を示します。  
  
-   アプリケーションが [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] アプリケーション プールでホストされている。  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] が統合モードで実行されている。  
  
-   アプリケーションが [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] 以降を使用している。  
  
 この例で指定している値は既定値です。  
  
```  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## 要素情報  
  
|||  
|-|-|  
|名前空間||  
|スキーマ名||  
|検証ファイル||  
|空も使用できる||  
  
## 参照  
 [\<system.web\> 要素 \(Web 設定\)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)