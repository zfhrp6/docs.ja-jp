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
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="8bccd-102">&lt;フィルター&gt;要素&lt;追加&gt;の&lt;リスナー&gt;の&lt;ソース&gt;</span><span class="sxs-lookup"><span data-stu-id="8bccd-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="8bccd-103">トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="8bccd-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="8bccd-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8bccd-104">\<configuration></span></span>  
<span data-ttu-id="8bccd-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="8bccd-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8bccd-106">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="8bccd-106">\<sources></span></span>  
<span data-ttu-id="8bccd-107">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="8bccd-107">\<source></span></span>  
<span data-ttu-id="8bccd-108">\<リスナー ></span><span class="sxs-lookup"><span data-stu-id="8bccd-108">\<listeners></span></span>  
<span data-ttu-id="8bccd-109">\<add></span><span class="sxs-lookup"><span data-stu-id="8bccd-109">\<add></span></span>  
<span data-ttu-id="8bccd-110">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="8bccd-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bccd-111">構文</span><span class="sxs-lookup"><span data-stu-id="8bccd-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bccd-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8bccd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8bccd-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8bccd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bccd-114">属性</span><span class="sxs-lookup"><span data-stu-id="8bccd-114">Attributes</span></span>  
  
|<span data-ttu-id="8bccd-115">属性</span><span class="sxs-lookup"><span data-stu-id="8bccd-115">Attribute</span></span>|<span data-ttu-id="8bccd-116">説明</span><span class="sxs-lookup"><span data-stu-id="8bccd-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="8bccd-117">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="8bccd-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="8bccd-118">継承する必要がありますフィルターの種類を指定します、<xref:System.Diagnostics.TraceFilter>クラスです。</span><span class="sxs-lookup"><span data-stu-id="8bccd-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="8bccd-119">を、型に対応する型の名前空間で修飾された名前を使用する<xref:System.Type.FullName%2A>プロパティを使用するかに対応するアセンブリ情報を含め、完全修飾型名、<xref:System.Type.AssemblyQualifiedName%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8bccd-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="8bccd-120">完全修飾型名については、次を参照してください。[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="8bccd-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="8bccd-121">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="8bccd-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8bccd-122">指定したフィルター クラスのコンス トラクターに渡された文字列。</span><span class="sxs-lookup"><span data-stu-id="8bccd-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bccd-123">子要素</span><span class="sxs-lookup"><span data-stu-id="8bccd-123">Child Elements</span></span>  
 <span data-ttu-id="8bccd-124">なし。</span><span class="sxs-lookup"><span data-stu-id="8bccd-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8bccd-125">親要素</span><span class="sxs-lookup"><span data-stu-id="8bccd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8bccd-126">要素</span><span class="sxs-lookup"><span data-stu-id="8bccd-126">Element</span></span>|<span data-ttu-id="8bccd-127">説明</span><span class="sxs-lookup"><span data-stu-id="8bccd-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8bccd-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="8bccd-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8bccd-129">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="8bccd-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="8bccd-130">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="8bccd-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="8bccd-131">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="8bccd-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8bccd-132">収集、保管、およびメッセージをルーティングするリスナーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8bccd-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="8bccd-133">リスナーでは、適切なターゲットのトレースを出力します。</span><span class="sxs-lookup"><span data-stu-id="8bccd-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="8bccd-134">トレース ソースの `Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="8bccd-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bccd-135">コメント</span><span class="sxs-lookup"><span data-stu-id="8bccd-135">Remarks</span></span>  
 <span data-ttu-id="8bccd-136">`<filter>`で要素を含める必要があります、`<add>`リスナーの種類を指定するトレース ソースのリスナーの要素で定義されているリスナーの名前だけでなく、 [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="8bccd-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="8bccd-137">リスナーがで定義されている場合、 [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)、その要素には、そのリスナーのフィルターを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8bccd-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="8bccd-138">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="8bccd-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bccd-139">例</span><span class="sxs-lookup"><span data-stu-id="8bccd-139">Example</span></span>  
 <span data-ttu-id="8bccd-140">次の例を使用する方法を示しています、`<filter>`リスナーにフィルターを追加する要素`console`で、`Listeners`トレース ソースのコレクション`myTraceSource`、レベルを指定して、フィルター イベントとして`Error`です。</span><span class="sxs-lookup"><span data-stu-id="8bccd-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8bccd-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bccd-141">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="8bccd-142">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="8bccd-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
