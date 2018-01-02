---
title: "&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c370bc9ea5f8c3cdbf8690c7e22788b1224f4df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a><span data-ttu-id="f7bfc-102">&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt;要素</span><span class="sxs-lookup"><span data-stu-id="f7bfc-102">&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; Element</span></span>
<span data-ttu-id="f7bfc-103">ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドで固定量のメモリを使用してハッシュ コードを計算するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f7bfc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f7bfc-104">\<configuration></span></span>  
<span data-ttu-id="f7bfc-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="f7bfc-105">\<runtime></span></span>  
<span data-ttu-id="f7bfc-106">< NetFx45_CultureAwareComparerGetHashCode_LongStrings ></span><span class="sxs-lookup"><span data-stu-id="f7bfc-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7bfc-107">構文</span><span class="sxs-lookup"><span data-stu-id="f7bfc-107">Syntax</span></span>  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7bfc-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f7bfc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f7bfc-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7bfc-110">属性</span><span class="sxs-lookup"><span data-stu-id="f7bfc-110">Attributes</span></span>  
  
|<span data-ttu-id="f7bfc-111">属性</span><span class="sxs-lookup"><span data-stu-id="f7bfc-111">Attribute</span></span>|<span data-ttu-id="f7bfc-112">説明</span><span class="sxs-lookup"><span data-stu-id="f7bfc-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f7bfc-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f7bfc-114">ハッシュ コードを計算するときに、共通言語ランタイムが固定メモリを割り当てるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f7bfc-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="f7bfc-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="f7bfc-116">値</span><span class="sxs-lookup"><span data-stu-id="f7bfc-116">Value</span></span>|<span data-ttu-id="f7bfc-117">説明</span><span class="sxs-lookup"><span data-stu-id="f7bfc-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f7bfc-118">0</span><span class="sxs-lookup"><span data-stu-id="f7bfc-118">0</span></span>|<span data-ttu-id="f7bfc-119">共通言語ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドに可変メモリを割り当ててハッシュ コードを計算します。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="f7bfc-120">既定値です。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-120">This is the default.</span></span>|  
|<span data-ttu-id="f7bfc-121">1</span><span class="sxs-lookup"><span data-stu-id="f7bfc-121">1</span></span>|<span data-ttu-id="f7bfc-122">共通言語ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドに固定メモリを割り当ててハッシュ コードを計算します。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7bfc-123">子要素</span><span class="sxs-lookup"><span data-stu-id="f7bfc-123">Child Elements</span></span>  
 <span data-ttu-id="f7bfc-124">なし。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7bfc-125">親要素</span><span class="sxs-lookup"><span data-stu-id="f7bfc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f7bfc-126">要素</span><span class="sxs-lookup"><span data-stu-id="f7bfc-126">Element</span></span>|<span data-ttu-id="f7bfc-127">説明</span><span class="sxs-lookup"><span data-stu-id="f7bfc-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f7bfc-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f7bfc-129">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-129">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7bfc-130">コメント</span><span class="sxs-lookup"><span data-stu-id="f7bfc-130">Remarks</span></span>  
 <span data-ttu-id="f7bfc-131">既定では、共通言語ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドに可変メモリを割り当て、メソッドが非常に長い文字列 (数メガバイト以上) のハッシュ コードを計算しようとすると <xref:System.ArgumentException> 例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="f7bfc-132">この要素をアプリケーション構成ファイルに追加し、`enabled` 属性を 1 に設定すると、<xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドでハッシュ コードの計算時に固定メモリを割り当てる別のアルゴリズムを使用することを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7bfc-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` 要素は [!INCLUDE[win8](../../../../../includes/win8-md.md)] 以降のバージョンでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="f7bfc-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bfc-134">参照</span><span class="sxs-lookup"><span data-stu-id="f7bfc-134">See Also</span></span>  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f7bfc-135">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="f7bfc-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="f7bfc-136">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="f7bfc-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
