---
title: "&lt;shadowCopyVerifyByTimestamp&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 261962819e9b2b37682a13bffb53d2912a660566
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a><span data-ttu-id="9eea8-102">&lt;shadowCopyVerifyByTimestamp&gt;要素</span><span class="sxs-lookup"><span data-stu-id="9eea8-102">&lt;shadowCopyVerifyByTimestamp&gt; Element</span></span>
<span data-ttu-id="9eea8-103">シャドウ コピーが [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] で導入された既定の起動の動作を使用するか、.NET Framework の以前のバージョンの起動の動作に戻すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9eea8-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="9eea8-104">\<configuration > 要素</span><span class="sxs-lookup"><span data-stu-id="9eea8-104">\<configuration> Element</span></span>  
<span data-ttu-id="9eea8-105">\<ランタイム > 要素</span><span class="sxs-lookup"><span data-stu-id="9eea8-105">\<runtime> Element</span></span>  
<span data-ttu-id="9eea8-106">\<shadowCopyVerifyByTimestamp > 要素</span><span class="sxs-lookup"><span data-stu-id="9eea8-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eea8-107">構文</span><span class="sxs-lookup"><span data-stu-id="9eea8-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eea8-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9eea8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9eea8-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9eea8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eea8-110">属性</span><span class="sxs-lookup"><span data-stu-id="9eea8-110">Attributes</span></span>  
  
|<span data-ttu-id="9eea8-111">属性</span><span class="sxs-lookup"><span data-stu-id="9eea8-111">Attribute</span></span>|<span data-ttu-id="9eea8-112">説明</span><span class="sxs-lookup"><span data-stu-id="9eea8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9eea8-113">enabled</span><span class="sxs-lookup"><span data-stu-id="9eea8-113">enabled</span></span>|<span data-ttu-id="9eea8-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="9eea8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="9eea8-115">起動時、アセンブリをシャドウ コピーする前に、アセンブリが更新されているかどうかを確認するシャドウ コピーを使用するアプリケーション ドメインがアセンブリのタイムスタンプを比較するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9eea8-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9eea8-116">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="9eea8-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="9eea8-117">値</span><span class="sxs-lookup"><span data-stu-id="9eea8-117">Value</span></span>|<span data-ttu-id="9eea8-118">説明</span><span class="sxs-lookup"><span data-stu-id="9eea8-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9eea8-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="9eea8-119">true</span></span>|<span data-ttu-id="9eea8-120">起動時に、前回シャドウ コピーのディレクトリにコピーされたとき以降に更新されたアセンブリだけをコピーします。</span><span class="sxs-lookup"><span data-stu-id="9eea8-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="9eea8-121">これは、既定値を[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9eea8-121">This is the default for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>|  
|<span data-ttu-id="9eea8-122">false</span><span class="sxs-lookup"><span data-stu-id="9eea8-122">false</span></span>|<span data-ttu-id="9eea8-123">起動時にすべてのファイルをコピーしましたが、.NET Framework の以前のバージョンの起動時の動作に戻ります。</span><span class="sxs-lookup"><span data-stu-id="9eea8-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9eea8-124">子要素</span><span class="sxs-lookup"><span data-stu-id="9eea8-124">Child Elements</span></span>  
 <span data-ttu-id="9eea8-125">なし。</span><span class="sxs-lookup"><span data-stu-id="9eea8-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9eea8-126">親要素</span><span class="sxs-lookup"><span data-stu-id="9eea8-126">Parent Elements</span></span>  
  
|<span data-ttu-id="9eea8-127">要素</span><span class="sxs-lookup"><span data-stu-id="9eea8-127">Element</span></span>|<span data-ttu-id="9eea8-128">説明</span><span class="sxs-lookup"><span data-stu-id="9eea8-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9eea8-129">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="9eea8-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9eea8-130">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9eea8-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eea8-131">コメント</span><span class="sxs-lookup"><span data-stu-id="9eea8-131">Remarks</span></span>  
 <span data-ttu-id="9eea8-132">以降で、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]アセンブリのシャドウ コピーのタイムスタンプでは、シャドウ コピーのディレクトリに前回コピーされたとき以降に変更されたことを示している場合のみです。</span><span class="sxs-lookup"><span data-stu-id="9eea8-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="9eea8-133">」の説明に従って、シャドウ コピーを使用する多くのアプリケーションの起動時間が短縮この[アセンブリのシャドウ コピー](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)です。</span><span class="sxs-lookup"><span data-stu-id="9eea8-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="9eea8-134">割合が高いと、アセンブリの更新の頻度を持つアプリケーションは、この動作の変更による利点がないです。</span><span class="sxs-lookup"><span data-stu-id="9eea8-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="9eea8-135">その場合は、この要素を使用して、.NET Framework の以前のバージョンの動作を復元することができます。</span><span class="sxs-lookup"><span data-stu-id="9eea8-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eea8-136">例</span><span class="sxs-lookup"><span data-stu-id="9eea8-136">Example</span></span>  
 <span data-ttu-id="9eea8-137">次の例のシャドウ コピーの既定のスタートアップ動作を無効にする方法を示しています、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]、し、.NET Framework の以前のバージョンの起動時の動作に戻します。</span><span class="sxs-lookup"><span data-stu-id="9eea8-137">The following example shows how to disable the default startup behavior of shadow copying in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9eea8-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="9eea8-138">See Also</span></span>  
 [<span data-ttu-id="9eea8-139">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="9eea8-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="9eea8-140">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="9eea8-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="9eea8-141">アセンブリのシャドウ コピー</span><span class="sxs-lookup"><span data-stu-id="9eea8-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
