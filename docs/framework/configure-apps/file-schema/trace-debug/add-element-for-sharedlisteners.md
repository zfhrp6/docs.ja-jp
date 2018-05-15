---
title: '&lt;追加&gt;要素&lt;sharedListeners&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 27d83ba706b4d93b4ac5426bf5bae59b4bfc0d9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a><span data-ttu-id="9a676-102">&lt;追加&gt;要素&lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="9a676-102">&lt;add&gt; Element for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="9a676-103">`sharedListeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="9a676-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="9a676-104">`sharedListeners` リスナーのコレクションをするには[\<ソース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)または[\<トレース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)を参照できます。</span><span class="sxs-lookup"><span data-stu-id="9a676-104">`sharedListeners` is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="9a676-105">既定では、リスナーに、`sharedListeners`にコレクションが配置されていない、`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="9a676-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="9a676-106">名前で追加する必要があります、 [\<ソース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)または[\<トレース >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a676-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="9a676-107">内のリスナーを取得することはできません、`sharedListeners`実行時にコード内のコレクション。</span><span class="sxs-lookup"><span data-stu-id="9a676-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="9a676-108">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9a676-108">\<configuration></span></span>  
<span data-ttu-id="9a676-109">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="9a676-109">\<system.diagnostics></span></span>  
<span data-ttu-id="9a676-110">\<sharedListeners > 要素</span><span class="sxs-lookup"><span data-stu-id="9a676-110">\<sharedListeners> Element</span></span>  
<span data-ttu-id="9a676-111">\<add></span><span class="sxs-lookup"><span data-stu-id="9a676-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a676-112">構文</span><span class="sxs-lookup"><span data-stu-id="9a676-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a676-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9a676-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9a676-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a676-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a676-115">属性</span><span class="sxs-lookup"><span data-stu-id="9a676-115">Attributes</span></span>  
  
|<span data-ttu-id="9a676-116">属性</span><span class="sxs-lookup"><span data-stu-id="9a676-116">Attribute</span></span>|<span data-ttu-id="9a676-117">説明</span><span class="sxs-lookup"><span data-stu-id="9a676-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="9a676-118">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="9a676-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="9a676-119">共有リスナーを追加するために使用するリスナーの名前を指定、`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="9a676-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="9a676-120">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="9a676-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="9a676-121">リスナーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="9a676-121">Specifies the type of the listener.</span></span> <span data-ttu-id="9a676-122">指定された要件を満たしている文字列を使用する必要があります[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a676-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="9a676-123">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="9a676-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9a676-124">指定したクラスのコンス トラクターに渡された文字列。</span><span class="sxs-lookup"><span data-stu-id="9a676-124">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a676-125">子要素</span><span class="sxs-lookup"><span data-stu-id="9a676-125">Child Elements</span></span>  
  
|<span data-ttu-id="9a676-126">要素</span><span class="sxs-lookup"><span data-stu-id="9a676-126">Element</span></span>|<span data-ttu-id="9a676-127">説明</span><span class="sxs-lookup"><span data-stu-id="9a676-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a676-128">\<filter></span><span class="sxs-lookup"><span data-stu-id="9a676-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="9a676-129">`sharedListeners` コレクションのリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="9a676-129">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a676-130">親要素</span><span class="sxs-lookup"><span data-stu-id="9a676-130">Parent Elements</span></span>  
  
|<span data-ttu-id="9a676-131">要素</span><span class="sxs-lookup"><span data-stu-id="9a676-131">Element</span></span>|<span data-ttu-id="9a676-132">説明</span><span class="sxs-lookup"><span data-stu-id="9a676-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9a676-133">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="9a676-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9a676-134">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="9a676-134">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="9a676-135">任意のソースまたはトレース要素を参照できるリスナーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="9a676-135">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a676-136">コメント</span><span class="sxs-lookup"><span data-stu-id="9a676-136">Remarks</span></span>  
 <span data-ttu-id="9a676-137">.NET Framework に付属のリスナー クラスから派生して、<xref:System.Diagnostics.TraceListener>クラスです。</span><span class="sxs-lookup"><span data-stu-id="9a676-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="9a676-138">値、`name`属性を使用する共有リスナーを追加して、`Listeners`トレースまたはトレース ソースのいずれかのコレクション。</span><span class="sxs-lookup"><span data-stu-id="9a676-138">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="9a676-139">値、`initializeData`属性を作成するリスナーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9a676-139">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="9a676-140">すべてのトレース リスナーを指定することが必要と`initializeData`です。</span><span class="sxs-lookup"><span data-stu-id="9a676-140">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a676-141">使用すると、`initializeData`属性を受け取ることがあります、コンパイラの警告「'initializeData' 属性は宣言されていません」。</span><span class="sxs-lookup"><span data-stu-id="9a676-141">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="9a676-142">この警告の原因は、構成設定は、抽象基本クラスに対して検証されます<xref:System.Diagnostics.TraceListener>、これは認識されません、`initializeData`属性。</span><span class="sxs-lookup"><span data-stu-id="9a676-142">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="9a676-143">通常、パラメーターを受け取るコンス トラクターを持つトレース リスナーの実装のためには、この警告を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="9a676-143">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="9a676-144">次の表は、.NET Framework に含まれているトレース リスナーを示しの値を記述、`initializeData`属性。</span><span class="sxs-lookup"><span data-stu-id="9a676-144">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="9a676-145">トレース リスナー クラス</span><span class="sxs-lookup"><span data-stu-id="9a676-145">Trace listener class</span></span>|<span data-ttu-id="9a676-146">initializeData 属性値</span><span class="sxs-lookup"><span data-stu-id="9a676-146">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="9a676-147">`useErrorStream`値を<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="9a676-147">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="9a676-148">設定、`initializeData`属性を"`true`「書き込むトレースとデバッグの出力を標準エラー ストリーム; に設定」`false`"を標準出力ストリームに書き込めません。</span><span class="sxs-lookup"><span data-stu-id="9a676-148">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="9a676-149">ファイルの名前、<xref:System.Diagnostics.DelimitedListTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9a676-149">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9a676-150">既存のイベント ログ ソースの名前。</span><span class="sxs-lookup"><span data-stu-id="9a676-150">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9a676-151">ファイルの名前を<xref:System.Diagnostics.EventSchemaTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9a676-151">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9a676-152">ファイルの名前を<xref:System.Diagnostics.TextWriterTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9a676-152">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="9a676-153">ファイルの名前を<xref:System.Diagnostics.XmlWriterTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9a676-153">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="9a676-154">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="9a676-154">Configuration File</span></span>  
 <span data-ttu-id="9a676-155">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a676-155">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a676-156">例</span><span class="sxs-lookup"><span data-stu-id="9a676-156">Example</span></span>  
 <span data-ttu-id="9a676-157">次の例は、使用する方法を示しています。`<add>`要素を追加する、 <xref:System.Diagnostics.TextWriterTraceListener> `textListener`を、`sharedListeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="9a676-157">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="9a676-158">`textListener` 名前で追加された、`Listeners`トレース ソースのコレクション`TraceSourceApp`です。</span><span class="sxs-lookup"><span data-stu-id="9a676-158">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="9a676-159">`textListener`ファイル myListener.log にリスナーがトレース出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9a676-159">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a676-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a676-160">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="9a676-161">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="9a676-161">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="9a676-162">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="9a676-162">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
