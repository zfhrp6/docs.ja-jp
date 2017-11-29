---
title: "&lt;トレース&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 157adb6c7317aa047976cdb9e30711d20c9e543b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttracegt-element"></a>&lt;トレース&gt;要素
トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。  
  
 \<configuration>  
\<system.diagnostics >  
\<トレース >  
  
## <a name="syntax"></a>構文  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`autoflush`|省略可能な属性です。<br /><br /> トレース リスナーが、すべての書き込み操作の後に、出力バッファーを自動的にフラッシュするかどうかを指定します。|  
|`indentsize`|省略可能な属性です。<br /><br /> インデントを設定する空白の数を指定します。|  
|`useGlobalLock`|省略可能な属性です。<br /><br /> グローバル ロックを使用するかどうかを示します。|  
  
## <a name="autoflush-attribute"></a>autoflush 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|出力バッファーを自動的にフラッシュしません。 既定値です。|  
|`true`|自動的に出力バッファーをフラッシュします。|  
  
## <a name="usegloballock-attribute"></a>属性を用意されました  
  
|値|説明|  
|-----------|-----------------|  
|`false`|リスナーがスレッド セーフである場合、グローバル ロックを使用しません。それ以外の場合、グローバル ロックを使用します。|  
|`true`|リスナーは、スレッド セーフであるかどうかに関係なくグローバル ロックを使用します。 既定値です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|リスナーを収集すると、ストアを指定し、メッセージをルーティングします。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`<trace>`リスナーを追加する要素`MyListener`を`Listeners`コレクション。 `MyListener`という名前のファイルを作成`MyListener.log`し、ファイルに出力を書き込みます。 `useGlobalLock`属性に設定されている`false`、それが原因で、グローバル ロック トレース リスナーがスレッド セーフである場合に使用することはできません。 `autoflush`属性に設定されている`true`、それが原因かどうかに関係なく、ファイルに書き込むトレース リスナー、<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>メソッドが呼び出されます。 `indentsize`属性が 0 (ゼロ)。 これにより、0 個のスペースのインデントを設定するリスナーに設定されているときに、<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>メソッドが呼び出されます。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
