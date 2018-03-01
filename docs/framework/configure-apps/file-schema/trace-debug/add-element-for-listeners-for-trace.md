---
title: "&lt;追加&gt;要素&lt;リスナー&gt;の&lt;トレース&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: eb624052c3638cb49abe143ebd4173a5ee85a054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="52997-102">&lt;追加&gt;要素&lt;リスナー&gt;の&lt;トレース&gt;</span><span class="sxs-lookup"><span data-stu-id="52997-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="52997-103">リスナーを追加、**リスナー**コレクション。</span><span class="sxs-lookup"><span data-stu-id="52997-103">Adds a listener to the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="52997-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="52997-104">\<configuration></span></span>  
<span data-ttu-id="52997-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="52997-105">\<system.diagnostics></span></span>  
<span data-ttu-id="52997-106">\<トレース ></span><span class="sxs-lookup"><span data-stu-id="52997-106">\<trace></span></span>  
<span data-ttu-id="52997-107">\<リスナー ></span><span class="sxs-lookup"><span data-stu-id="52997-107">\<listeners></span></span>  
<span data-ttu-id="52997-108">\<add></span><span class="sxs-lookup"><span data-stu-id="52997-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52997-109">構文</span><span class="sxs-lookup"><span data-stu-id="52997-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52997-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="52997-110">Attributes and Elements</span></span>  
 <span data-ttu-id="52997-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="52997-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52997-112">属性</span><span class="sxs-lookup"><span data-stu-id="52997-112">Attributes</span></span>  
  
|<span data-ttu-id="52997-113">属性</span><span class="sxs-lookup"><span data-stu-id="52997-113">Attribute</span></span>|<span data-ttu-id="52997-114">説明</span><span class="sxs-lookup"><span data-stu-id="52997-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52997-115">**type**</span><span class="sxs-lookup"><span data-stu-id="52997-115">**type**</span></span>|<span data-ttu-id="52997-116">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="52997-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="52997-117">リスナーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="52997-117">Specifies the type of the listener.</span></span> <span data-ttu-id="52997-118">指定された要件を満たしている文字列を使用する必要があります[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="52997-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="52997-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="52997-119">**initializeData**</span></span>|<span data-ttu-id="52997-120">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="52997-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="52997-121">指定したクラスのコンス トラクターに渡された文字列。</span><span class="sxs-lookup"><span data-stu-id="52997-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="52997-122">**name**</span><span class="sxs-lookup"><span data-stu-id="52997-122">**name**</span></span>|<span data-ttu-id="52997-123">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="52997-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="52997-124">リスナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="52997-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52997-125">子要素</span><span class="sxs-lookup"><span data-stu-id="52997-125">Child Elements</span></span>  
  
|<span data-ttu-id="52997-126">要素</span><span class="sxs-lookup"><span data-stu-id="52997-126">Element</span></span>|<span data-ttu-id="52997-127">説明</span><span class="sxs-lookup"><span data-stu-id="52997-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52997-128">\<filter></span><span class="sxs-lookup"><span data-stu-id="52997-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="52997-129">リスナーにフィルターを追加、`Listeners`トレースのコレクション。</span><span class="sxs-lookup"><span data-stu-id="52997-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52997-130">親要素</span><span class="sxs-lookup"><span data-stu-id="52997-130">Parent Elements</span></span>  
  
|<span data-ttu-id="52997-131">要素</span><span class="sxs-lookup"><span data-stu-id="52997-131">Element</span></span>|<span data-ttu-id="52997-132">説明</span><span class="sxs-lookup"><span data-stu-id="52997-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="52997-133">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="52997-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="52997-134">リスナーを収集すると、ストアを指定し、メッセージをルーティングします。</span><span class="sxs-lookup"><span data-stu-id="52997-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="52997-135">リスナーでは、適切なターゲットのトレースを出力します。</span><span class="sxs-lookup"><span data-stu-id="52997-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="52997-136">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="52997-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="52997-137">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="52997-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52997-138">コメント</span><span class="sxs-lookup"><span data-stu-id="52997-138">Remarks</span></span>  
 <span data-ttu-id="52997-139"><xref:System.Diagnostics.Debug>と<xref:System.Diagnostics.Trace>クラスが同じ**リスナー**コレクション。</span><span class="sxs-lookup"><span data-stu-id="52997-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="52997-140">これらのクラスのいずれかで、コレクションに、リスナー オブジェクトを追加する場合、その他のクラスは、同じリスナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52997-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="52997-141">リスナー クラスから派生して、<xref:System.Diagnostics.TraceListener>です。</span><span class="sxs-lookup"><span data-stu-id="52997-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="52997-142">指定しない場合、`name`トレース リスナの属性、<xref:System.Diagnostics.TraceListener.Name%2A>のトレース リスナーの既定値に空の文字列 ("") です。</span><span class="sxs-lookup"><span data-stu-id="52997-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="52997-143">アプリケーションに 1 つだけリスナーがある場合は、それを名前を指定せず追加し、名前の空の文字列を指定することで削除します。</span><span class="sxs-lookup"><span data-stu-id="52997-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="52997-144">ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーを識別および内の個別のトレース リスナーを管理することができますに一意の名前を指定する必要があります、<xref:System.Diagnostics.Debug.Listeners%2A>と<xref:System.Diagnostics.Trace.Listeners%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="52997-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52997-145">その型の 1 つだけのトレース リスナーに結果の名前を指定し、名前に追加されている、同じ種類のと同じ 2 つ以上のトレース リスナーを追加する、`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="52997-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="52997-146">、に複数の同一のリスナーがプログラムで追加することができます、`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="52997-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="52997-147">値、 **initializeData**属性を作成するリスナーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="52997-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="52997-148">すべてのトレース リスナーを指定することが必要と**initializeData**です。</span><span class="sxs-lookup"><span data-stu-id="52997-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52997-149">使用すると、`initializeData`属性を受け取ることがあります、コンパイラの警告「'initializeData' 属性は宣言されていません」。</span><span class="sxs-lookup"><span data-stu-id="52997-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="52997-150">この警告の原因は、構成設定は、抽象基本クラスに対して検証されます<xref:System.Diagnostics.TraceListener>、これは認識されません、`initializeData`属性。</span><span class="sxs-lookup"><span data-stu-id="52997-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="52997-151">通常、パラメーターを受け取るコンス トラクターを持つトレース リスナーの実装のためには、この警告を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="52997-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="52997-152">次の表は、.NET Framework に含まれているトレース リスナーを示しの値を記述、 **initializeData**属性。</span><span class="sxs-lookup"><span data-stu-id="52997-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="52997-153">トレース リスナー クラス</span><span class="sxs-lookup"><span data-stu-id="52997-153">Trace listener class</span></span>|<span data-ttu-id="52997-154">initializeData 属性値</span><span class="sxs-lookup"><span data-stu-id="52997-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="52997-155">`useErrorStream`値を<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="52997-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="52997-156">設定、`initializeData`属性を"`true`"書き込むトレースとデバッグ出力を<xref:System.Console.Error%2A?displayProperty=nameWithType>です。"`false`"に書き込めません<xref:System.Console.Out%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="52997-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="52997-157">ファイルの名前、<xref:System.Diagnostics.DelimitedListTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="52997-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="52997-158">既存のイベント ログ ソースの名前の名前。</span><span class="sxs-lookup"><span data-stu-id="52997-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="52997-159">ファイルの名前を<xref:System.Diagnostics.EventSchemaTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="52997-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="52997-160">ファイルの名前を<xref:System.Diagnostics.TextWriterTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="52997-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="52997-161">ファイルの名前を<xref:System.Diagnostics.XmlWriterTraceListener>を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="52997-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="52997-162">例</span><span class="sxs-lookup"><span data-stu-id="52997-162">Example</span></span>  
 <span data-ttu-id="52997-163">次の例は、使用する方法を示しています。 **\<追加 >**リスナーを追加する要素`MyListener`と`MyEventListener`を、**リスナー**コレクション。</span><span class="sxs-lookup"><span data-stu-id="52997-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="52997-164">`MyListener`という名前のファイルを作成`MyListener.log`し、ファイルに出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="52997-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="52997-165">`MyEventListener`イベント ログにエントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="52997-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52997-166">参照</span><span class="sxs-lookup"><span data-stu-id="52997-166">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 [<span data-ttu-id="52997-167">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="52997-167">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="52997-168">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="52997-168">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
