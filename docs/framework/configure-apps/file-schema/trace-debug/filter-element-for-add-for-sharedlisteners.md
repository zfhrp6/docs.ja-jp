---
title: "&lt;フィルター&gt;要素&lt;追加&gt;の&lt;sharedListeners&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ce4134d9059d1f1d5bd2e435a3cc87d3fbccd422
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltsharedlistenersgt"></a><span data-ttu-id="acc7b-102">&lt;フィルター&gt;要素&lt;追加&gt;の&lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="acc7b-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="acc7b-103">`sharedListeners` コレクションのリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="acc7b-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="acc7b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="acc7b-104">\<configuration></span></span>  
<span data-ttu-id="acc7b-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="acc7b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="acc7b-106">\<sharedListeners > 要素</span><span class="sxs-lookup"><span data-stu-id="acc7b-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="acc7b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="acc7b-107">\<add></span></span>  
<span data-ttu-id="acc7b-108">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="acc7b-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acc7b-109">構文</span><span class="sxs-lookup"><span data-stu-id="acc7b-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acc7b-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="acc7b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="acc7b-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="acc7b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acc7b-112">属性</span><span class="sxs-lookup"><span data-stu-id="acc7b-112">Attributes</span></span>  
  
|<span data-ttu-id="acc7b-113">属性</span><span class="sxs-lookup"><span data-stu-id="acc7b-113">Attribute</span></span>|<span data-ttu-id="acc7b-114">説明</span><span class="sxs-lookup"><span data-stu-id="acc7b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="acc7b-115">**type**</span><span class="sxs-lookup"><span data-stu-id="acc7b-115">**type**</span></span>|<span data-ttu-id="acc7b-116">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="acc7b-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="acc7b-117">フィルターの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="acc7b-117">Specifies the type of the filter.</span></span> <span data-ttu-id="acc7b-118">型の完全名のみを使用することができます (の形式で、<xref:System.Type.FullName%2A?displayProperty=nameWithType>プロパティ)、アセンブリ情報を含め、完全修飾型名を使用することもできます (の形式で、<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>プロパティ)。</span><span class="sxs-lookup"><span data-stu-id="acc7b-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="acc7b-119">完全修飾型名を作成する方法については、次を参照してください。[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="acc7b-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="acc7b-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="acc7b-120">**initializeData**</span></span>|<span data-ttu-id="acc7b-121">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="acc7b-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="acc7b-122">指定したクラスのコンス トラクターに渡された文字列。</span><span class="sxs-lookup"><span data-stu-id="acc7b-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="acc7b-123">子要素</span><span class="sxs-lookup"><span data-stu-id="acc7b-123">Child Elements</span></span>  
 <span data-ttu-id="acc7b-124">なし。</span><span class="sxs-lookup"><span data-stu-id="acc7b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="acc7b-125">親要素</span><span class="sxs-lookup"><span data-stu-id="acc7b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="acc7b-126">要素</span><span class="sxs-lookup"><span data-stu-id="acc7b-126">Element</span></span>|<span data-ttu-id="acc7b-127">説明</span><span class="sxs-lookup"><span data-stu-id="acc7b-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="acc7b-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="acc7b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="acc7b-129">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="acc7b-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="acc7b-130">任意のソースまたはトレース要素を参照できるリスナーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="acc7b-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="acc7b-131">リスナーを追加、 **sharedListeners**コレクション。</span><span class="sxs-lookup"><span data-stu-id="acc7b-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acc7b-132">コメント</span><span class="sxs-lookup"><span data-stu-id="acc7b-132">Remarks</span></span>  
 <span data-ttu-id="acc7b-133">リスナーがで定義されている場合、`<add>`の要素、`<sharedListeners>`要素、そのリスナーのフィルターで定義する必要があります、`<filter>`はの子要素、`<add>`要素。</span><span class="sxs-lookup"><span data-stu-id="acc7b-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="acc7b-134">この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="acc7b-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acc7b-135">例</span><span class="sxs-lookup"><span data-stu-id="acc7b-135">Example</span></span>  
 <span data-ttu-id="acc7b-136">次の例を使用する方法を示しています、`<filter>`トレース リスナーにフィルターを追加する要素`console`で、`sharedListeners`コレクション。</span><span class="sxs-lookup"><span data-stu-id="acc7b-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="acc7b-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="acc7b-137">See Also</span></span>  
 <xref:System.Diagnostics.TraceFilter>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="acc7b-138">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="acc7b-138">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
