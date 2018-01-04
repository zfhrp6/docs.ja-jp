---
title: "ICLRRuntimeHost インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost
helpviewer_keywords: ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type: apiref
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 247c50eb88f3b1814fd5342ded4ed3c98d4b60a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="d938d-102">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d938d-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="d938d-103">類似の機能を提供、 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)バージョン 1 の場合、次の変更と .NET Framework で提供されるインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="d938d-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
-   <span data-ttu-id="d938d-104">追加、 [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)ホスト コントロールのインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="d938d-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
-   <span data-ttu-id="d938d-105">によって提供されるいくつかのメソッドの省略`ICorRuntimeHost`です。</span><span class="sxs-lookup"><span data-stu-id="d938d-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d938d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-106">Methods</span></span>  
  
|<span data-ttu-id="d938d-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-107">Method</span></span>|<span data-ttu-id="d938d-108">説明</span><span class="sxs-lookup"><span data-stu-id="d938d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d938d-109">ExecuteApplication メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="d938d-110">新しいドメインでアクティブにするアプリケーションを指定するマニフェストに基づく ClickOnce の配置シナリオに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d938d-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="d938d-111">ExecuteInAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="d938d-112">指定します、<xref:System.AppDomain>指定したマネージ コードを実行するためです。</span><span class="sxs-lookup"><span data-stu-id="d938d-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="d938d-113">ExecuteInDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="d938d-114">指定したアセンブリで指定した型の指定したメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d938d-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="d938d-115">GetCLRControl メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="d938d-116">型のインターフェイス ポインターを取得[ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)ホストが共通言語ランタイム (CLR) のカスタマイズに使用できます。</span><span class="sxs-lookup"><span data-stu-id="d938d-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="d938d-117">GetCurrentAppDomainId メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="d938d-118">数値識別子を取得、<xref:System.AppDomain>が現在実行されています。</span><span class="sxs-lookup"><span data-stu-id="d938d-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="d938d-119">SetHostControl メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="d938d-120">ホスト コントロールのインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="d938d-120">Sets the host control interface.</span></span> <span data-ttu-id="d938d-121">呼び出す必要があります`SetHostControl`呼び出す前に`Start`です。</span><span class="sxs-lookup"><span data-stu-id="d938d-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="d938d-122">Start メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="d938d-123">プロセスに CLR を初期化します。</span><span class="sxs-lookup"><span data-stu-id="d938d-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="d938d-124">Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="d938d-125">ランタイムによってコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="d938d-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="d938d-126">UnloadAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="d938d-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="d938d-127">アンロード、<xref:System.AppDomain>指定した数値識別子に対応します。</span><span class="sxs-lookup"><span data-stu-id="d938d-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d938d-128">コメント</span><span class="sxs-lookup"><span data-stu-id="d938d-128">Remarks</span></span>  
 <span data-ttu-id="d938d-129">以降で、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]を使用して、 [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)へのポインターを取得するインターフェイス、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイス、およびを呼び出す、 [iclrruntimeinfo::getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)へのポインターを取得するメソッド`ICLRRuntimeHost`です。</span><span class="sxs-lookup"><span data-stu-id="d938d-129">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="d938d-130">.NET Framework の以前のバージョンで、ホストのポインターを取得する、`ICLRRuntimeHost`を呼び出してインスタンス[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)または[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="d938d-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="d938d-131">使用する必要があります、.NET Framework version 2.0 で提供されるテクノロジのいずれかの実装を提供する`ICLRRuntimeHost`の代わりに`ICorRuntimeHost`です。</span><span class="sxs-lookup"><span data-stu-id="d938d-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d938d-132">呼び出す必要はありません、[開始](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)メソッドを呼び出す前に、 [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)マニフェスト ベースのアプリケーションをアクティブ化するメソッド。</span><span class="sxs-lookup"><span data-stu-id="d938d-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="d938d-133">場合、`Start`メソッドが最初と呼ばれる、`ExecuteApplication`メソッドの呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="d938d-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d938d-134">必要条件</span><span class="sxs-lookup"><span data-stu-id="d938d-134">Requirements</span></span>  
 <span data-ttu-id="d938d-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d938d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d938d-136">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d938d-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d938d-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d938d-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d938d-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d938d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d938d-139">参照</span><span class="sxs-lookup"><span data-stu-id="d938d-139">See Also</span></span>  
 [<span data-ttu-id="d938d-140">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="d938d-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="d938d-141">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="d938d-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="d938d-142">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d938d-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="d938d-143">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d938d-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="d938d-144">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d938d-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="d938d-145">CLRRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="d938d-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
