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
ms.workload: dotnet
ms.openlocfilehash: 3cc809a6e896119c5d31c700f3e2ced171da9f7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="dd271-102">&lt;オフ&gt;要素&lt;リスナー&gt;の&lt;ソース&gt;</span><span class="sxs-lookup"><span data-stu-id="dd271-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="dd271-103">トレース ソースの `Listeners` コレクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="dd271-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="dd271-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dd271-104">\<configuration></span></span>  
<span data-ttu-id="dd271-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="dd271-105">\<system.diagnostics></span></span>  
<span data-ttu-id="dd271-106">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="dd271-106">\<sources></span></span>  
<span data-ttu-id="dd271-107">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="dd271-107">\<source></span></span>  
<span data-ttu-id="dd271-108">\<リスナー ></span><span class="sxs-lookup"><span data-stu-id="dd271-108">\<listeners></span></span>  
<span data-ttu-id="dd271-109">\<オフ ></span><span class="sxs-lookup"><span data-stu-id="dd271-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd271-110">構文</span><span class="sxs-lookup"><span data-stu-id="dd271-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd271-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dd271-111">Attributes and Elements</span></span>  
 <span data-ttu-id="dd271-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd271-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd271-113">属性</span><span class="sxs-lookup"><span data-stu-id="dd271-113">Attributes</span></span>  
 <span data-ttu-id="dd271-114">なし。</span><span class="sxs-lookup"><span data-stu-id="dd271-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd271-115">子要素</span><span class="sxs-lookup"><span data-stu-id="dd271-115">Child Elements</span></span>  
 <span data-ttu-id="dd271-116">なし。</span><span class="sxs-lookup"><span data-stu-id="dd271-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd271-117">親要素</span><span class="sxs-lookup"><span data-stu-id="dd271-117">Parent Elements</span></span>  
  
|<span data-ttu-id="dd271-118">要素</span><span class="sxs-lookup"><span data-stu-id="dd271-118">Element</span></span>|<span data-ttu-id="dd271-119">説明</span><span class="sxs-lookup"><span data-stu-id="dd271-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dd271-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="dd271-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="dd271-121">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd271-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="dd271-122">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="dd271-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="dd271-123">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd271-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="dd271-124">収集、保管、およびメッセージをルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd271-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd271-125">コメント</span><span class="sxs-lookup"><span data-stu-id="dd271-125">Remarks</span></span>  
 <span data-ttu-id="dd271-126">`<clear>`要素からすべてのリスナーを削除して、`Listeners`トレース ソースのコレクションを含む、<xref:System.Diagnostics.DefaultTraceListener>です。</span><span class="sxs-lookup"><span data-stu-id="dd271-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="dd271-127">使用することができます、`<clear>`要素を使用する前に、`<add>`要素をコレクション内の他のアクティブなリスナーが存在しないことを特定します。</span><span class="sxs-lookup"><span data-stu-id="dd271-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="dd271-128">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="dd271-128">Configuration File</span></span>  
 <span data-ttu-id="dd271-129">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd271-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd271-130">例</span><span class="sxs-lookup"><span data-stu-id="dd271-130">Example</span></span>  
 <span data-ttu-id="dd271-131">次の例を使用する方法を示しています、`<clear>`要素を使用する前に、`<add>`リスナーを追加する要素`console`と`textListener`を`Listeners`トレース ソースのコレクション`TraceSourceApp`です。</span><span class="sxs-lookup"><span data-stu-id="dd271-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd271-132">参照</span><span class="sxs-lookup"><span data-stu-id="dd271-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="dd271-133">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="dd271-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="dd271-134">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="dd271-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
