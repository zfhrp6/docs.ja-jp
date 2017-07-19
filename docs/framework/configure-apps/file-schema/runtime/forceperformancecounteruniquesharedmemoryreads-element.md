---
title: "&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; 要素 | Microsoft Docs"
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
  - "<forcePerformanceCounterUniqueSharedMemoryReads> 要素"
  - "forcePerformanceCounterUniqueSharedMemoryReads 要素"
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; 要素
PerfCounter.dll がカテゴリ固有の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを判断するために .NET Framework Version 1.1 アプリケーションの CategoryOptions レジストリ設定を使用するかどうかを指定します。  
  
## 構文  
  
```  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> PerfCounter.dll がカテゴリ固有の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを判断するために CategoryOptions レジストリ設定を使用するかどうかを示します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|PerfCounter.dll では、CategoryOptions レジストリ設定が使用されません。これが既定値です。|  
|`true`|PerfCounter.dll では、CategoryOptions レジストリ設定が使用されます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] より前のバージョンの .NET Framework では、読み込まれた PerfCounter.dll のバージョンは、プロセスに読み込まれたランタイムに対応します。  コンピューターに、.NET Framework Version 1.1 と [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] の両方がインストールされている場合、.NET Framework 1.1 アプリケーションは .NET Framework 1.1 バージョンの PerfCounter.dll を読み込みます。  [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 以降では、インストールされている最新のバージョンの PerfCounter.dll が読み込まれます。  これにより、.NET Framework 1.1 アプリケーションは、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] がコンピューターにインストールされている場合に、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] バージョンの PerfCounter.dll を読み込みます。  
  
 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 以降では、パフォーマンス カウンターを使用する場合に、PerfCounter.dll は各プロバイダーの CategoryOptions レジストリ エントリをチェックして、カテゴリ固有の共有メモリとグローバル共有メモリのどちらから読み取る必要があるかを判断します。  .NET Framework 1.1 PerfCounter.dll は、カテゴリ固有の共有メモリを認識しないため、このレジストリ エントリを読み取りません。常にグローバル共有メモリから読み取ります。  
  
 下位互換性を維持するために、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll は、.NET Framework 1.1 アプリケーションで実行されている場合に、CategoryOptions レジストリ エントリをチェックしません。  .NET Framework 1.1 PerfCounter.dll と同様に、単純にグローバル共有メモリを使用します。  ただし、`<forcePerformanceCounterUniqueSharedMemoryReads>` 要素を有効にすることで、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll に対してレジストリ設定をチェックするように指示できます。  
  
> [!NOTE]
>  `<forcePerformanceCounterUniqueSharedMemoryReads>` 要素を有効にしても、カテゴリ固有の共有メモリが使用されるという保証はありません。  `true` を有効にする設定は、PerfCounter.dll が CategoryOptions レジストリ設定を参照する原因にしかなりません。  CategoryOptions の既定の設定では、カテゴリ固有の共有メモリが使用されます。ただし、CategoryOptions を変更して、グローバル共有メモリを使用するように指示できます。  
  
 CategoryOptions 設定を含むレジストリ キーは、HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\の categoryName\\Performance\<\>です。  既定では、CategoryOptions は 3 に設定されます。これは、PerfCounter.dll に対してカテゴリ固有の共有メモリを使用するように指示します。  CategoryOptions が 0 に設定されている場合、PerfCounter.dll はグローバル共有メモリを使用します。  インスタンス データは、作成されるインスタンスの名前が再利用されるインスタンスの名前と同じ場合にのみ再利用されます。  すべてのバージョンで、カテゴリに書き込むことができます。  CategoryOptions が 1 に設定されている場合は、グローバル共有メモリが使用されますが、インスタンス データは、カテゴリ名の長さが再利用されるカテゴリと同じ場合にのみ再利用できます。  
  
 設定 0 および 1 は、メモリ リークと、パフォーマンス カウンター メモリの不足を引き起こすことがあります。  
  
## 使用例  
 PerfCounter.dll がカテゴリ固有の共有メモリを使用する必要があるかどうかを判断するために CategoryOptions レジストリ エントリを参照する必要があることを指定する方法を次の例に示します。  
  
```  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)