---
title: "&lt;追加&gt;要素&lt;スイッチ&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: de1acb37f3236598e9d8a74a188033d18b65ac8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="ac24d-102">&lt;追加&gt;要素&lt;スイッチ&gt;</span><span class="sxs-lookup"><span data-stu-id="ac24d-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="ac24d-103">トレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac24d-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="ac24d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ac24d-104">\<configuration></span></span>  
<span data-ttu-id="ac24d-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="ac24d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="ac24d-106">\<スイッチ ></span><span class="sxs-lookup"><span data-stu-id="ac24d-106">\<switches></span></span>  
<span data-ttu-id="ac24d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ac24d-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac24d-108">構文</span><span class="sxs-lookup"><span data-stu-id="ac24d-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac24d-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ac24d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ac24d-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac24d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac24d-111">属性</span><span class="sxs-lookup"><span data-stu-id="ac24d-111">Attributes</span></span>  
  
|<span data-ttu-id="ac24d-112">属性</span><span class="sxs-lookup"><span data-stu-id="ac24d-112">Attribute</span></span>|<span data-ttu-id="ac24d-113">説明</span><span class="sxs-lookup"><span data-stu-id="ac24d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac24d-114">**name**</span><span class="sxs-lookup"><span data-stu-id="ac24d-114">**name**</span></span>|<span data-ttu-id="ac24d-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ac24d-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac24d-116">スイッチの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac24d-116">Specifies the name of the switch.</span></span> <span data-ttu-id="ac24d-117">この属性の値に対応、 *displayName*切り替えるコンス トラクターに渡されるパラメーター。</span><span class="sxs-lookup"><span data-stu-id="ac24d-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="ac24d-118">**value**</span><span class="sxs-lookup"><span data-stu-id="ac24d-118">**value**</span></span>|<span data-ttu-id="ac24d-119">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ac24d-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac24d-120">スイッチのレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac24d-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac24d-121">子要素</span><span class="sxs-lookup"><span data-stu-id="ac24d-121">Child Elements</span></span>  
 <span data-ttu-id="ac24d-122">なし。</span><span class="sxs-lookup"><span data-stu-id="ac24d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac24d-123">親要素</span><span class="sxs-lookup"><span data-stu-id="ac24d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ac24d-124">要素</span><span class="sxs-lookup"><span data-stu-id="ac24d-124">Element</span></span>|<span data-ttu-id="ac24d-125">説明</span><span class="sxs-lookup"><span data-stu-id="ac24d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ac24d-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ac24d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="ac24d-127">トレース スイッチと、トレース スイッチを設定するレベルを保持します。</span><span class="sxs-lookup"><span data-stu-id="ac24d-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ac24d-128">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac24d-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac24d-129">コメント</span><span class="sxs-lookup"><span data-stu-id="ac24d-129">Remarks</span></span>  
 <span data-ttu-id="ac24d-130">トレース スイッチのレベルを変更するには、構成ファイルに配置します。</span><span class="sxs-lookup"><span data-stu-id="ac24d-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="ac24d-131">スイッチの場合、 <xref:System.Diagnostics.BooleanSwitch>、オンまたはオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ac24d-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="ac24d-132">スイッチの場合、<xref:System.Diagnostics.TraceSwitch>トレースの種類を指定するためにさまざまなレベルを割り当てることができます、またはデバッグ メッセージをアプリケーションが出力されます。</span><span class="sxs-lookup"><span data-stu-id="ac24d-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac24d-133">例</span><span class="sxs-lookup"><span data-stu-id="ac24d-133">Example</span></span>  
 <span data-ttu-id="ac24d-134">次の例を使用する方法を示しています、 **\<を追加 >**を設定する要素、`General`トレース スイッチを<xref:System.Diagnostics.TraceLevel>レベル、および有効にする、`Data`ブール トレース スイッチ。</span><span class="sxs-lookup"><span data-stu-id="ac24d-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac24d-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac24d-135">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="ac24d-136">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="ac24d-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
