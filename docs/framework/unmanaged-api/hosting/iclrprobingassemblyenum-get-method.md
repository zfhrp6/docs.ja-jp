---
title: ICLRProbingAssemblyEnum::Get メソッド
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f5ddd352d027365e02366e9aa779053da3bdc2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434805"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="dfca7-102">ICLRProbingAssemblyEnum::Get メソッド</span><span class="sxs-lookup"><span data-stu-id="dfca7-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="dfca7-103">指定したインデックス位置には、アセンブリの id を取得します。</span><span class="sxs-lookup"><span data-stu-id="dfca7-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfca7-104">構文</span><span class="sxs-lookup"><span data-stu-id="dfca7-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfca7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dfca7-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="dfca7-106">[in]アセンブリ id を返すの 0 から始まるインデックス。</span><span class="sxs-lookup"><span data-stu-id="dfca7-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="dfca7-107">[out]アセンブリの id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="dfca7-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="dfca7-108">[入力、出力].サイズ、`pwzBuffer`バッファー。</span><span class="sxs-lookup"><span data-stu-id="dfca7-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfca7-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="dfca7-109">Return Value</span></span>  
  
|<span data-ttu-id="dfca7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfca7-110">HRESULT</span></span>|<span data-ttu-id="dfca7-111">説明</span><span class="sxs-lookup"><span data-stu-id="dfca7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfca7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfca7-112">S_OK</span></span>|<span data-ttu-id="dfca7-113">`Get` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="dfca7-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="dfca7-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="dfca7-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="dfca7-115">`pwzBuffer` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="dfca7-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="dfca7-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="dfca7-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="dfca7-117">列挙には、これ以上項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dfca7-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="dfca7-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dfca7-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dfca7-119">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="dfca7-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dfca7-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dfca7-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dfca7-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="dfca7-121">The call timed out.</span></span>|  
|<span data-ttu-id="dfca7-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dfca7-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dfca7-123">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="dfca7-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dfca7-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dfca7-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dfca7-125">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="dfca7-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dfca7-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dfca7-126">E_FAIL</span></span>|<span data-ttu-id="dfca7-127">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="dfca7-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dfca7-128">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="dfca7-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dfca7-129">ホスティング メソッドが存在する後続の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="dfca7-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfca7-130">コメント</span><span class="sxs-lookup"><span data-stu-id="dfca7-130">Remarks</span></span>  
 <span data-ttu-id="dfca7-131">インデックス 0 の id は、プロセッサ アーキテクチャに固有の id です。</span><span class="sxs-lookup"><span data-stu-id="dfca7-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="dfca7-132">インデックス 1 の id は、Microsoft intermediate language (MSIL) のアーキテクチャに依存しないアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="dfca7-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="dfca7-133">インデックス 2 の id には、アーキテクチャの情報が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="dfca7-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="dfca7-134">`Get` 通常 2 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="dfca7-134">`Get` is typically called twice.</span></span> <span data-ttu-id="dfca7-135">最初の呼び出しに対して null 値を提供する`pwzBuffer`、設定と`pcchBufferSize`の適切なサイズに`pwzBuffer`です。</span><span class="sxs-lookup"><span data-stu-id="dfca7-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="dfca7-136">2 番目の呼び出しを適切なサイズ指定`pwzBuffer`、完了したときに標準アセンブリの id データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dfca7-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfca7-137">要件</span><span class="sxs-lookup"><span data-stu-id="dfca7-137">Requirements</span></span>  
 <span data-ttu-id="dfca7-138">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dfca7-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfca7-139">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dfca7-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfca7-140">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="dfca7-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfca7-141">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfca7-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfca7-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfca7-142">See Also</span></span>  
 [<span data-ttu-id="dfca7-143">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dfca7-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="dfca7-144">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dfca7-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
