---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a3d5bb8a8cc5acc88373fa4952848d08ccd485
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434917"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="9b5bb-102">ICLRPolicyManager::SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="9b5bb-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="9b5bb-103">ハンドルされない例外が発生したときに、共通言語ランタイム (CLR) の動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b5bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b5bb-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b5bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b5bb-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="9b5bb-106">[in]1 つ、 [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) CLR または、ホストによって動作が設定されているかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b5bb-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="9b5bb-107">Return Value</span></span>  
  
|<span data-ttu-id="9b5bb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b5bb-108">HRESULT</span></span>|<span data-ttu-id="9b5bb-109">説明</span><span class="sxs-lookup"><span data-stu-id="9b5bb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b5bb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b5bb-110">S_OK</span></span>|<span data-ttu-id="9b5bb-111">`SetUnhandledExceptionPolicy` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="9b5bb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9b5bb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9b5bb-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9b5bb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9b5bb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9b5bb-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-115">The call timed out.</span></span>|  
|<span data-ttu-id="9b5bb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9b5bb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9b5bb-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9b5bb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9b5bb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9b5bb-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9b5bb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9b5bb-120">E_FAIL</span></span>|<span data-ttu-id="9b5bb-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9b5bb-122">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9b5bb-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b5bb-124">コメント</span><span class="sxs-lookup"><span data-stu-id="9b5bb-124">Remarks</span></span>  
 <span data-ttu-id="9b5bb-125">既定では、CLR は、すべてのハンドルされない例外では、最後のハンドラーであり、その既定の動作は、プロセスをダウン破棄します。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="9b5bb-126">ホストは設定してこの動作を変更することができます、 `policy` eHostDeterminedPolicy する値。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="9b5bb-127">CLR の以前のバージョンと同じように、この値により、ホストが独自の既定の動作を実装します。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b5bb-128">要件</span><span class="sxs-lookup"><span data-stu-id="9b5bb-128">Requirements</span></span>  
 <span data-ttu-id="9b5bb-129">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b5bb-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b5bb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b5bb-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9b5bb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b5bb-132">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b5bb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5bb-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b5bb-133">See Also</span></span>  
 [<span data-ttu-id="9b5bb-134">EClrUnhandledException 列挙型</span><span class="sxs-lookup"><span data-stu-id="9b5bb-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 [<span data-ttu-id="9b5bb-135">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b5bb-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="9b5bb-136">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b5bb-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="9b5bb-137">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b5bb-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
