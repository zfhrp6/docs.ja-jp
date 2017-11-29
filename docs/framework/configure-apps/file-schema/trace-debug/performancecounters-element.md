---
title: "&lt;performanceCounters&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f7fdbb244663e5114880437a5a508270c80a9c79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltperformancecountersgt-element"></a>&lt;performanceCounters&gt;要素
パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。  
  
 \<configuration>  
\<system.diagnostics >  
\<performanceCounters >  
  
## <a name="syntax"></a>構文  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|filemappingsize|必須の属性です。<br /><br /> パフォーマンス カウンターが共有するグローバル メモリのバイト単位のサイズを指定します。 既定値は 524288 です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`Configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
  
## <a name="remarks"></a>コメント  
 パフォーマンス カウンターでは、メモリ マップト ファイルまたは共有メモリを使用して、パフォーマンス データを公開します。  共有メモリのサイズは、一度に使用できるインスタンスの数を決定します。  共有メモリの 2 種類があります。 グローバル共有メモリと別の共有メモリです。  グローバル共有メモリは、.NET Framework バージョン 1.0 または 1.1 でインストールされているすべてのパフォーマンス カウンターのカテゴリを使用します。  .NET Framework version 2.0 にインストールされているパフォーマンス カウンター カテゴリは、独自のメモリを持つ各パフォーマンス カウンター カテゴリ別の共有メモリを使用します。  
  
 グローバル共有メモリのサイズは、構成ファイルでのみ設定できます。  既定のサイズは 524, 288 バイト、最大サイズは 33,554, 432 (バイト単位)、最小サイズは 32,768 バイトです。  グローバル共有メモリは、すべてのプロセスとカテゴリが共有しているために、最初の作成者は、サイズを指定します。  アプリケーション構成ファイルのサイズを定義する場合、そのサイズは場合にのみ使用アプリケーションが実行するパフォーマンス カウンターの原因となる最初のアプリケーション。  したがって、正しい場所を指定、`filemappingsize`値は、Machine.config ファイルです。  個々 のパフォーマンス カウンターによって、最終的に多数の異なる名前を持つパフォーマンス カウンター インスタンスが作成される場合、グローバル共有メモリがなくなったグローバル共有メモリ内のメモリを解放できません。  
  
 別の共有メモリのサイズをレジストリの DWORD FileMappingSize 値キー hkey_local_machine \system\currentcontrolset\services\\*\<カテゴリ名 >*\Performance が参照されています。最初に、構成ファイル内のグローバル共有メモリに指定された値に続きます。 FileMappingSize 値が存在しないかどうかは、別の共有メモリのサイズが 4 分の 1 に設定されている (1/4)、構成ファイルのグローバル設定。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
