---
title: LockClrVersion 関数
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6956d73be0380baef96d94584f007e0683331784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446090"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="f5763-102">LockClrVersion 関数</span><span class="sxs-lookup"><span data-stu-id="f5763-102">LockClrVersion Function</span></span>
<span data-ttu-id="f5763-103">により、ホストがプロセス内で明示的に CLR を初期化する前に使用する共通言語ランタイム (CLR) のバージョンを決定します。</span><span class="sxs-lookup"><span data-stu-id="f5763-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="f5763-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="f5763-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5763-105">構文</span><span class="sxs-lookup"><span data-stu-id="f5763-105">Syntax</span></span>  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5763-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5763-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="f5763-107">[in]初期化時に CLR によって呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="f5763-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="f5763-108">[in]初期化の CLR を通知するためにホストによって呼び出される関数を開始しています。</span><span class="sxs-lookup"><span data-stu-id="f5763-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="f5763-109">[in]初期化の CLR を通知するためにホストによって呼び出される関数が完了しました。</span><span class="sxs-lookup"><span data-stu-id="f5763-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5763-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="f5763-110">Return Value</span></span>  
 <span data-ttu-id="f5763-111">このメソッドは、次の値に加え、WinError.h で定義されている標準の COM エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="f5763-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f5763-112">リターン コード</span><span class="sxs-lookup"><span data-stu-id="f5763-112">Return code</span></span>|<span data-ttu-id="f5763-113">説明</span><span class="sxs-lookup"><span data-stu-id="f5763-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f5763-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5763-114">S_OK</span></span>|<span data-ttu-id="f5763-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="f5763-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="f5763-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f5763-116">E_INVALIDARG</span></span>|<span data-ttu-id="f5763-117">1 つ以上の引数が null です。</span><span class="sxs-lookup"><span data-stu-id="f5763-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5763-118">コメント</span><span class="sxs-lookup"><span data-stu-id="f5763-118">Remarks</span></span>  
 <span data-ttu-id="f5763-119">ホスト呼び出し`LockClrVersion`CLR を初期化する前にします。</span><span class="sxs-lookup"><span data-stu-id="f5763-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="f5763-120">`LockClrVersion` 型のコールバックをすべての 3 つのパラメーターを受け取る[FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5763-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="f5763-121">この種類の定義は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f5763-121">This type is defined as follows.</span></span>  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="f5763-122">次の手順は、ランタイムの初期化時に発生します。</span><span class="sxs-lookup"><span data-stu-id="f5763-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1.  <span data-ttu-id="f5763-123">ホスト呼び出し[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)または他のランタイム初期化関数のいずれか。</span><span class="sxs-lookup"><span data-stu-id="f5763-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="f5763-124">または、ホストは、COM オブジェクトのアクティブ化を使用してランタイムを初期化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f5763-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2.  <span data-ttu-id="f5763-125">ランタイムがで指定された関数を呼び出す、`hostCallback`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="f5763-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3.  <span data-ttu-id="f5763-126">指定された関数`hostCallback`次の一連の呼び出しを使用します。</span><span class="sxs-lookup"><span data-stu-id="f5763-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    -   <span data-ttu-id="f5763-127">指定された関数、`pBeginHostSetup`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="f5763-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    -   <span data-ttu-id="f5763-128">`CorBindToRuntimeEx` (または別のランタイム初期化関数)。</span><span class="sxs-lookup"><span data-stu-id="f5763-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    -   <span data-ttu-id="f5763-129">[Iclrruntimehost::sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5763-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    -   <span data-ttu-id="f5763-130">[Iclrruntimehost::start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5763-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    -   <span data-ttu-id="f5763-131">指定された関数、`pEndHostSetup`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="f5763-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="f5763-132">すべての呼び出し`pBeginHostSetup`に`pEndHostSetup`1 つのスレッドまたはファイバーは、同じ論理スタックに対して実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5763-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="f5763-133">このスレッドは、基になるスレッドと異なる場合が`hostCallback`と呼びます。</span><span class="sxs-lookup"><span data-stu-id="f5763-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5763-134">要件</span><span class="sxs-lookup"><span data-stu-id="f5763-134">Requirements</span></span>  
 <span data-ttu-id="f5763-135">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5763-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5763-136">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5763-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5763-137">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5763-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5763-138">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5763-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5763-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5763-139">See Also</span></span>  
 <span data-ttu-id="f5763-140">
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span><span class="sxs-lookup"><span data-stu-id="f5763-140">[Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span></span>
