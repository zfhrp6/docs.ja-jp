---
title: "&lt;PreferComInsteadOfManagedRemoting&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad60d73e30bf02fd52f9c8f3bd707b571959bdd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="1778d-102">&lt;PreferComInsteadOfManagedRemoting&gt;要素</span><span class="sxs-lookup"><span data-stu-id="1778d-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="1778d-103">かどうか、ランタイムを使用して COM 相互運用機能リモート処理ではなく呼び出しは、すべてのアプリケーション ドメインの境界を越えてを指定します。</span><span class="sxs-lookup"><span data-stu-id="1778d-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="1778d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1778d-104">\<configuration></span></span>  
<span data-ttu-id="1778d-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="1778d-105">\<runtime></span></span>  
<span data-ttu-id="1778d-106">\<PreferComInsteadOfManagedRemoting ></span><span class="sxs-lookup"><span data-stu-id="1778d-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1778d-107">構文</span><span class="sxs-lookup"><span data-stu-id="1778d-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1778d-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1778d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1778d-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1778d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1778d-110">属性</span><span class="sxs-lookup"><span data-stu-id="1778d-110">Attributes</span></span>  
  
|<span data-ttu-id="1778d-111">属性</span><span class="sxs-lookup"><span data-stu-id="1778d-111">Attribute</span></span>|<span data-ttu-id="1778d-112">説明</span><span class="sxs-lookup"><span data-stu-id="1778d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1778d-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="1778d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1778d-114">ランタイムは COM 相互運用機能のリモート処理ではなくアプリケーション ドメインの境界を越えて使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="1778d-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1778d-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="1778d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1778d-116">値</span><span class="sxs-lookup"><span data-stu-id="1778d-116">Value</span></span>|<span data-ttu-id="1778d-117">説明</span><span class="sxs-lookup"><span data-stu-id="1778d-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1778d-118">ランタイムは、アプリケーション ドメインの境界を越えて、リモート処理を使用します。</span><span class="sxs-lookup"><span data-stu-id="1778d-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="1778d-119">既定値です。</span><span class="sxs-lookup"><span data-stu-id="1778d-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="1778d-120">ランタイムは、アプリケーション ドメインの境界を越えて COM 相互運用機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="1778d-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1778d-121">子要素</span><span class="sxs-lookup"><span data-stu-id="1778d-121">Child Elements</span></span>  
 <span data-ttu-id="1778d-122">なし。</span><span class="sxs-lookup"><span data-stu-id="1778d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1778d-123">親要素</span><span class="sxs-lookup"><span data-stu-id="1778d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1778d-124">要素</span><span class="sxs-lookup"><span data-stu-id="1778d-124">Element</span></span>|<span data-ttu-id="1778d-125">説明</span><span class="sxs-lookup"><span data-stu-id="1778d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1778d-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="1778d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1778d-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1778d-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1778d-128">コメント</span><span class="sxs-lookup"><span data-stu-id="1778d-128">Remarks</span></span>  
 <span data-ttu-id="1778d-129">設定すると、`enabled`属性を`true`ランタイムが次のように動作します。</span><span class="sxs-lookup"><span data-stu-id="1778d-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="1778d-130">ランタイムは呼び出しません[iunknown::queryinterface](http://go.microsoft.com/fwlink/?LinkID=144867)の[IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)インターフェイスの場合、 [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003)インターフェイスが COM インターフェイスを使用してドメインを入力します。</span><span class="sxs-lookup"><span data-stu-id="1778d-130">The runtime does not call [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="1778d-131">代わりに、構築、[ランタイム呼び出し可能ラッパー](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) オブジェクトの周りです。</span><span class="sxs-lookup"><span data-stu-id="1778d-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="1778d-132">受信すると、ランタイムは E_NOINTERFACE を返します、`QueryInterface`を呼び出して、 [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)のいずれかのインターフェイス[COM 呼び出し可能ラッパー](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) このドメインで作成されました。</span><span class="sxs-lookup"><span data-stu-id="1778d-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="1778d-133">これら 2 つの動作では、COM 経由でのすべての呼び出しがアプリケーション ドメインの境界を使用して COM を越えてマネージ オブジェクトとリモート処理ではなく COM 相互運用機能間でやり取りすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1778d-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1778d-134">例</span><span class="sxs-lookup"><span data-stu-id="1778d-134">Example</span></span>  
 <span data-ttu-id="1778d-135">次の例では、分離の境界を越えて相互運用、ランタイムで COM を使用するように指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1778d-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1778d-136">参照</span><span class="sxs-lookup"><span data-stu-id="1778d-136">See Also</span></span>  
 [<span data-ttu-id="1778d-137">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="1778d-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="1778d-138">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="1778d-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
