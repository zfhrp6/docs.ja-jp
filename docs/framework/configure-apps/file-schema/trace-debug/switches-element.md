---
title: "&lt;スイッチ&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6240f8192f2a31faeb81528e54481eb06cc04d04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="0cc64-102">&lt;スイッチ&gt;要素</span><span class="sxs-lookup"><span data-stu-id="0cc64-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="0cc64-103">トレース スイッチと、トレース スイッチを設定するレベルを保持します。</span><span class="sxs-lookup"><span data-stu-id="0cc64-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="0cc64-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0cc64-104">\<configuration></span></span>  
<span data-ttu-id="0cc64-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="0cc64-105">\<system.diagnostics></span></span>  
<span data-ttu-id="0cc64-106">\<スイッチ ></span><span class="sxs-lookup"><span data-stu-id="0cc64-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cc64-107">構文</span><span class="sxs-lookup"><span data-stu-id="0cc64-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cc64-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0cc64-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0cc64-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0cc64-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cc64-110">属性</span><span class="sxs-lookup"><span data-stu-id="0cc64-110">Attributes</span></span>  
 <span data-ttu-id="0cc64-111">なし。</span><span class="sxs-lookup"><span data-stu-id="0cc64-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0cc64-112">子要素</span><span class="sxs-lookup"><span data-stu-id="0cc64-112">Child Elements</span></span>  
  
|<span data-ttu-id="0cc64-113">要素</span><span class="sxs-lookup"><span data-stu-id="0cc64-113">Element</span></span>|<span data-ttu-id="0cc64-114">説明</span><span class="sxs-lookup"><span data-stu-id="0cc64-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cc64-115">\<add></span><span class="sxs-lookup"><span data-stu-id="0cc64-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="0cc64-116">トレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="0cc64-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0cc64-117">親要素</span><span class="sxs-lookup"><span data-stu-id="0cc64-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0cc64-118">要素</span><span class="sxs-lookup"><span data-stu-id="0cc64-118">Element</span></span>|<span data-ttu-id="0cc64-119">説明</span><span class="sxs-lookup"><span data-stu-id="0cc64-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0cc64-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="0cc64-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="0cc64-121">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="0cc64-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cc64-122">コメント</span><span class="sxs-lookup"><span data-stu-id="0cc64-122">Remarks</span></span>  
 <span data-ttu-id="0cc64-123">トレース スイッチのレベルを変更するには、構成ファイルに配置します。</span><span class="sxs-lookup"><span data-stu-id="0cc64-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="0cc64-124">スイッチの場合、 <xref:System.Diagnostics.BooleanSwitch>、オンまたはオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="0cc64-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="0cc64-125">スイッチの場合、<xref:System.Diagnostics.TraceSwitch>トレースの種類を指定するためにさまざまなレベルを割り当てることができます、またはデバッグ メッセージをアプリケーションが出力されます。</span><span class="sxs-lookup"><span data-stu-id="0cc64-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cc64-126">例</span><span class="sxs-lookup"><span data-stu-id="0cc64-126">Example</span></span>  
 <span data-ttu-id="0cc64-127">次の例を使用する方法を示しています、 **\<スイッチ >**を設定する要素、`General`トレース スイッチを<xref:System.Diagnostics.TraceLevel>レベル、および有効にする、`Data`ブール トレース スイッチ。</span><span class="sxs-lookup"><span data-stu-id="0cc64-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cc64-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cc64-128">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="0cc64-129">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="0cc64-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
