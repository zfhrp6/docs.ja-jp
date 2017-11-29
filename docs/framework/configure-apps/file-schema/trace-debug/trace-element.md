---
title: "&lt;トレース&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 157adb6c7317aa047976cdb9e30711d20c9e543b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttracegt-element"></a><span data-ttu-id="967dd-102">&lt;トレース&gt;要素</span><span class="sxs-lookup"><span data-stu-id="967dd-102">&lt;trace&gt; Element</span></span>
<span data-ttu-id="967dd-103">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="967dd-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
 <span data-ttu-id="967dd-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="967dd-104">\<configuration></span></span>  
<span data-ttu-id="967dd-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="967dd-105">\<system.diagnostics></span></span>  
<span data-ttu-id="967dd-106">\<トレース ></span><span class="sxs-lookup"><span data-stu-id="967dd-106">\<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="967dd-107">構文</span><span class="sxs-lookup"><span data-stu-id="967dd-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="967dd-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="967dd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="967dd-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="967dd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="967dd-110">属性</span><span class="sxs-lookup"><span data-stu-id="967dd-110">Attributes</span></span>  
  
|<span data-ttu-id="967dd-111">属性</span><span class="sxs-lookup"><span data-stu-id="967dd-111">Attribute</span></span>|<span data-ttu-id="967dd-112">説明</span><span class="sxs-lookup"><span data-stu-id="967dd-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="967dd-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="967dd-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="967dd-114">トレース リスナーが、すべての書き込み操作の後に、出力バッファーを自動的にフラッシュするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="967dd-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="967dd-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="967dd-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="967dd-116">インデントを設定する空白の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="967dd-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="967dd-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="967dd-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="967dd-118">グローバル ロックを使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="967dd-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="967dd-119">autoflush 属性</span><span class="sxs-lookup"><span data-stu-id="967dd-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="967dd-120">値</span><span class="sxs-lookup"><span data-stu-id="967dd-120">Value</span></span>|<span data-ttu-id="967dd-121">説明</span><span class="sxs-lookup"><span data-stu-id="967dd-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="967dd-122">出力バッファーを自動的にフラッシュしません。</span><span class="sxs-lookup"><span data-stu-id="967dd-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="967dd-123">既定値です。</span><span class="sxs-lookup"><span data-stu-id="967dd-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="967dd-124">自動的に出力バッファーをフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="967dd-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="967dd-125">属性を用意されました</span><span class="sxs-lookup"><span data-stu-id="967dd-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="967dd-126">値</span><span class="sxs-lookup"><span data-stu-id="967dd-126">Value</span></span>|<span data-ttu-id="967dd-127">説明</span><span class="sxs-lookup"><span data-stu-id="967dd-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="967dd-128">リスナーがスレッド セーフである場合、グローバル ロックを使用しません。それ以外の場合、グローバル ロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="967dd-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="967dd-129">リスナーは、スレッド セーフであるかどうかに関係なくグローバル ロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="967dd-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="967dd-130">既定値です。</span><span class="sxs-lookup"><span data-stu-id="967dd-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="967dd-131">子要素</span><span class="sxs-lookup"><span data-stu-id="967dd-131">Child Elements</span></span>  
  
|<span data-ttu-id="967dd-132">要素</span><span class="sxs-lookup"><span data-stu-id="967dd-132">Element</span></span>|<span data-ttu-id="967dd-133">説明</span><span class="sxs-lookup"><span data-stu-id="967dd-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="967dd-134">\<listeners></span><span class="sxs-lookup"><span data-stu-id="967dd-134">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="967dd-135">リスナーを収集すると、ストアを指定し、メッセージをルーティングします。</span><span class="sxs-lookup"><span data-stu-id="967dd-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="967dd-136">親要素</span><span class="sxs-lookup"><span data-stu-id="967dd-136">Parent Elements</span></span>  
  
|<span data-ttu-id="967dd-137">要素</span><span class="sxs-lookup"><span data-stu-id="967dd-137">Element</span></span>|<span data-ttu-id="967dd-138">説明</span><span class="sxs-lookup"><span data-stu-id="967dd-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="967dd-139">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="967dd-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="967dd-140">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="967dd-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="967dd-141">例</span><span class="sxs-lookup"><span data-stu-id="967dd-141">Example</span></span>  
 <span data-ttu-id="967dd-142">次の例を使用する方法を示しています、`<trace>`リスナーを追加する要素`MyListener`を`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="967dd-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="967dd-143">`MyListener`という名前のファイルを作成`MyListener.log`し、ファイルに出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="967dd-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="967dd-144">`useGlobalLock`属性に設定されている`false`、それが原因で、グローバル ロック トレース リスナーがスレッド セーフである場合に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="967dd-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="967dd-145">`autoflush`属性に設定されている`true`、それが原因かどうかに関係なく、ファイルに書き込むトレース リスナー、<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="967dd-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="967dd-146">`indentsize`属性が 0 (ゼロ)。 これにより、0 個のスペースのインデントを設定するリスナーに設定されているときに、<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="967dd-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="967dd-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="967dd-147">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="967dd-148">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="967dd-148">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
