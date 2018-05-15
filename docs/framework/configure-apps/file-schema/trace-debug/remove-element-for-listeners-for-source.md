---
title: '&lt;削除&gt;要素&lt;リスナー&gt;の&lt;ソース&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cc6772e7a9b98f09df21fd1acf24f578b66ae51e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="3e704-102">&lt;削除&gt;要素&lt;リスナー&gt;の&lt;ソース&gt;</span><span class="sxs-lookup"><span data-stu-id="3e704-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="3e704-103">トレース ソースの `Listeners` コレクションからリスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="3e704-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="3e704-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3e704-104">\<configuration></span></span>  
<span data-ttu-id="3e704-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="3e704-105">\<system.diagnostics></span></span>  
<span data-ttu-id="3e704-106">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="3e704-106">\<sources></span></span>  
<span data-ttu-id="3e704-107">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="3e704-107">\<source></span></span>  
<span data-ttu-id="3e704-108">\<リスナー ></span><span class="sxs-lookup"><span data-stu-id="3e704-108">\<listeners></span></span>  
<span data-ttu-id="3e704-109">\<remove></span><span class="sxs-lookup"><span data-stu-id="3e704-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e704-110">構文</span><span class="sxs-lookup"><span data-stu-id="3e704-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e704-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3e704-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3e704-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e704-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e704-113">属性</span><span class="sxs-lookup"><span data-stu-id="3e704-113">Attributes</span></span>  
  
|<span data-ttu-id="3e704-114">属性</span><span class="sxs-lookup"><span data-stu-id="3e704-114">Attribute</span></span>|<span data-ttu-id="3e704-115">説明</span><span class="sxs-lookup"><span data-stu-id="3e704-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="3e704-116">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3e704-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="3e704-117">削除するリスナーの名前、`Listeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="3e704-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e704-118">子要素</span><span class="sxs-lookup"><span data-stu-id="3e704-118">Child Elements</span></span>  
 <span data-ttu-id="3e704-119">なし。</span><span class="sxs-lookup"><span data-stu-id="3e704-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e704-120">親要素</span><span class="sxs-lookup"><span data-stu-id="3e704-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3e704-121">要素</span><span class="sxs-lookup"><span data-stu-id="3e704-121">Element</span></span>|<span data-ttu-id="3e704-122">説明</span><span class="sxs-lookup"><span data-stu-id="3e704-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3e704-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="3e704-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3e704-124">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e704-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="3e704-125">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="3e704-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="3e704-126">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e704-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="3e704-127">収集、保管、およびメッセージをルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e704-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e704-128">コメント</span><span class="sxs-lookup"><span data-stu-id="3e704-128">Remarks</span></span>  
 <span data-ttu-id="3e704-129">`<remove>`要素から指定されたリスナーの削除、`Listeners`トレース ソースのコレクション。</span><span class="sxs-lookup"><span data-stu-id="3e704-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="3e704-130">要素を削除することができます、`Listeners`呼び出すことによってプログラムでトレース ソースのコレクション、<xref:System.Diagnostics.TraceListenerCollection.Remove%2A>メソッドを<xref:System.Diagnostics.TraceSource.Listeners%2A>のプロパティ、<xref:System.Diagnostics.TraceSource>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3e704-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="3e704-131">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e704-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e704-132">例</span><span class="sxs-lookup"><span data-stu-id="3e704-132">Example</span></span>  
 <span data-ttu-id="3e704-133">次の例を使用する方法を示しています、`<remove>`要素を使用する前に、`<add>`リスナーを追加する要素`console`を`Listeners`トレース ソースのコレクション`TraceSourceApp`です。</span><span class="sxs-lookup"><span data-stu-id="3e704-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="3e704-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e704-134">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="3e704-135">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="3e704-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="3e704-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="3e704-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)  
 [<span data-ttu-id="3e704-137">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="3e704-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
