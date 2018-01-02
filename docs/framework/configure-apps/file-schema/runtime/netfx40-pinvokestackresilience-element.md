---
title: "&lt;NetFx40_PInvokeStackResilience&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b17816ee6134dc6b3074256093c0cba07419baf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a><span data-ttu-id="fbbeb-102">&lt;NetFx40_PInvokeStackResilience&gt;要素</span><span class="sxs-lookup"><span data-stu-id="fbbeb-102">&lt;NetFx40_PInvokeStackResilience&gt; Element</span></span>
<span data-ttu-id="fbbeb-103">ランタイムが実行時の不適切なプラットフォーム呼び出し宣言を自動的に修正するかどうかを指定します。これにより、マネージ コードとアンマネージ コード間の遷移が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="fbbeb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="fbbeb-104">\<configuration></span></span>  
<span data-ttu-id="fbbeb-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="fbbeb-105">\<runtime></span></span>  
<span data-ttu-id="fbbeb-106">< NetFx40_PInvokeStackResilience ></span><span class="sxs-lookup"><span data-stu-id="fbbeb-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbbeb-107">構文</span><span class="sxs-lookup"><span data-stu-id="fbbeb-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbbeb-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fbbeb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fbbeb-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbbeb-110">属性</span><span class="sxs-lookup"><span data-stu-id="fbbeb-110">Attributes</span></span>  
  
|<span data-ttu-id="fbbeb-111">属性</span><span class="sxs-lookup"><span data-stu-id="fbbeb-111">Attribute</span></span>|<span data-ttu-id="fbbeb-112">説明</span><span class="sxs-lookup"><span data-stu-id="fbbeb-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fbbeb-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fbbeb-114">ランタイムは不適切なプラットフォームを検出するかどうかを示す宣言を呼び出すし、スタックを 32 ビット プラットフォーム上で実行時に自動的に修正します。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fbbeb-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="fbbeb-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="fbbeb-116">値</span><span class="sxs-lookup"><span data-stu-id="fbbeb-116">Value</span></span>|<span data-ttu-id="fbbeb-117">説明</span><span class="sxs-lookup"><span data-stu-id="fbbeb-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="fbbeb-118">ランタイムは、高速の相互運用マーシャ リングで導入されたアーキテクチャを使用して、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]が検出されない、および修正プログラムの不適切なプラットフォーム呼び出しの宣言。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="fbbeb-119">既定値です。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="fbbeb-120">ランタイムは低速の遷移を検出して修正する不適切なプラットフォーム呼び出しの宣言。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbbeb-121">子要素</span><span class="sxs-lookup"><span data-stu-id="fbbeb-121">Child Elements</span></span>  
 <span data-ttu-id="fbbeb-122">なし。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fbbeb-123">親要素</span><span class="sxs-lookup"><span data-stu-id="fbbeb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fbbeb-124">要素</span><span class="sxs-lookup"><span data-stu-id="fbbeb-124">Element</span></span>|<span data-ttu-id="fbbeb-125">説明</span><span class="sxs-lookup"><span data-stu-id="fbbeb-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fbbeb-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fbbeb-127">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbbeb-128">コメント</span><span class="sxs-lookup"><span data-stu-id="fbbeb-128">Remarks</span></span>  
 <span data-ttu-id="fbbeb-129">この要素では、高速相互運用マーシャ リング ランタイム回復不適切なプラットフォーム呼び出しの宣言を交換することができます。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="fbbeb-130">以降で、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]アーキテクチャをマーシャ リングの簡素化された相互運用機能は、マネージ コードからアンマネージ コードへの遷移の大幅なパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="fbbeb-131">.NET Framework の以前のバージョンでは、マーシャ リング レイヤーが検出されましたが正しくありませんプラットフォームは、呼び出しの 32 ビット プラットフォーム上で宣言され、スタックを自動的に固定されます。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="fbbeb-132">マーシャ リングの新しいアーキテクチャでは、この手順が排除されます。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="fbbeb-133">この結果、遷移は非常に高速が不適切なプラットフォーム呼び出しの宣言プログラム エラーが発生することができます。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="fbbeb-134">開発中に正しくない宣言を検出するために簡単に、Visual Studio のデバッグ機能が改善されました。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="fbbeb-135">[PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)マネージ デバッグ アシスタント (MDA) は、アタッチされたデバッガーでアプリケーションが実行されているときに、宣言を呼び出す不適切なプラットフォームに通知します。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="fbbeb-136">コンポーネントを再コンパイルすることはできません、およびことが不適切なプラットフォーム呼び出しの宣言を行うこともできますが、アプリケーションにで使用されているアドレス シナリオを`NetFx40_PInvokeStackResilience`要素。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="fbbeb-137">この要素で、アプリケーション構成ファイルを追加する`enabled="1"`opts 低速の遷移しますが、.NET Framework の以前のバージョンの動作と互換性があるモードにします。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="fbbeb-138">.NET Framework の以前のバージョンに対してコンパイルされたアセンブリでは、この互換モードが自動的に選択されるためし、この要素は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fbbeb-139">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="fbbeb-139">Configuration File</span></span>  
 <span data-ttu-id="fbbeb-140">この要素は、アプリケーション構成ファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbbeb-141">例</span><span class="sxs-lookup"><span data-stu-id="fbbeb-141">Example</span></span>  
 <span data-ttu-id="fbbeb-142">例を次にマネージ コードに対する不適切な回復を強化を選択するプラットフォーム呼び出しの間の遷移が遅くなりますが、アプリケーションの宣言方法とアンマネージ コードです。</span><span class="sxs-lookup"><span data-stu-id="fbbeb-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbbeb-143">参照</span><span class="sxs-lookup"><span data-stu-id="fbbeb-143">See Also</span></span>  
 [<span data-ttu-id="fbbeb-144">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="fbbeb-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="fbbeb-145">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="fbbeb-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="fbbeb-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="fbbeb-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
