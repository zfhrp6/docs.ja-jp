---
title: '&lt;フィルター&gt;要素&lt;追加&gt;の&lt;リスナー&gt;の&lt;トレース&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 095212f73adb906d9d80db747c331c436c1cf846
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="3ac48-102">&lt;フィルター&gt;要素&lt;追加&gt;の&lt;リスナー&gt;の&lt;トレース&gt;</span><span class="sxs-lookup"><span data-stu-id="3ac48-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="3ac48-103">リスナーにフィルターを追加、`Listeners`トレースのコレクション。</span><span class="sxs-lookup"><span data-stu-id="3ac48-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="3ac48-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3ac48-104">\<configuration></span></span>  
<span data-ttu-id="3ac48-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="3ac48-105">\<system.diagnostics></span></span>  
<span data-ttu-id="3ac48-106">\<トレース ></span><span class="sxs-lookup"><span data-stu-id="3ac48-106">\<trace></span></span>  
<span data-ttu-id="3ac48-107">\<リスナー ></span><span class="sxs-lookup"><span data-stu-id="3ac48-107">\<listeners></span></span>  
<span data-ttu-id="3ac48-108">\<add></span><span class="sxs-lookup"><span data-stu-id="3ac48-108">\<add></span></span>  
<span data-ttu-id="3ac48-109">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="3ac48-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ac48-110">構文</span><span class="sxs-lookup"><span data-stu-id="3ac48-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ac48-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3ac48-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3ac48-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ac48-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ac48-113">属性</span><span class="sxs-lookup"><span data-stu-id="3ac48-113">Attributes</span></span>  
  
|<span data-ttu-id="3ac48-114">属性</span><span class="sxs-lookup"><span data-stu-id="3ac48-114">Attribute</span></span>|<span data-ttu-id="3ac48-115">説明</span><span class="sxs-lookup"><span data-stu-id="3ac48-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="3ac48-116">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3ac48-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="3ac48-117">継承する必要がありますフィルターの種類を指定します、<xref:System.Diagnostics.TraceFilter>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3ac48-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="3ac48-118">を、型に対応する型の名前空間で修飾された名前を使用する<xref:System.Type.FullName%2A>プロパティを使用するかに対応するアセンブリ情報を含め、完全修飾型名、<xref:System.Type.AssemblyQualifiedName%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3ac48-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="3ac48-119">完全修飾型名については、次を参照してください。[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="3ac48-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="3ac48-120">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="3ac48-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3ac48-121">指定したフィルター クラスのコンス トラクターに渡された文字列。</span><span class="sxs-lookup"><span data-stu-id="3ac48-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ac48-122">子要素</span><span class="sxs-lookup"><span data-stu-id="3ac48-122">Child Elements</span></span>  
 <span data-ttu-id="3ac48-123">なし。</span><span class="sxs-lookup"><span data-stu-id="3ac48-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ac48-124">親要素</span><span class="sxs-lookup"><span data-stu-id="3ac48-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3ac48-125">要素</span><span class="sxs-lookup"><span data-stu-id="3ac48-125">Element</span></span>|<span data-ttu-id="3ac48-126">説明</span><span class="sxs-lookup"><span data-stu-id="3ac48-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3ac48-127">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="3ac48-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3ac48-128">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="3ac48-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="3ac48-129">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="3ac48-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="3ac48-130">収集、保管、およびメッセージをルーティングするリスナーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ac48-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="3ac48-131">リスナーでは、適切なターゲットのトレースを出力します。</span><span class="sxs-lookup"><span data-stu-id="3ac48-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="3ac48-132">`Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="3ac48-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ac48-133">コメント</span><span class="sxs-lookup"><span data-stu-id="3ac48-133">Remarks</span></span>  
 <span data-ttu-id="3ac48-134">`<filter>`で要素を含める必要があります、`<add>`リスナーの種類を指定する、トレース リスナーの要素で定義されているリスナーの名前だけでなく、 [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="3ac48-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="3ac48-135">リスナーがで定義されている場合、 [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)、その要素には、そのリスナーのフィルターを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ac48-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="3ac48-136">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="3ac48-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ac48-137">例</span><span class="sxs-lookup"><span data-stu-id="3ac48-137">Example</span></span>  
 <span data-ttu-id="3ac48-138">次の例を使用する方法を示しています、`<filter>`リスナーにフィルターを追加する要素`console`で、`Listeners`としてフィルター イベント レベルを指定して、トレース`Error`です。</span><span class="sxs-lookup"><span data-stu-id="3ac48-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ac48-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ac48-139">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="3ac48-140">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="3ac48-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
