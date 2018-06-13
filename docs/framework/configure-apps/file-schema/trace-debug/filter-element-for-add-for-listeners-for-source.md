---
title: '&lt;フィルター&gt;要素&lt;追加&gt;の&lt;リスナー&gt;の&lt;ソース&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 763d15a1391d8c9539d5fb92d4ad50132c17c065
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745780"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a>&lt;フィルター&gt;要素&lt;追加&gt;の&lt;リスナー&gt;の&lt;ソース&gt;
トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。  
  
 \<configuration>  
\<system.diagnostics >  
\<ソース >  
\<ソース >  
\<リスナー >  
\<add>  
\<フィルター >  
  
## <a name="syntax"></a>構文  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`type`|必須の属性です。<br /><br /> 継承する必要がありますフィルターの種類を指定します、<xref:System.Diagnostics.TraceFilter>クラスです。 を、型に対応する型の名前空間で修飾された名前を使用する<xref:System.Type.FullName%2A>プロパティを使用するかに対応するアセンブリ情報を含め、完全修飾型名、<xref:System.Type.AssemblyQualifiedName%2A>プロパティです。 完全修飾型名については、次を参照してください。[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定したフィルター クラスのコンス トラクターに渡された文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
|`source`|トレース メッセージを開始するトレース ソースを指定します。|  
|`listeners`|収集、保管、およびメッセージをルーティングするリスナーが含まれています。 リスナーでは、適切なターゲットのトレースを出力します。|  
|`add`|トレース ソースの `Listeners` コレクションにリスナーを追加します。|  
  
## <a name="remarks"></a>コメント  
 `<filter>`で要素を含める必要があります、`<add>`リスナーの種類を指定するトレース ソースのリスナーの要素で定義されているリスナーの名前だけでなく、 [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)です。 リスナーがで定義されている場合、 [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)、その要素には、そのリスナーのフィルターを定義する必要があります。  
  
 この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`<filter>`リスナーにフィルターを追加する要素`console`で、`Listeners`トレース ソースのコレクション`myTraceSource`、レベルを指定して、フィルター イベントとして`Error`です。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
