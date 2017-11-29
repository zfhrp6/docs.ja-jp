---
title: "&lt;system.diagnostics&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d336a0f733451cb28d8fe57af20585515b71ca4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemdiagnosticsgt-element"></a><span data-ttu-id="a4e09-102">&lt;system.diagnostics&gt;要素</span><span class="sxs-lookup"><span data-stu-id="a4e09-102">&lt;system.diagnostics&gt; Element</span></span>
<span data-ttu-id="a4e09-103">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4e09-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="a4e09-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a4e09-104">\<configuration></span></span>  
<span data-ttu-id="a4e09-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="a4e09-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e09-106">構文</span><span class="sxs-lookup"><span data-stu-id="a4e09-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4e09-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a4e09-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a4e09-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a4e09-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4e09-109">属性</span><span class="sxs-lookup"><span data-stu-id="a4e09-109">Attributes</span></span>  
 <span data-ttu-id="a4e09-110">なし。</span><span class="sxs-lookup"><span data-stu-id="a4e09-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a4e09-111">子要素</span><span class="sxs-lookup"><span data-stu-id="a4e09-111">Child Elements</span></span>  
  
|<span data-ttu-id="a4e09-112">要素</span><span class="sxs-lookup"><span data-stu-id="a4e09-112">Element</span></span>|<span data-ttu-id="a4e09-113">説明</span><span class="sxs-lookup"><span data-stu-id="a4e09-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4e09-114">\<assert></span><span class="sxs-lookup"><span data-stu-id="a4e09-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="a4e09-115"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。</span><span class="sxs-lookup"><span data-stu-id="a4e09-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="a4e09-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="a4e09-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="a4e09-117">パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4e09-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="a4e09-118">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="a4e09-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="a4e09-119">任意の source 要素または trace 要素が参照できるリスナーを含みます。</span><span class="sxs-lookup"><span data-stu-id="a4e09-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="a4e09-120">共有リスナーとして識別されたリスナーは、名前でソースまたはカスタム トレースに追加できます。</span><span class="sxs-lookup"><span data-stu-id="a4e09-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="a4e09-121">\<sources></span><span class="sxs-lookup"><span data-stu-id="a4e09-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="a4e09-122">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4e09-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="a4e09-123">\<switches></span><span class="sxs-lookup"><span data-stu-id="a4e09-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="a4e09-124">トレース スイッチとトレース スイッチを設定するレベルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a4e09-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="a4e09-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="a4e09-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="a4e09-126">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="a4e09-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4e09-127">親要素</span><span class="sxs-lookup"><span data-stu-id="a4e09-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a4e09-128">要素</span><span class="sxs-lookup"><span data-stu-id="a4e09-128">Element</span></span>|<span data-ttu-id="a4e09-129">説明</span><span class="sxs-lookup"><span data-stu-id="a4e09-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a4e09-130">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a4e09-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4e09-131">例</span><span class="sxs-lookup"><span data-stu-id="a4e09-131">Example</span></span>  
 <span data-ttu-id="a4e09-132">次の例は、トレース スイッチと内部のトレース リスナーを埋め込む方法を示します、  **\<system.diagnostics >**要素。</span><span class="sxs-lookup"><span data-stu-id="a4e09-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="a4e09-133">`General`にトレース スイッチが設定されている、<xref:System.Diagnostics.TraceLevel>レベル。</span><span class="sxs-lookup"><span data-stu-id="a4e09-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="a4e09-134">トレース リスナー`myListener`という名前のファイルを作成`MyListener.log`し、ファイルに出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a4e09-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4e09-135">.NET Framework バージョン 2.0 では、スイッチの値を指定するためにテキストを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4e09-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="a4e09-136">たとえば、指定することができます`true`の<xref:System.Diagnostics.BooleanSwitch>など列挙値を表すテキストを使用するか`Error`の<xref:System.Diagnostics.TraceSwitch>です。</span><span class="sxs-lookup"><span data-stu-id="a4e09-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="a4e09-137">`<add name="myTraceSwitch" value="Error" />` という行は、`<add name="myTraceSwitch" value="1" />` と同じです。</span><span class="sxs-lookup"><span data-stu-id="a4e09-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4e09-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4e09-138">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="a4e09-139">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="a4e09-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
