---
title: "&lt;追加&gt;要素&lt;リスナー&gt;の&lt;トレース&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
caps.latest.revision: "24"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bbb74d9a542833a96c61bcc09f6e4e5f0807843d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;追加&gt;要素&lt;リスナー&gt;の&lt;トレース&gt;
リスナーを追加、**リスナー**コレクション。  
  
 \<configuration>  
\<system.diagnostics >  
\<トレース >  
\<リスナー >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**type**|必須の属性です。<br /><br /> リスナーの種類を指定します。 指定された要件を満たしている文字列を使用する必要があります[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。|  
|**initializeData**|省略可能な属性です。<br /><br /> 指定したクラスのコンス トラクターに渡された文字列。|  
|**name**|省略可能な属性です。<br /><br /> リスナーの名前を指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|リスナーにフィルターを追加、`Listeners`トレースのコレクション。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`listeners`|リスナーを収集すると、ストアを指定し、メッセージをルーティングします。 リスナーでは、適切なターゲットのトレースを出力します。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
## <a name="remarks"></a>コメント  
 <xref:System.Diagnostics.Debug>と<xref:System.Diagnostics.Trace>クラスが同じ**リスナー**コレクション。 これらのクラスのいずれかで、コレクションに、リスナー オブジェクトを追加する場合、その他のクラスは、同じリスナーを使用します。 リスナー クラスから派生して、<xref:System.Diagnostics.TraceListener>です。  
  
 指定しない場合、`name`トレース リスナの属性、<xref:System.Diagnostics.TraceListener.Name%2A>のトレース リスナーの既定値に空の文字列 ("") です。 アプリケーションに 1 つだけリスナーがある場合は、それを名前を指定せず追加し、名前の空の文字列を指定することで削除します。 ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーを識別および内の個別のトレース リスナーを管理することができますに一意の名前を指定する必要があります、<xref:System.Diagnostics.Debug.Listeners%2A>と<xref:System.Diagnostics.Trace.Listeners%2A>コレクション。  
  
> [!NOTE]
>  その型の 1 つだけのトレース リスナーに結果の名前を指定し、名前に追加されている、同じ種類のと同じ 2 つ以上のトレース リスナーを追加する、`Listeners`コレクション。 、に複数の同一のリスナーがプログラムで追加することができます、`Listeners`コレクション。  
  
 値、 **initializeData**属性を作成するリスナーの種類によって異なります。 すべてのトレース リスナーを指定することが必要と**initializeData**です。  
  
> [!NOTE]
>  使用すると、`initializeData`属性を受け取ることがあります、コンパイラの警告「'initializeData' 属性は宣言されていません」。 この警告の原因は、構成設定は、抽象基本クラスに対して検証されます<xref:System.Diagnostics.TraceListener>、これは認識されません、`initializeData`属性。 通常、パラメーターを受け取るコンス トラクターを持つトレース リスナーの実装のためには、この警告を無視することができます。  
  
 次の表は、.NET Framework に含まれているトレース リスナーを示しの値を記述、 **initializeData**属性。  
  
|トレース リスナー クラス|initializeData 属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream`値を<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>コンス トラクターです。  設定、`initializeData`属性を"`true`"書き込むトレースとデバッグ出力を<xref:System.Console.Error%2A?displayProperty=nameWithType>です。"`false`"に書き込めません<xref:System.Console.Out%2A?displayProperty=nameWithType>です。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|ファイルの名前、<xref:System.Diagnostics.DelimitedListTraceListener>を書き込みます。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベント ログ ソースの名前の名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.EventSchemaTraceListener>を書き込みます。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.TextWriterTraceListener>を書き込みます。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.XmlWriterTraceListener>を書き込みます。|  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示しています。 **\<追加 >**リスナーを追加する要素`MyListener`と`MyEventListener`を、**リスナー**コレクション。 `MyListener`という名前のファイルを作成`MyListener.log`し、ファイルに出力を書き込みます。 `MyEventListener`イベント ログにエントリを作成します。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [トレース リスナー](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
