---
title: "&lt;legacyCorruptedStateExceptionsPolicy&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4379f6f38c886504905483cefd7c7a6bbd519ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a><span data-ttu-id="5c8be-102">&lt;legacyCorruptedStateExceptionsPolicy&gt;要素</span><span class="sxs-lookup"><span data-stu-id="5c8be-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; Element</span></span>
<span data-ttu-id="5c8be-103">共通言語ランタイムにアクセス違反およびその他の破損状態例外をキャッチするマネージ コードができるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5c8be-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="5c8be-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5c8be-104">\<configuration></span></span>  
<span data-ttu-id="5c8be-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="5c8be-105">\<runtime></span></span>  
<span data-ttu-id="5c8be-106">\<legacyCorruptedStateExceptionsPolicy ></span><span class="sxs-lookup"><span data-stu-id="5c8be-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c8be-107">構文</span><span class="sxs-lookup"><span data-stu-id="5c8be-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c8be-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5c8be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5c8be-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c8be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c8be-110">属性</span><span class="sxs-lookup"><span data-stu-id="5c8be-110">Attributes</span></span>  
  
|<span data-ttu-id="5c8be-111">属性</span><span class="sxs-lookup"><span data-stu-id="5c8be-111">Attribute</span></span>|<span data-ttu-id="5c8be-112">説明</span><span class="sxs-lookup"><span data-stu-id="5c8be-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5c8be-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="5c8be-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5c8be-114">アプリケーションがキャッチすることを指定の破損状態例外エラー アクセス違反などです。</span><span class="sxs-lookup"><span data-stu-id="5c8be-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5c8be-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="5c8be-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5c8be-116">値</span><span class="sxs-lookup"><span data-stu-id="5c8be-116">Value</span></span>|<span data-ttu-id="5c8be-117">説明</span><span class="sxs-lookup"><span data-stu-id="5c8be-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5c8be-118">アプリケーションは検出されません破損状態例外エラー アクセス違反などです。</span><span class="sxs-lookup"><span data-stu-id="5c8be-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="5c8be-119">既定値です。</span><span class="sxs-lookup"><span data-stu-id="5c8be-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5c8be-120">アプリケーションがキャッチ破損状態例外エラー アクセス違反などです。</span><span class="sxs-lookup"><span data-stu-id="5c8be-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c8be-121">子要素</span><span class="sxs-lookup"><span data-stu-id="5c8be-121">Child Elements</span></span>  
 <span data-ttu-id="5c8be-122">なし。</span><span class="sxs-lookup"><span data-stu-id="5c8be-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c8be-123">親要素</span><span class="sxs-lookup"><span data-stu-id="5c8be-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5c8be-124">要素</span><span class="sxs-lookup"><span data-stu-id="5c8be-124">Element</span></span>|<span data-ttu-id="5c8be-125">説明</span><span class="sxs-lookup"><span data-stu-id="5c8be-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5c8be-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="5c8be-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5c8be-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c8be-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c8be-128">コメント</span><span class="sxs-lookup"><span data-stu-id="5c8be-128">Remarks</span></span>  
 <span data-ttu-id="5c8be-129">.NET Framework バージョン 3.5 以前では、共通言語ランタイムは、破損しているプロセスの状態で発生した例外をキャッチするマネージ コードを許可します。</span><span class="sxs-lookup"><span data-stu-id="5c8be-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="5c8be-130">アクセス違反は、この種類の例外の例を示します。</span><span class="sxs-lookup"><span data-stu-id="5c8be-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="5c8be-131">以降で、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、マネージ コードが不要になったこれらの型の例外をキャッチ`catch`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="5c8be-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="5c8be-132">ただし、この変更をオーバーライドして、2 つの方法で破損状態例外の処理を維持できます。</span><span class="sxs-lookup"><span data-stu-id="5c8be-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="5c8be-133">設定、`<legacyCorruptedStateExceptionsPolicy>`要素の`enabled`属性を`true`です。</span><span class="sxs-lookup"><span data-stu-id="5c8be-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="5c8be-134">この構成設定は適用されているプロセスであり、すべてのメソッドに影響します。</span><span class="sxs-lookup"><span data-stu-id="5c8be-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="5c8be-135">または</span><span class="sxs-lookup"><span data-stu-id="5c8be-135">-or-</span></span>  
  
-   <span data-ttu-id="5c8be-136">適用、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>属性、例外が含まれるメソッドを`catch`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="5c8be-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="5c8be-137">この構成要素はでのみ使用できますが、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]およびそれ以降。</span><span class="sxs-lookup"><span data-stu-id="5c8be-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c8be-138">例</span><span class="sxs-lookup"><span data-stu-id="5c8be-138">Example</span></span>  
 <span data-ttu-id="5c8be-139">次の例は、アプリケーションは前に、の動作を戻すかを指定する方法を示しています、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]、およびすべての破損状態例外のエラーをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="5c8be-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c8be-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c8be-140">See Also</span></span>  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [<span data-ttu-id="5c8be-141">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="5c8be-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5c8be-142">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="5c8be-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
