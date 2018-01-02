---
title: "&lt;リスナー&gt;要素&lt;ソース&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dbabe9fbdc7ac4e611d96bf4bd696b716cf68156
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="eb7a2-102">&lt;リスナー&gt;要素&lt;ソース&gt;</span><span class="sxs-lookup"><span data-stu-id="eb7a2-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="eb7a2-103">追加または内のリスナーを削除、<xref:System.Diagnostics.TraceSource.Listeners%2A>のコレクション、<xref:System.Diagnostics.TraceSource>です。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="eb7a2-104">リスナーは、ログ、ウィンドウ、またはテキスト ファイルなどの適切なターゲットにトレース出力を出力します。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="eb7a2-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="eb7a2-105">\<configuration></span></span>  
<span data-ttu-id="eb7a2-106">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="eb7a2-106">\<system.diagnostics></span></span>  
<span data-ttu-id="eb7a2-107">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="eb7a2-107">\<sources></span></span>  
<span data-ttu-id="eb7a2-108">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="eb7a2-108">\<source></span></span>  
<span data-ttu-id="eb7a2-109">\<リスナー > 要素</span><span class="sxs-lookup"><span data-stu-id="eb7a2-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb7a2-110">構文</span><span class="sxs-lookup"><span data-stu-id="eb7a2-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb7a2-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="eb7a2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="eb7a2-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb7a2-113">属性</span><span class="sxs-lookup"><span data-stu-id="eb7a2-113">Attributes</span></span>  
 <span data-ttu-id="eb7a2-114">なし。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eb7a2-115">子要素</span><span class="sxs-lookup"><span data-stu-id="eb7a2-115">Child Elements</span></span>  
  
|<span data-ttu-id="eb7a2-116">要素</span><span class="sxs-lookup"><span data-stu-id="eb7a2-116">Element</span></span>|<span data-ttu-id="eb7a2-117">説明</span><span class="sxs-lookup"><span data-stu-id="eb7a2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb7a2-118">\<add></span><span class="sxs-lookup"><span data-stu-id="eb7a2-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="eb7a2-119">`Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="eb7a2-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="eb7a2-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="eb7a2-121">リスナーを削除、`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="eb7a2-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="eb7a2-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="eb7a2-123">トレース ソースの `Listeners` コレクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb7a2-124">親要素</span><span class="sxs-lookup"><span data-stu-id="eb7a2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="eb7a2-125">要素</span><span class="sxs-lookup"><span data-stu-id="eb7a2-125">Element</span></span>|<span data-ttu-id="eb7a2-126">説明</span><span class="sxs-lookup"><span data-stu-id="eb7a2-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eb7a2-127">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="eb7a2-128">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="eb7a2-129">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="eb7a2-130">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb7a2-131">コメント</span><span class="sxs-lookup"><span data-stu-id="eb7a2-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="eb7a2-132">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="eb7a2-132">Configuration File</span></span>  
 <span data-ttu-id="eb7a2-133">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb7a2-134">例</span><span class="sxs-lookup"><span data-stu-id="eb7a2-134">Example</span></span>  
 <span data-ttu-id="eb7a2-135">次の例を使用する方法を示しています、`<listeners>`コンソール トレース リスナーを追加する要素、`mySource`ソースおよび既定のトレース リスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="eb7a2-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb7a2-136">参照</span><span class="sxs-lookup"><span data-stu-id="eb7a2-136">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="eb7a2-137">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="eb7a2-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="eb7a2-138">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="eb7a2-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
