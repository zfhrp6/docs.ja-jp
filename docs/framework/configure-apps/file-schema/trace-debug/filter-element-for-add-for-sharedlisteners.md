---
title: "&lt;フィルター&gt;要素&lt;追加&gt;の&lt;sharedListeners&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bc3f97619c8ec28a61a9a51b431581383558a7d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltsharedlistenersgt"></a>&lt;フィルター&gt;要素&lt;追加&gt;の&lt;sharedListeners&gt;
`sharedListeners` コレクションのリスナーにフィルターを追加します。  
  
 \<configuration>  
\<system.diagnostics >  
\<sharedListeners > 要素  
\<add>  
\<フィルター >  
  
## <a name="syntax"></a>構文  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**type**|必須の属性です。<br /><br /> フィルターの種類を指定します。 型の完全名のみを使用することができます (の形式で、<xref:System.Type.FullName%2A?displayProperty=nameWithType>プロパティ)、アセンブリ情報を含め、完全修飾型名を使用することもできます (の形式で、<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>プロパティ)。 完全修飾型名を作成する方法については、次を参照してください。[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。|  
|**initializeData**|省略可能な属性です。<br /><br /> 指定したクラスのコンス トラクターに渡された文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sharedListeners`|任意のソースまたはトレース要素を参照できるリスナーのコレクション。|  
|`add`|リスナーを追加、 **sharedListeners**コレクション。|  
  
## <a name="remarks"></a>コメント  
 リスナーがで定義されている場合、`<add>`の要素、`<sharedListeners>`要素、そのリスナーのフィルターで定義する必要があります、`<filter>`はの子要素、`<add>`要素。  
  
 この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`<filter>`トレース リスナーにフィルターを追加する要素`console`で、`sharedListeners`コレクション。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Diagnostics.TraceFilter>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceSource>  
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
