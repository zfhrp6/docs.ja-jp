---
title: "&lt;performanceCounters&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<perfomanceCounters> 要素"
  - "performanceCounters 要素"
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;performanceCounters&gt; 要素
パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。  
  
## 構文  
  
```  
<performanceCounters filemappingsize="524288" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|filemappingsize|必須の属性です。<br /><br /> パフォーマンス カウンターが共有するグローバル メモリのサイズをバイト単位で指定します。  既定値は 524288 です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`Configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
  
## 解説  
 パフォーマンス カウンターは、メモリ マップト ファイル \(共有メモリ\) を使用してパフォーマンス データを公開します。共有メモリのサイズによって、一度に使用できるインスタンスの数が決まります。共有メモリには、グローバル共有メモリと個別共有メモリの 2 種類があります。グローバル共有メモリは、.NET Framework Version 1.0 または 1.1 と共にインストールされるすべてのパフォーマンス カウンター カテゴリで使用されます。.NET Framework Version 2.0 と共にインストールされるパフォーマンス カウンター カテゴリでは、個別共有メモリが使用されます。この場合、各パフォーマンス カウンター カテゴリが独自のメモリを持ちます。  
  
 グローバル共有メモリのサイズは、構成ファイル内でのみ設定できます。既定のサイズは 524,288 バイト、最大サイズは 33,554,432 バイト、最小サイズは 32,768 バイトです。グローバル共有メモリはすべてのプロセスおよびカテゴリで共有されるため、最初の作成者がサイズを指定します。アプリケーション構成ファイルにサイズを定義すると、指定したサイズは、そのアプリケーションが最初にパフォーマンス カウンターを実行する場合にのみ使用されます。したがって、`filemappingsize` 値は、Machine.config ファイルで指定する必要があります。グローバル共有メモリ内のメモリはパフォーマンス カウンターごとに解放できないため、異なる名前を使用してパフォーマンス カウンターのインスタンスを大量に作成すると、最終的にはグローバル共有メモリを使い果たすことになります。  
  
 個別共有メモリのサイズは、レジストリ キーの HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\*\<category name\>*\\Performance の DWORD FileMappingSize の値は、構成ファイル内のグローバル共有メモリに指定した値によって、その後に最初に参照されます。  FileMappingSize の値が存在しない場合、個別共有メモリのサイズは、構成ファイル内のグローバル設定の値の 4 分の 1 に設定されます。  
  
## 参照  
 <xref:System.Diagnostics.PerformanceCounter>   
 <xref:System.Diagnostics.PerformanceCounterCategory>   
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>   
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>