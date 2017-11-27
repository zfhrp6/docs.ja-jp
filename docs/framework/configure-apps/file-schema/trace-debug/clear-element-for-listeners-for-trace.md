---
title: "&lt;オフ&gt;要素&lt;リスナー&gt;の&lt;トレース&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 34e6e7c505dab135452664fdb815ee3e905a2ad0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="c4e77-102">&lt;オフ&gt;要素&lt;リスナー&gt;の&lt;トレース&gt;</span><span class="sxs-lookup"><span data-stu-id="c4e77-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="c4e77-103">トレースの `Listeners` コレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="c4e77-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="c4e77-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c4e77-104">\<configuration></span></span>  
<span data-ttu-id="c4e77-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="c4e77-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c4e77-106">\<トレース ></span><span class="sxs-lookup"><span data-stu-id="c4e77-106">\<trace></span></span>  
<span data-ttu-id="c4e77-107">\<リスナー ></span><span class="sxs-lookup"><span data-stu-id="c4e77-107">\<listeners></span></span>  
<span data-ttu-id="c4e77-108">\<オフ ></span><span class="sxs-lookup"><span data-stu-id="c4e77-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e77-109">構文</span><span class="sxs-lookup"><span data-stu-id="c4e77-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4e77-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c4e77-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c4e77-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c4e77-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4e77-112">属性</span><span class="sxs-lookup"><span data-stu-id="c4e77-112">Attributes</span></span>  
 <span data-ttu-id="c4e77-113">なし。</span><span class="sxs-lookup"><span data-stu-id="c4e77-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4e77-114">子要素</span><span class="sxs-lookup"><span data-stu-id="c4e77-114">Child Elements</span></span>  
 <span data-ttu-id="c4e77-115">なし。</span><span class="sxs-lookup"><span data-stu-id="c4e77-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4e77-116">親要素</span><span class="sxs-lookup"><span data-stu-id="c4e77-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c4e77-117">要素</span><span class="sxs-lookup"><span data-stu-id="c4e77-117">Element</span></span>|<span data-ttu-id="c4e77-118">説明</span><span class="sxs-lookup"><span data-stu-id="c4e77-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c4e77-119">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="c4e77-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c4e77-120">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4e77-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="c4e77-121">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="c4e77-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="c4e77-122">収集、保管、およびメッセージをルーティングするリスナーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c4e77-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="c4e77-123">リスナーでは、適切なターゲットのトレースを出力します。</span><span class="sxs-lookup"><span data-stu-id="c4e77-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4e77-124">コメント</span><span class="sxs-lookup"><span data-stu-id="c4e77-124">Remarks</span></span>  
 <span data-ttu-id="c4e77-125">`<clear>`要素からすべてのリスナーを削除して、`Listeners`トレースのコレクション。</span><span class="sxs-lookup"><span data-stu-id="c4e77-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="c4e77-126">使用することができます、`<clear>`要素を使用する前に、`<add>`要素をコレクション内の他のアクティブなリスナーが存在しないことを特定します。</span><span class="sxs-lookup"><span data-stu-id="c4e77-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="c4e77-127">オフにすることができます、`Listeners`呼び出すことによってプログラムでコレクション、<xref:System.Diagnostics.TraceListenerCollection.Clear%2A>メソッドを<xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>プロパティ (`System.Diagnostics.Trace.Listeners.Clear()`)。</span><span class="sxs-lookup"><span data-stu-id="c4e77-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="c4e77-128">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="c4e77-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4e77-129">`<clear>`要素は、削除、<xref:System.Diagnostics.DefaultTraceListener>から、`Listeners`の動作を変更する、コレクション、 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>、 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>、 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>、および<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c4e77-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="c4e77-130">呼び出す、`Assert`または`Fail`メソッドは、通常、メッセージ ボックスの表示になります。</span><span class="sxs-lookup"><span data-stu-id="c4e77-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="c4e77-131">ただし、メッセージ ボックスが表示されない場合、<xref:System.Diagnostics.DefaultTraceListener>に含まれていない、`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="c4e77-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4e77-132">例</span><span class="sxs-lookup"><span data-stu-id="c4e77-132">Example</span></span>  
 <span data-ttu-id="c4e77-133">次の例を使用する方法を示しています、`<clear>`要素を使用する前に、`<add>`リスナーを追加する要素`console`を`Listeners`トレースのコレクション。</span><span class="sxs-lookup"><span data-stu-id="c4e77-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="c4e77-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4e77-134">See Also</span></span>  
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="c4e77-135">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="c4e77-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="c4e77-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="c4e77-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [<span data-ttu-id="c4e77-137">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="c4e77-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
