---
title: IHostSecurityManager::OpenThreadToken メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35a41badd7ade016619d940880a3ace80ccf5693
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="99084-102">IHostSecurityManager::OpenThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="99084-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="99084-103">現在実行中のスレッドに関連付けられている随意アクセス トークンを開きます。</span><span class="sxs-lookup"><span data-stu-id="99084-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99084-104">構文</span><span class="sxs-lookup"><span data-stu-id="99084-104">Syntax</span></span>  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99084-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="99084-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="99084-106">[in]スレッド トークンへのアクセスの要求の種類を指定するアクセスの値のマスク。</span><span class="sxs-lookup"><span data-stu-id="99084-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="99084-107">これらの値が、Win32 で定義されている`OpenThreadToken`関数。</span><span class="sxs-lookup"><span data-stu-id="99084-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="99084-108">要求されたアクセス タイプは、トークンの随意アクセス制御リスト (DACL) を許可または拒否するアクセスの種類を決定に対して調整します。</span><span class="sxs-lookup"><span data-stu-id="99084-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="99084-109">[in]`true` ; 呼び出し元のスレッド、プロセスのセキュリティ コンテキストを使用して、アクセス チェックが行われることを指定するには`false`自体、呼び出し元スレッドのセキュリティ コンテキストを使用して、アクセス チェックを実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="99084-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="99084-110">スレッドでは、クライアントを偽装する場合、クライアント プロセスのことをセキュリティ コンテキストにできます。</span><span class="sxs-lookup"><span data-stu-id="99084-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="99084-111">[out]新しく開かれたアクセス トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99084-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99084-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="99084-112">Return Value</span></span>  
  
|<span data-ttu-id="99084-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99084-113">HRESULT</span></span>|<span data-ttu-id="99084-114">説明</span><span class="sxs-lookup"><span data-stu-id="99084-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99084-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="99084-115">S_OK</span></span>|<span data-ttu-id="99084-116">`OpenThreadToken` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="99084-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="99084-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99084-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99084-118">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="99084-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99084-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99084-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99084-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="99084-120">The call timed out.</span></span>|  
|<span data-ttu-id="99084-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99084-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99084-122">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="99084-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99084-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99084-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99084-124">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="99084-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99084-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99084-125">E_FAIL</span></span>|<span data-ttu-id="99084-126">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="99084-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99084-127">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="99084-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99084-128">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="99084-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99084-129">コメント</span><span class="sxs-lookup"><span data-stu-id="99084-129">Remarks</span></span>  
 <span data-ttu-id="99084-130">`IHostSecurityManager::OpenThreadToken` 動作は同様に、同じ名前の対応する Win32 関数に Win32 関数には、任意のスレッドに、ハンドルに渡す、呼び出し元がで使用できる、する点を除いて while`IHostSecurityManager::OpenThreadToken`呼び出し元のスレッドに関連付けられたトークンのみを開きます。</span><span class="sxs-lookup"><span data-stu-id="99084-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="99084-131">`HANDLE`型が COM に準拠していない、つまり、そのサイズは、オペレーティング システムに固有、カスタム マーシャ リングが必要です。</span><span class="sxs-lookup"><span data-stu-id="99084-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="99084-132">したがって、このトークンは、CLR とホスト間のプロセス内でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="99084-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99084-133">要件</span><span class="sxs-lookup"><span data-stu-id="99084-133">Requirements</span></span>  
 <span data-ttu-id="99084-134">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="99084-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99084-135">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99084-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99084-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="99084-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99084-137">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99084-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99084-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="99084-138">See Also</span></span>  
 [<span data-ttu-id="99084-139">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99084-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="99084-140">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99084-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
