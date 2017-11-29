---
title: "&lt;sharedListeners&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7ab96ad43248517dca99bff176be7edfab8d3ced
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsharedlistenersgt-element"></a><span data-ttu-id="b22eb-102">&lt;sharedListeners&gt;要素</span><span class="sxs-lookup"><span data-stu-id="b22eb-102">&lt;sharedListeners&gt; Element</span></span>
<span data-ttu-id="b22eb-103">任意の source 要素または trace 要素が参照できるリスナーを含みます。</span><span class="sxs-lookup"><span data-stu-id="b22eb-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="b22eb-104">これらのリスナーは、既定では、トレースを受け取りません、実行時にこれらのリスナーを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="b22eb-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="b22eb-105">共有リスナーとして識別されたリスナーは、名前でソースまたはカスタム トレースに追加できます。</span><span class="sxs-lookup"><span data-stu-id="b22eb-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
 <span data-ttu-id="b22eb-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b22eb-106">\<configuration></span></span>  
<span data-ttu-id="b22eb-107">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="b22eb-107">\<system.diagnostics></span></span>  
<span data-ttu-id="b22eb-108">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="b22eb-108">\<sharedListeners></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b22eb-109">構文</span><span class="sxs-lookup"><span data-stu-id="b22eb-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b22eb-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b22eb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b22eb-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b22eb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b22eb-112">属性</span><span class="sxs-lookup"><span data-stu-id="b22eb-112">Attributes</span></span>  
 <span data-ttu-id="b22eb-113">なし。</span><span class="sxs-lookup"><span data-stu-id="b22eb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b22eb-114">子要素</span><span class="sxs-lookup"><span data-stu-id="b22eb-114">Child Elements</span></span>  
  
|<span data-ttu-id="b22eb-115">要素</span><span class="sxs-lookup"><span data-stu-id="b22eb-115">Element</span></span>|<span data-ttu-id="b22eb-116">説明</span><span class="sxs-lookup"><span data-stu-id="b22eb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b22eb-117">\<add></span><span class="sxs-lookup"><span data-stu-id="b22eb-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="b22eb-118">`sharedListeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="b22eb-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b22eb-119">親要素</span><span class="sxs-lookup"><span data-stu-id="b22eb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b22eb-120">要素</span><span class="sxs-lookup"><span data-stu-id="b22eb-120">Element</span></span>|<span data-ttu-id="b22eb-121">説明</span><span class="sxs-lookup"><span data-stu-id="b22eb-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="b22eb-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="b22eb-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b22eb-123">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="b22eb-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b22eb-124">コメント</span><span class="sxs-lookup"><span data-stu-id="b22eb-124">Remarks</span></span>  
 <span data-ttu-id="b22eb-125">リスナーを共有リスナー コレクションに追加することはありませんが、アクティブなリスナー。</span><span class="sxs-lookup"><span data-stu-id="b22eb-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="b22eb-126">これは、必要がありますによって引き続き追加できますをトレース ソースまたはトレースに追加すること、 `Listeners` trace 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="b22eb-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="b22eb-127">.NET Framework のリスナー クラスから派生して、<xref:System.Diagnostics.TraceListener>クラスです。</span><span class="sxs-lookup"><span data-stu-id="b22eb-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="b22eb-128">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b22eb-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b22eb-129">例</span><span class="sxs-lookup"><span data-stu-id="b22eb-129">Example</span></span>  
 <span data-ttu-id="b22eb-130">次の例を使用する方法を示しています、`<sharedListeners>`リスナーを追加する要素`console`を`Listeners`両方のコレクション、<xref:System.Diagnostics.TraceSource>と<xref:System.Diagnostics.Trace>クラスです。</span><span class="sxs-lookup"><span data-stu-id="b22eb-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="b22eb-131">コンソールのトレース リスナーは、いずれかを呼び出すことで、コンソールにトレース情報を書き込みます<xref:System.Diagnostics.TraceSource>または<xref:System.Diagnostics.Trace>です。</span><span class="sxs-lookup"><span data-stu-id="b22eb-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a><span data-ttu-id="b22eb-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b22eb-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="b22eb-133">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="b22eb-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="b22eb-134">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="b22eb-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
