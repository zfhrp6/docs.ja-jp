---
title: '&lt;alwaysFlowImpersonationPolicy&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cc704bbf8631936dbbeb3539ea5ed0d8499f378
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a><span data-ttu-id="e077c-102">&lt;alwaysFlowImpersonationPolicy&gt;要素</span><span class="sxs-lookup"><span data-stu-id="e077c-102">&lt;alwaysFlowImpersonationPolicy&gt; Element</span></span>
<span data-ttu-id="e077c-103">偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間でフローすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e077c-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
 <span data-ttu-id="e077c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e077c-104">\<configuration></span></span>  
<span data-ttu-id="e077c-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="e077c-105">\<runtime></span></span>  
<span data-ttu-id="e077c-106">\<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="e077c-106">\<alwaysFlowImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e077c-107">構文</span><span class="sxs-lookup"><span data-stu-id="e077c-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e077c-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e077c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e077c-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e077c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e077c-110">属性</span><span class="sxs-lookup"><span data-stu-id="e077c-110">Attributes</span></span>  
  
|<span data-ttu-id="e077c-111">属性</span><span class="sxs-lookup"><span data-stu-id="e077c-111">Attribute</span></span>|<span data-ttu-id="e077c-112">説明</span><span class="sxs-lookup"><span data-stu-id="e077c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e077c-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="e077c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e077c-114">Windows id が非同期ポイント間をフローするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e077c-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e077c-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="e077c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e077c-116">値</span><span class="sxs-lookup"><span data-stu-id="e077c-116">Value</span></span>|<span data-ttu-id="e077c-117">説明</span><span class="sxs-lookup"><span data-stu-id="e077c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e077c-118">管理されているメソッドをなど、Windows のユーザーでは、使用して、権限の借用が実行しない限り、非同期ポイント間フローしません<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>です。</span><span class="sxs-lookup"><span data-stu-id="e077c-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="e077c-119">既定値です。</span><span class="sxs-lookup"><span data-stu-id="e077c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="e077c-120">権限借用の実行方法に関係なく、非同期ポイント間では、Windows id が常にフローします。</span><span class="sxs-lookup"><span data-stu-id="e077c-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e077c-121">子要素</span><span class="sxs-lookup"><span data-stu-id="e077c-121">Child Elements</span></span>  
 <span data-ttu-id="e077c-122">なし。</span><span class="sxs-lookup"><span data-stu-id="e077c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e077c-123">親要素</span><span class="sxs-lookup"><span data-stu-id="e077c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e077c-124">要素</span><span class="sxs-lookup"><span data-stu-id="e077c-124">Element</span></span>|<span data-ttu-id="e077c-125">説明</span><span class="sxs-lookup"><span data-stu-id="e077c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e077c-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="e077c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e077c-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e077c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e077c-128">コメント</span><span class="sxs-lookup"><span data-stu-id="e077c-128">Remarks</span></span>  
 <span data-ttu-id="e077c-129">.NET Framework バージョン 1.0 および 1.1 では、Windows id は非同期ポイント間をフローしません。</span><span class="sxs-lookup"><span data-stu-id="e077c-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="e077c-130">.NET Framework version 2.0 では、<xref:System.Threading.ExecutionContext>オブジェクトを現在実行中のスレッドに関する情報を格納し、アプリケーション ドメイン内での非同期ポイント間をフローします。</span><span class="sxs-lookup"><span data-stu-id="e077c-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="e077c-131"><xref:System.Security.Principal.WindowsIdentity>またメソッドの管理ポイント間をフロー、非同期を使用して、権限の借用が達成された提供情報の一部としてフローなど<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>プラットフォームなどの他の方法ではなく、ネイティブ メソッドを呼び出すとします。</span><span class="sxs-lookup"><span data-stu-id="e077c-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="e077c-132">この要素を使用してを Windows id 偽装の実行方法に関係なく、非同期ポイント間をフローするを指定します。</span><span class="sxs-lookup"><span data-stu-id="e077c-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="e077c-133">他の 2 つの方法でこの既定の動作を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="e077c-133">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="e077c-134">スレッドごとにマネージ コード。</span><span class="sxs-lookup"><span data-stu-id="e077c-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="e077c-135">スレッドごとのフローを抑制するには変更することによって、<xref:System.Threading.ExecutionContext>と<xref:System.Security.SecurityContext>設定を使用して、 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>、 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>、または<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e077c-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="e077c-136">呼び出しで、アンマネージ ホスト インターフェイスを共通言語ランタイム (CLR) を読み込めません。</span><span class="sxs-lookup"><span data-stu-id="e077c-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="e077c-137">呼び出しで特別なフラグを指定できます (単純なマネージ実行可能ファイル) ではなく、アンマネージ ホスト インターフェイスが、CLR の読み込みに使用されている場合、 [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="e077c-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="e077c-138">プロセス全体の互換モードを有効にするには設定、`flags`パラメーター [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)に`STARTUP_ALWAYSFLOW_IMPERSONATION`です。</span><span class="sxs-lookup"><span data-stu-id="e077c-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e077c-139">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="e077c-139">Configuration File</span></span>  
 <span data-ttu-id="e077c-140">.NET Framework アプリケーションでこの要素は、アプリケーション構成ファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e077c-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="e077c-141">内で見つかった aspnet.config ファイルで、ASP.NET アプリケーションの権限借用のフローを構成できます、 \<Windows フォルダー > \Microsoft.NET\Framework\vx.x.xxxx ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="e077c-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="e077c-142">既定では ASP.NET には、次の構成設定を使用して、aspnet.config ファイルで、権限借用フローが無効にします。</span><span class="sxs-lookup"><span data-stu-id="e077c-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="e077c-143">ASP.NET では、代わりに、権限借用のフローを許可したい場合必要があります明示的に使用する次の構成設定。</span><span class="sxs-lookup"><span data-stu-id="e077c-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="e077c-144">例</span><span class="sxs-lookup"><span data-stu-id="e077c-144">Example</span></span>  
 <span data-ttu-id="e077c-145">次の例では、Windows id は、マネージ メソッド以外の方法で、権限の借用を実現する場合でも、非同期ポイント間でフローを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e077c-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e077c-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="e077c-146">See Also</span></span>  
 [<span data-ttu-id="e077c-147">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="e077c-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="e077c-148">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="e077c-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e077c-149">\<legacyImpersonationPolicy > 要素</span><span class="sxs-lookup"><span data-stu-id="e077c-149">\<legacyImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
