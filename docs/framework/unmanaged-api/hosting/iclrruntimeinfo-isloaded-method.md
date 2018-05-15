---
title: ICLRRuntimeInfo::IsLoaded メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ff1723cb481ee946e0c5c433009d3d6d7460cf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="2b11d-102">ICLRRuntimeInfo::IsLoaded メソッド</span><span class="sxs-lookup"><span data-stu-id="2b11d-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="2b11d-103">共通言語ランタイム (CLR) に関連付けられているかどうかを示す、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスが、プロセスに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2b11d-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="2b11d-104">開始されないままランタイムを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="2b11d-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b11d-105">構文</span><span class="sxs-lookup"><span data-stu-id="2b11d-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b11d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b11d-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="2b11d-107">[in]プロセスへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="2b11d-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="2b11d-108">[out]`true` CLR がプロセスに読み込まれ、それ以外の場合は`false`します。</span><span class="sxs-lookup"><span data-stu-id="2b11d-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b11d-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="2b11d-109">Return Value</span></span>  
 <span data-ttu-id="2b11d-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="2b11d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2b11d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b11d-111">HRESULT</span></span>|<span data-ttu-id="2b11d-112">説明</span><span class="sxs-lookup"><span data-stu-id="2b11d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b11d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b11d-113">S_OK</span></span>|<span data-ttu-id="2b11d-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="2b11d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="2b11d-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2b11d-115">E_POINTER</span></span>|<span data-ttu-id="2b11d-116">`pbLoaded` が null です。</span><span class="sxs-lookup"><span data-stu-id="2b11d-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b11d-117">コメント</span><span class="sxs-lookup"><span data-stu-id="2b11d-117">Remarks</span></span>  
 <span data-ttu-id="2b11d-118">このメソッドは、旧バージョンと互換性のある次の関数とインターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b11d-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
-   <span data-ttu-id="2b11d-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)インターフェイスに、.NET Framework バージョン 1 のホスト API)。</span><span class="sxs-lookup"><span data-stu-id="2b11d-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
-   <span data-ttu-id="2b11d-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)インターフェイスに、.NET Framework 2.0 API をホストしている)。</span><span class="sxs-lookup"><span data-stu-id="2b11d-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
-   <span data-ttu-id="2b11d-121">推奨されなくなった`CorBindTo*`関数 (を参照してください[CLR をホストしている関数の非推奨](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)API をホストしている .NET Framework 2.0 で)。</span><span class="sxs-lookup"><span data-stu-id="2b11d-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="2b11d-122">ホストは、非推奨のいずれかを呼び出すことが`CorBindTo*`などの関数、 [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)関数、CLR の特定のバージョンのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2b11d-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="2b11d-123">ホストが、呼び出し、 [iclrmetahost::getruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)メソッドを取得する同じバージョン番号を指定し、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="2b11d-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="2b11d-124">ホストが呼び出した場合、`IsLoaded`メソッドで返された[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイス、`pbLoaded`を返します`true`、それ以外を返します`false`です。</span><span class="sxs-lookup"><span data-stu-id="2b11d-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b11d-125">要件</span><span class="sxs-lookup"><span data-stu-id="2b11d-125">Requirements</span></span>  
 <span data-ttu-id="2b11d-126">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b11d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b11d-127">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2b11d-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2b11d-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="2b11d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b11d-129">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b11d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b11d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b11d-130">See Also</span></span>  
 [<span data-ttu-id="2b11d-131">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b11d-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="2b11d-132">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b11d-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="2b11d-133">ホスティング</span><span class="sxs-lookup"><span data-stu-id="2b11d-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
