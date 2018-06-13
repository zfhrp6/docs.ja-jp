---
title: IHostMemoryManager::VirtualProtect メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bada01e910397adcf0fe59286d90774a0ab24ffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439877"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="a7c60-102">IHostMemoryManager::VirtualProtect メソッド</span><span class="sxs-lookup"><span data-stu-id="a7c60-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="a7c60-103">対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="a7c60-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="a7c60-104">Win32 実装`VirtualProtect`呼び出しプロセスの仮想アドレス空間でコミットされたページの領域に保護を変更します。</span><span class="sxs-lookup"><span data-stu-id="a7c60-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c60-105">構文</span><span class="sxs-lookup"><span data-stu-id="a7c60-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7c60-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a7c60-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="a7c60-107">[in]変更する保護属性は、仮想メモリのベース アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7c60-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="a7c60-108">[in] 変更されるメモリページの領域のサイズ（バイト単位）。</span><span class="sxs-lookup"><span data-stu-id="a7c60-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="a7c60-109">[in]適用するメモリの保護の種類。</span><span class="sxs-lookup"><span data-stu-id="a7c60-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="a7c60-110">[out]前のメモリ保護値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7c60-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7c60-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="a7c60-111">Return Value</span></span>  
  
|<span data-ttu-id="a7c60-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7c60-112">HRESULT</span></span>|<span data-ttu-id="a7c60-113">説明</span><span class="sxs-lookup"><span data-stu-id="a7c60-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7c60-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7c60-114">S_OK</span></span>|<span data-ttu-id="a7c60-115">`VirtualProtect` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a7c60-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="a7c60-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7c60-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7c60-117">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="a7c60-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7c60-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7c60-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7c60-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a7c60-119">The call timed out.</span></span>|  
|<span data-ttu-id="a7c60-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7c60-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7c60-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a7c60-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7c60-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7c60-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7c60-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="a7c60-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7c60-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7c60-124">E_FAIL</span></span>|<span data-ttu-id="a7c60-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a7c60-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7c60-126">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a7c60-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7c60-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="a7c60-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7c60-128">コメント</span><span class="sxs-lookup"><span data-stu-id="a7c60-128">Remarks</span></span>  
 <span data-ttu-id="a7c60-129">この実装の`VirtualProtect`Win32 実装が成功を示すゼロ以外の値を返すとき、HRESULT 値とエラーを示す 0 値を返します。</span><span class="sxs-lookup"><span data-stu-id="a7c60-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="a7c60-130">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7c60-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7c60-131">要件</span><span class="sxs-lookup"><span data-stu-id="a7c60-131">Requirements</span></span>  
 <span data-ttu-id="a7c60-132">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7c60-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7c60-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7c60-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7c60-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a7c60-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7c60-135">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7c60-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c60-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7c60-136">See Also</span></span>  
 [<span data-ttu-id="a7c60-137">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a7c60-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
