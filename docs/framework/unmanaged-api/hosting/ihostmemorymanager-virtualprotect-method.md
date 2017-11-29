---
title: "IHostMemoryManager::VirtualProtect メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualProtect
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8f8d363054ab4728ae031ccea44eb8eb853354ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="f0303-102">IHostMemoryManager::VirtualProtect メソッド</span><span class="sxs-lookup"><span data-stu-id="f0303-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="f0303-103">対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="f0303-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="f0303-104">Win32 実装`VirtualProtect`呼び出しプロセスの仮想アドレス空間でコミットされたページの領域に保護を変更します。</span><span class="sxs-lookup"><span data-stu-id="f0303-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0303-105">構文</span><span class="sxs-lookup"><span data-stu-id="f0303-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0303-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0303-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="f0303-107">[in]変更する保護属性は、仮想メモリのベース アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f0303-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="f0303-108">[in](バイト単位) を変更するメモリ ページの領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f0303-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="f0303-109">[in]適用するメモリの保護の種類。</span><span class="sxs-lookup"><span data-stu-id="f0303-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="f0303-110">[out]前のメモリ保護値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f0303-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0303-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="f0303-111">Return Value</span></span>  
  
|<span data-ttu-id="f0303-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0303-112">HRESULT</span></span>|<span data-ttu-id="f0303-113">説明</span><span class="sxs-lookup"><span data-stu-id="f0303-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0303-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0303-114">S_OK</span></span>|<span data-ttu-id="f0303-115">`VirtualProtect`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="f0303-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="f0303-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0303-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0303-117">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="f0303-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0303-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0303-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0303-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f0303-119">The call timed out.</span></span>|  
|<span data-ttu-id="f0303-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0303-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0303-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f0303-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0303-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0303-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0303-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="f0303-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0303-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0303-124">E_FAIL</span></span>|<span data-ttu-id="f0303-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f0303-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0303-126">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="f0303-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0303-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="f0303-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0303-128">コメント</span><span class="sxs-lookup"><span data-stu-id="f0303-128">Remarks</span></span>  
 <span data-ttu-id="f0303-129">この実装の`VirtualProtect`Win32 実装が成功を示すゼロ以外の値を返すとき、HRESULT 値とエラーを示す 0 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0303-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="f0303-130">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0303-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0303-131">要件</span><span class="sxs-lookup"><span data-stu-id="f0303-131">Requirements</span></span>  
 <span data-ttu-id="f0303-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f0303-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0303-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0303-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0303-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0303-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0303-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0303-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0303-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0303-136">See Also</span></span>  
 [<span data-ttu-id="f0303-137">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f0303-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
