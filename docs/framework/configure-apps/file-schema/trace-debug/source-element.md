---
title: '&lt;ソース&gt;要素'
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b7c2a71b129a0ad7d1c2a72b18b8a69a111f9495
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="153f3-102">&lt;ソース&gt;要素</span><span class="sxs-lookup"><span data-stu-id="153f3-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="153f3-103">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="153f3-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="153f3-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="153f3-104">\<configuration></span></span>  
<span data-ttu-id="153f3-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="153f3-105">\<system.diagnostics></span></span>  
<span data-ttu-id="153f3-106">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="153f3-106">\<sources></span></span>  
<span data-ttu-id="153f3-107">\<ソース ></span><span class="sxs-lookup"><span data-stu-id="153f3-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="153f3-108">構文</span><span class="sxs-lookup"><span data-stu-id="153f3-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="153f3-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="153f3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="153f3-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="153f3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="153f3-111">属性</span><span class="sxs-lookup"><span data-stu-id="153f3-111">Attributes</span></span>  
  
|<span data-ttu-id="153f3-112">属性</span><span class="sxs-lookup"><span data-stu-id="153f3-112">Attribute</span></span>|<span data-ttu-id="153f3-113">説明</span><span class="sxs-lookup"><span data-stu-id="153f3-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="153f3-114">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="153f3-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="153f3-115">トレース ソースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="153f3-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="153f3-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="153f3-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="153f3-117">アプリケーションでトレース スイッチのインスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="153f3-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="153f3-118">スイッチがで指定されていない場合、`<switches>`要素値が、スイッチのレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="153f3-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="153f3-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="153f3-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="153f3-120">トレース スイッチの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="153f3-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="153f3-121">存在する場合、型は有効なクラス名である必要がありますされ、空の文字列にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="153f3-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="153f3-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="153f3-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="153f3-123">によって識別されるトレース ソースに固有の属性の値を指定、<xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A>そのトレース ソースのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="153f3-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="153f3-124">子要素</span><span class="sxs-lookup"><span data-stu-id="153f3-124">Child Elements</span></span>  
  
|<span data-ttu-id="153f3-125">要素</span><span class="sxs-lookup"><span data-stu-id="153f3-125">Element</span></span>|<span data-ttu-id="153f3-126">説明</span><span class="sxs-lookup"><span data-stu-id="153f3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="153f3-127">\<listeners></span><span class="sxs-lookup"><span data-stu-id="153f3-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="153f3-128">収集、保管、およびメッセージをルーティングするリスナーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="153f3-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="153f3-129">親要素</span><span class="sxs-lookup"><span data-stu-id="153f3-129">Parent Elements</span></span>  
  
|<span data-ttu-id="153f3-130">要素</span><span class="sxs-lookup"><span data-stu-id="153f3-130">Element</span></span>|<span data-ttu-id="153f3-131">説明</span><span class="sxs-lookup"><span data-stu-id="153f3-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="153f3-132">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="153f3-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="153f3-133">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="153f3-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="153f3-134">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="153f3-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="153f3-135">コメント</span><span class="sxs-lookup"><span data-stu-id="153f3-135">Remarks</span></span>  
 <span data-ttu-id="153f3-136">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="153f3-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="153f3-137">例</span><span class="sxs-lookup"><span data-stu-id="153f3-137">Example</span></span>  
 <span data-ttu-id="153f3-138">次の例を使用する方法を示しています、`<source>`トレース ソースを追加する要素`mySource`という名前のソース スイッチのレベルを設定して`sourceSwitch`です。</span><span class="sxs-lookup"><span data-stu-id="153f3-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="153f3-139">トレース情報をコンソールに出力をコンソール トレース リスナーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="153f3-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="153f3-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="153f3-140">See Also</span></span>  
 [<span data-ttu-id="153f3-141">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="153f3-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="153f3-142">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="153f3-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
