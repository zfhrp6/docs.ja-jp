---
title: "ICLRMetaHost::GetRuntime メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 849668f10eba81ba1667ac6518ab699e4bca3bcb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="27cf1-102">ICLRMetaHost::GetRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="27cf1-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="27cf1-103">取得、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)共通言語ランタイム (CLR) の特定のバージョンに対応するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="27cf1-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="27cf1-104">このメソッドは、 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)で使用される関数、 [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)フラグ。</span><span class="sxs-lookup"><span data-stu-id="27cf1-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27cf1-105">構文</span><span class="sxs-lookup"><span data-stu-id="27cf1-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27cf1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27cf1-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="27cf1-107">[in]形式で、メタデータに格納されている .NET Framework のコンパイル バージョン"v*A*.*B*[.*X*]"です。</span><span class="sxs-lookup"><span data-stu-id="27cf1-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="27cf1-108">*A*、 *B*、および*X*はメジャー バージョン、マイナー バージョン、およびビルド番号に対応する 10 進数。</span><span class="sxs-lookup"><span data-stu-id="27cf1-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27cf1-109">このパラメーターは、C:\Windows\Microsoft.NET\Framework または C:\Windows\Microsoft.NET\Framework64 で表示される、.NET Framework のバージョンのディレクトリ名と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27cf1-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="27cf1-110">値の例は、"v1.0.3705"、"v1.1.4322"、"v2.0.50727"および"v4.0 です。*X*"ここで、 *X*インストールされているビルドの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="27cf1-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="27cf1-111">"V"プレフィックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="27cf1-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="27cf1-112">[in]目的のインターフェイスの識別子です。</span><span class="sxs-lookup"><span data-stu-id="27cf1-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="27cf1-113">現時点では、このパラメーターの唯一の有効な値は、IID_ICLRRuntimeInfo がします。</span><span class="sxs-lookup"><span data-stu-id="27cf1-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="27cf1-114">[out]ポインター、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)要求されたランタイムに対応するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="27cf1-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27cf1-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="27cf1-115">Return Value</span></span>  
 <span data-ttu-id="27cf1-116">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="27cf1-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="27cf1-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27cf1-117">HRESULT</span></span>|<span data-ttu-id="27cf1-118">説明</span><span class="sxs-lookup"><span data-stu-id="27cf1-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27cf1-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="27cf1-119">S_OK</span></span>|<span data-ttu-id="27cf1-120">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="27cf1-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="27cf1-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="27cf1-121">E_POINTER</span></span>|<span data-ttu-id="27cf1-122">`pwzVersion` または `ppRuntime` が null です。</span><span class="sxs-lookup"><span data-stu-id="27cf1-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27cf1-123">コメント</span><span class="sxs-lookup"><span data-stu-id="27cf1-123">Remarks</span></span>  
 <span data-ttu-id="27cf1-124">このメソッドが対話一貫して従来のインターフェイスなど、 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)インターフェイスおよび従来の機能など、非推奨`CorBindTo*`関数 (を参照してください[廃止 CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) API をホストしている .NET Framework 2.0 で)。</span><span class="sxs-lookup"><span data-stu-id="27cf1-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="27cf1-125">従来の API が読み込まれているランタイムは、新しい API を表示でき、新しい API が読み込まれているランタイムがレガシ API に表示されます。</span><span class="sxs-lookup"><span data-stu-id="27cf1-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span> <span data-ttu-id="27cf1-126">である必要があります。</span><span class="sxs-lookup"><span data-stu-id="27cf1-126">.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27cf1-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="27cf1-127">Requirements</span></span>  
 <span data-ttu-id="27cf1-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="27cf1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27cf1-129">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="27cf1-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="27cf1-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="27cf1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27cf1-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27cf1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27cf1-132">参照</span><span class="sxs-lookup"><span data-stu-id="27cf1-132">See Also</span></span>  
 [<span data-ttu-id="27cf1-133">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27cf1-133">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="27cf1-134">サポートされなくなった CLR のホスト インターフェイスおよびコクラス</span><span class="sxs-lookup"><span data-stu-id="27cf1-134">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 [<span data-ttu-id="27cf1-135">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27cf1-135">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="27cf1-136">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="27cf1-136">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="27cf1-137">ホスティング</span><span class="sxs-lookup"><span data-stu-id="27cf1-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
