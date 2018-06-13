---
title: ICLRRuntimeHost::GetCurrentAppDomainId メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbe6ac3c9f03de2224f933a7e44325f578ded48b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433912"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="30c62-102">ICLRRuntimeHost::GetCurrentAppDomainId メソッド</span><span class="sxs-lookup"><span data-stu-id="30c62-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="30c62-103">数値識別子を取得、<xref:System.AppDomain>が現在実行されています。</span><span class="sxs-lookup"><span data-stu-id="30c62-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c62-104">構文</span><span class="sxs-lookup"><span data-stu-id="30c62-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30c62-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30c62-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="30c62-106">[out]数値識別子、<xref:System.AppDomain>が現在実行されています。</span><span class="sxs-lookup"><span data-stu-id="30c62-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30c62-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="30c62-107">Return Value</span></span>  
  
|<span data-ttu-id="30c62-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30c62-108">HRESULT</span></span>|<span data-ttu-id="30c62-109">説明</span><span class="sxs-lookup"><span data-stu-id="30c62-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30c62-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="30c62-110">S_OK</span></span>|<span data-ttu-id="30c62-111">`GetCurrentAppDomainId` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="30c62-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="30c62-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30c62-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30c62-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="30c62-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30c62-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30c62-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30c62-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="30c62-115">The call timed out.</span></span>|  
|<span data-ttu-id="30c62-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30c62-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30c62-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="30c62-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30c62-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30c62-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30c62-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="30c62-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30c62-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30c62-120">E_FAIL</span></span>|<span data-ttu-id="30c62-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="30c62-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30c62-122">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="30c62-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30c62-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="30c62-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30c62-124">コメント</span><span class="sxs-lookup"><span data-stu-id="30c62-124">Remarks</span></span>  
 <span data-ttu-id="30c62-125">`pdwAppDomainId`パラメーターがの値に設定されている、<xref:System.AppDomain.Id%2A>のプロパティ、<xref:System.AppDomain>現在のスレッドが実行中にします。</span><span class="sxs-lookup"><span data-stu-id="30c62-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30c62-126">要件</span><span class="sxs-lookup"><span data-stu-id="30c62-126">Requirements</span></span>  
 <span data-ttu-id="30c62-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="30c62-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30c62-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="30c62-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30c62-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="30c62-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30c62-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30c62-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c62-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="30c62-131">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="30c62-132">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30c62-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
