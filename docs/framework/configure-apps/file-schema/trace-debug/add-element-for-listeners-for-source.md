---
title: '&lt;追加&gt;要素&lt;リスナー&gt;の&lt;ソース&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ba8ff652003a9167ec370643797ac9300b83889a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a>&lt;追加&gt;要素&lt;リスナー&gt;の&lt;ソース&gt;
トレース ソースの `Listeners` コレクションにリスナーを追加します。  
  
 \<configuration>  
\<system.diagnostics >  
\<ソース >  
\<ソース >  
\<リスナー >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`type`|リスナーを参照している場合を除き、必須の属性を`sharedListeners`をコレクションには名前で参照するだけでかまいませんがケース (を参照してください、[例](#example))。<br /><br /> リスナーの種類を指定します。 指定された要件を満たしている文字列を使用する必要があります[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定したクラスのコンス トラクターに渡された文字列。 A<xref:System.Configuration.ConfigurationException>クラスには、文字列を受け取るコンス トラクターがない場合にスローされます。|  
|`name`|省略可能な属性です。<br /><br /> リスナーの名前を指定します。|  
|`traceOutputOptions`|省略可能な属性です。<br /><br /> 指定します、<xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>トレース リスナーのプロパティの値。|  
|[カスタム属性]|省略可能な属性です。<br /><br /> によって識別される属性をリスナー固有の値を指定、<xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A>そのリスナー メソッドです。 <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 余分な属性の例には、<xref:System.Diagnostics.DelimitedListTraceListener>クラスです。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
|`source`|トレース メッセージを開始するトレース ソースを指定します。|  
|`listeners`|収集、保管、およびメッセージをルーティングするリスナーを指定します。|  
  
## <a name="remarks"></a>コメント  
 .NET Framework に付属のリスナー クラスから派生して、<xref:System.Diagnostics.TraceListener>クラスです。  
  
 指定しない場合、`name`トレース リスナの属性、<xref:System.Diagnostics.TraceListener.Name%2A>トレース リスナーのプロパティの既定値は空の文字列 ("") です。 アプリケーションでは、1 つだけリスナーが、それを追加するには、名前を指定せずと名前の空の文字列を指定することで削除することができます。 ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーを識別および内の個々 のトレース リスナーを管理することができますに一意の名前を指定する必要があります、<xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>コレクション。  
  
> [!NOTE]
>  その型の 1 つだけのトレース リスナーに結果の名前を指定し、名前に追加されている、同じ種類のと同じ 2 つ以上のトレース リスナーを追加する、`Listeners`コレクション。 、に複数の同一のリスナーがプログラムで追加することができます、`Listeners`コレクション。  
  
 値、`initializeData`属性を作成するリスナーの種類によって異なります。 すべてのトレース リスナーを指定することが必要と`initializeData`です。  
  
> [!NOTE]
>  使用すると、`initializeData`属性を受け取ることがあります、コンパイラの警告「'initializeData' 属性は宣言されていません」。 この警告の原因は、構成設定は、抽象基本クラスに対して検証されます<xref:System.Diagnostics.TraceListener>、これは認識されません、`initializeData`属性。 通常、パラメーターを受け取るコンス トラクターを持つトレース リスナーの実装のためには、この警告を無視することができます。  
  
 次の表は、.NET Framework に含まれているトレース リスナーを示しの値を記述、`initializeData`属性。  
  
|トレース リスナー クラス|initializeData 属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream`値を<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>コンス トラクターです。  設定、`initializeData`属性を"`true`「書き込むトレースとデバッグの出力を標準エラー ストリーム; に設定」`false`"を標準出力ストリームに書き込めません。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|ファイルの名前、<xref:System.Diagnostics.DelimitedListTraceListener>を書き込みます。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.EventSchemaTraceListener>を書き込みます。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.TextWriterTraceListener>を書き込みます。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|ファイルの名前を<xref:System.Diagnostics.XmlWriterTraceListener>を書き込みます。|  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示しています。`<add>`リスナーを追加する要素`console`と`textListener`を、`Listeners`トレース ソースのコレクション`TraceSourceApp`です。 `textListener`ファイル myListener.log にリスナーがトレース出力を書き込みます。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [トレース リスナー](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
