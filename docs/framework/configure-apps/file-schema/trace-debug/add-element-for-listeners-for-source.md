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
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="dabff-102">&lt;追加&gt;要素&lt;リスナー&gt;の&lt;ソース&gt;</span><span class="sxs-lookup"><span data-stu-id="dabff-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="dabff-103">トレース ソースの `Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="dabff-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="dabff-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dabff-104">\<configuration></span></span>  
<span data-ttu-id="dabff-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="dabff-105">\<system.diagnostics></span></span>  
<span data-ttu-id="dabff-106">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="dabff-106">\<sources></span></span>  
<span data-ttu-id="dabff-107">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="dabff-107">\<source></span></span>  
<span data-ttu-id="dabff-108">\<リスナー ></span><span class="sxs-lookup"><span data-stu-id="dabff-108">\<listeners></span></span>  
<span data-ttu-id="dabff-109">\<add></span><span class="sxs-lookup"><span data-stu-id="dabff-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dabff-110">構文</span><span class="sxs-lookup"><span data-stu-id="dabff-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dabff-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dabff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="dabff-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dabff-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dabff-113">属性</span><span class="sxs-lookup"><span data-stu-id="dabff-113">Attributes</span></span>  
  
|<span data-ttu-id="dabff-114">属性</span><span class="sxs-lookup"><span data-stu-id="dabff-114">Attribute</span></span>|<span data-ttu-id="dabff-115">説明</span><span class="sxs-lookup"><span data-stu-id="dabff-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="dabff-116">リスナーを参照している場合を除き、必須の属性を`sharedListeners`をコレクションには名前で参照するだけでかまいませんがケース (を参照してください、[例](#example))。</span><span class="sxs-lookup"><span data-stu-id="dabff-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="dabff-117">リスナーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="dabff-117">Specifies the type of the listener.</span></span> <span data-ttu-id="dabff-118">指定された要件を満たしている文字列を使用する必要があります[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="dabff-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="dabff-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="dabff-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="dabff-120">指定したクラスのコンス トラクターに渡された文字列。</span><span class="sxs-lookup"><span data-stu-id="dabff-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="dabff-121">A<xref:System.Configuration.ConfigurationException>クラスには、文字列を受け取るコンス トラクターがない場合にスローされます。</span><span class="sxs-lookup"><span data-stu-id="dabff-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="dabff-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="dabff-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="dabff-123">リスナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dabff-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="dabff-124">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="dabff-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="dabff-125">指定します、<xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>トレース リスナーのプロパティの値。</span><span class="sxs-lookup"><span data-stu-id="dabff-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="dabff-126">[カスタム属性]</span><span class="sxs-lookup"><span data-stu-id="dabff-126">[custom attributes]</span></span>|<span data-ttu-id="dabff-127">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="dabff-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="dabff-128">によって識別される属性をリスナー固有の値を指定、<xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A>そのリスナー メソッドです。</span><span class="sxs-lookup"><span data-stu-id="dabff-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="dabff-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 余分な属性の例には、<xref:System.Diagnostics.DelimitedListTraceListener>クラスです。</span><span class="sxs-lookup"><span data-stu-id="dabff-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dabff-130">子要素</span><span class="sxs-lookup"><span data-stu-id="dabff-130">Child Elements</span></span>  
  
|<span data-ttu-id="dabff-131">要素</span><span class="sxs-lookup"><span data-stu-id="dabff-131">Element</span></span>|<span data-ttu-id="dabff-132">説明</span><span class="sxs-lookup"><span data-stu-id="dabff-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dabff-133">\<filter></span><span class="sxs-lookup"><span data-stu-id="dabff-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="dabff-134">トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="dabff-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dabff-135">親要素</span><span class="sxs-lookup"><span data-stu-id="dabff-135">Parent Elements</span></span>  
  
|<span data-ttu-id="dabff-136">要素</span><span class="sxs-lookup"><span data-stu-id="dabff-136">Element</span></span>|<span data-ttu-id="dabff-137">説明</span><span class="sxs-lookup"><span data-stu-id="dabff-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dabff-138">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="dabff-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="dabff-139">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="dabff-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="dabff-140">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="dabff-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="dabff-141">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="dabff-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="dabff-142">収集、保管、およびメッセージをルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="dabff-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dabff-143">コメント</span><span class="sxs-lookup"><span data-stu-id="dabff-143">Remarks</span></span>  
 <span data-ttu-id="dabff-144">.NET Framework に付属のリスナー クラスから派生して、<xref:System.Diagnostics.TraceListener>クラスです。</span><span class="sxs-lookup"><span data-stu-id="dabff-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="dabff-145">指定しない場合、`name`トレース リスナの属性、<xref:System.Diagnostics.TraceListener.Name%2A>トレース リスナーのプロパティの既定値は空の文字列 ("") です。</span><span class="sxs-lookup"><span data-stu-id="dabff-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="dabff-146">アプリケーションでは、1 つだけリスナーが、それを追加するには、名前を指定せずと名前の空の文字列を指定することで削除することができます。</span><span class="sxs-lookup"><span data-stu-id="dabff-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="dabff-147">ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーを識別および内の個々 のトレース リスナーを管理することができますに一意の名前を指定する必要があります、<xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>コレクション。</span><span class="sxs-lookup"><span data-stu-id="dabff-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dabff-148">その型の 1 つだけのトレース リスナーに結果の名前を指定し、名前に追加されている、同じ種類のと同じ 2 つ以上のトレース リスナーを追加する、`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="dabff-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="dabff-149">、に複数の同一のリスナーがプログラムで追加することができます、`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="dabff-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="dabff-150">値、`initializeData`属性を作成するリスナーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="dabff-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="dabff-151">すべてのトレース リスナーを指定することが必要と`initializeData`です。</span><span class="sxs-lookup"><span data-stu-id="dabff-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dabff-152">使用すると、`initializeData`属性を受け取ることがあります、コンパイラの警告「'initializeData' 属性は宣言されていません」。</span><span class="sxs-lookup"><span data-stu-id="dabff-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="dabff-153">この警告の原因は、構成設定は、抽象基本クラスに対して検証されます<xref:System.Diagnostics.TraceListener>、これは認識されません、`initializeData`属性。</span><span class="sxs-lookup"><span data-stu-id="dabff-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="dabff-154">通常、パラメーターを受け取るコンス トラクターを持つトレース リスナーの実装のためには、この警告を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="dabff-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="dabff-155">次の表は、.NET Framework に含まれているトレース リスナーを示しの値を記述、`initializeData`属性。</span><span class="sxs-lookup"><span data-stu-id="dabff-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="dabff-156">トレース リスナー クラス</span><span class="sxs-lookup"><span data-stu-id="dabff-156">Trace listener class</span></span>|<span data-ttu-id="dabff-157">initializeData 属性値</span><span class="sxs-lookup"><span data-stu-id="dabff-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dabff-158">`useErrorStream`値を<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="dabff-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="dabff-159">設定、`initializeData`属性を"`true`「書き込むトレースとデバッグの出力を標準エラー ストリーム; に設定」`false`"を標準出力ストリームに書き込めません。</span><span class="sxs-lookup"><span data-stu-id="dabff-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dabff-160">ファイルの名前、<xref:System.Diagnostics.DelimitedListTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="dabff-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dabff-161">既存のイベント ログ ソースの名前。</span><span class="sxs-lookup"><span data-stu-id="dabff-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dabff-162">ファイルの名前を<xref:System.Diagnostics.EventSchemaTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="dabff-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dabff-163">ファイルの名前を<xref:System.Diagnostics.TextWriterTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="dabff-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dabff-164">ファイルの名前を<xref:System.Diagnostics.XmlWriterTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="dabff-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="dabff-165">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="dabff-165">Configuration File</span></span>  
 <span data-ttu-id="dabff-166">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="dabff-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dabff-167">例</span><span class="sxs-lookup"><span data-stu-id="dabff-167">Example</span></span>  
 <span data-ttu-id="dabff-168">次の例は、使用する方法を示しています。`<add>`リスナーを追加する要素`console`と`textListener`を、`Listeners`トレース ソースのコレクション`TraceSourceApp`です。</span><span class="sxs-lookup"><span data-stu-id="dabff-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="dabff-169">`textListener`ファイル myListener.log にリスナーがトレース出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="dabff-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dabff-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="dabff-170">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="dabff-171">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="dabff-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="dabff-172">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="dabff-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
