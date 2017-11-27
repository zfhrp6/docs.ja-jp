---
title: "&lt;オフ&gt;要素&lt;リスナー&gt;の&lt;ソース&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d5e8518f2ca8a04d91f5bfdd9f6389c741d0278e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="8cc8d-102">&lt;オフ&gt;要素&lt;リスナー&gt;の&lt;ソース&gt;</span><span class="sxs-lookup"><span data-stu-id="8cc8d-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="8cc8d-103">トレース ソースの `Listeners` コレクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="8cc8d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8cc8d-104">\<configuration></span></span>  
<span data-ttu-id="8cc8d-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="8cc8d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8cc8d-106">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="8cc8d-106">\<sources></span></span>  
<span data-ttu-id="8cc8d-107">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="8cc8d-107">\<source></span></span>  
<span data-ttu-id="8cc8d-108">\<リスナー ></span><span class="sxs-lookup"><span data-stu-id="8cc8d-108">\<listeners></span></span>  
<span data-ttu-id="8cc8d-109">\<オフ ></span><span class="sxs-lookup"><span data-stu-id="8cc8d-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc8d-110">構文</span><span class="sxs-lookup"><span data-stu-id="8cc8d-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cc8d-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8cc8d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8cc8d-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cc8d-113">属性</span><span class="sxs-lookup"><span data-stu-id="8cc8d-113">Attributes</span></span>  
 <span data-ttu-id="8cc8d-114">なし。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8cc8d-115">子要素</span><span class="sxs-lookup"><span data-stu-id="8cc8d-115">Child Elements</span></span>  
 <span data-ttu-id="8cc8d-116">なし。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cc8d-117">親要素</span><span class="sxs-lookup"><span data-stu-id="8cc8d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8cc8d-118">要素</span><span class="sxs-lookup"><span data-stu-id="8cc8d-118">Element</span></span>|<span data-ttu-id="8cc8d-119">説明</span><span class="sxs-lookup"><span data-stu-id="8cc8d-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8cc8d-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8cc8d-121">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="8cc8d-122">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="8cc8d-123">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8cc8d-124">収集、保管、およびメッセージをルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cc8d-125">コメント</span><span class="sxs-lookup"><span data-stu-id="8cc8d-125">Remarks</span></span>  
 <span data-ttu-id="8cc8d-126">`<clear>`要素からすべてのリスナーを削除して、`Listeners`トレース ソースのコレクションを含む、<xref:System.Diagnostics.DefaultTraceListener>です。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="8cc8d-127">使用することができます、`<clear>`要素を使用する前に、`<add>`要素をコレクション内の他のアクティブなリスナーが存在しないことを特定します。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="8cc8d-128">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="8cc8d-128">Configuration File</span></span>  
 <span data-ttu-id="8cc8d-129">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cc8d-130">例</span><span class="sxs-lookup"><span data-stu-id="8cc8d-130">Example</span></span>  
 <span data-ttu-id="8cc8d-131">次の例を使用する方法を示しています、`<clear>`要素を使用する前に、`<add>`リスナーを追加する要素`console`と`textListener`を`Listeners`トレース ソースのコレクション`TraceSourceApp`です。</span><span class="sxs-lookup"><span data-stu-id="8cc8d-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="8cc8d-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cc8d-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="8cc8d-133">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="8cc8d-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="8cc8d-134">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="8cc8d-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
