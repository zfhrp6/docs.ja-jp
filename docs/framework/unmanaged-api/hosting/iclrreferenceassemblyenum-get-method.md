---
title: "ICLRReferenceAssemblyEnum::Get メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRReferenceAssemblyEnum.Get
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ab64f7983b5825505421e7bfbcf6866004778a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="22a4b-102">ICLRReferenceAssemblyEnum::Get メソッド</span><span class="sxs-lookup"><span data-stu-id="22a4b-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="22a4b-103">指定したインデックス位置には、アセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="22a4b-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a4b-104">構文</span><span class="sxs-lookup"><span data-stu-id="22a4b-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22a4b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="22a4b-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="22a4b-106">[in]アセンブリ id を返すの 0 から始まるインデックス。</span><span class="sxs-lookup"><span data-stu-id="22a4b-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="22a4b-107">[out]アセンブリの id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="22a4b-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="22a4b-108">[入力、出力].サイズ、`pwzBuffer`バッファー。</span><span class="sxs-lookup"><span data-stu-id="22a4b-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22a4b-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="22a4b-109">Return Value</span></span>  
  
|<span data-ttu-id="22a4b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22a4b-110">HRESULT</span></span>|<span data-ttu-id="22a4b-111">説明</span><span class="sxs-lookup"><span data-stu-id="22a4b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22a4b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="22a4b-112">S_OK</span></span>|<span data-ttu-id="22a4b-113">`Get`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="22a4b-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="22a4b-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="22a4b-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="22a4b-115">`pwzBuffer` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="22a4b-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="22a4b-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="22a4b-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="22a4b-117">列挙には、これ以上項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="22a4b-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="22a4b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22a4b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22a4b-119">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="22a4b-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="22a4b-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22a4b-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22a4b-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="22a4b-121">The call timed out.</span></span>|  
|<span data-ttu-id="22a4b-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22a4b-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22a4b-123">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="22a4b-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22a4b-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22a4b-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22a4b-125">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="22a4b-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22a4b-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22a4b-126">E_FAIL</span></span>|<span data-ttu-id="22a4b-127">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="22a4b-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22a4b-128">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="22a4b-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22a4b-129">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="22a4b-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22a4b-130">コメント</span><span class="sxs-lookup"><span data-stu-id="22a4b-130">Remarks</span></span>  
 <span data-ttu-id="22a4b-131">`Get`通常 2 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="22a4b-131">`Get` is typically called twice.</span></span> <span data-ttu-id="22a4b-132">最初の呼び出しに対して null 値を提供する`pwzBuffer`、設定と`pcchBufferSize`の適切なサイズに`pwzBuffer`です。</span><span class="sxs-lookup"><span data-stu-id="22a4b-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="22a4b-133">2 番目の呼び出しを適切なサイズ指定`pwzBuffer`、完了したときに標準アセンブリの id データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="22a4b-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22a4b-134">要件</span><span class="sxs-lookup"><span data-stu-id="22a4b-134">Requirements</span></span>  
 <span data-ttu-id="22a4b-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="22a4b-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22a4b-136">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="22a4b-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22a4b-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="22a4b-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22a4b-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22a4b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a4b-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="22a4b-139">See Also</span></span>  
 [<span data-ttu-id="22a4b-140">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22a4b-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="22a4b-141">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22a4b-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
